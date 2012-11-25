# Operational Exercises with the Command-line Interface#

The following exercises use the command line interface to perform typical operations on a VoltDB database.  Unless specified otherwise, these commands will work on Community Edition or Enterprise Edition.


## A. Starting and Stopping a cluster ##

Set the following environment variables that will be used in subsequent commands.

Start the database (the voter demo) manually:

    VOLTDB_HOME=`cd ~/voltdb-* && pwd`
    PATH=$PATH:$VOLTDB_HOME\bin
    voltdb start catalog voter.jar deployment deployment.xml \
        license $VOLTDB_HOME/voltdb/license.xml host localhost

Add some data:

    cd ~/voltdb-*
    cd bin
    sqlcmd
    1> INSERT INTO contestants (contestant_number,contestant_name) VALUES (100,'Homer Simpson');
    (1 row(s) affected)
    2> exit
    

Stop the database

    cd ~/voltdb-*
    cd bin
    sqlcmd
    1> exec @Shutdown

## B. Manual snapshot ##

Start the database (the voter demo) manually:

    VOLTDB_HOME=`cd ~/voltdb-* && pwd`
    PATH=$PATH:$VOLTDB_HOME\bin
    voltdb start catalog voter.jar deployment deployment.xml \
        license $VOLTDB_HOME/voltdb/license.xml host localhost

Add some data:

    cd ~/voltdb-*
    cd bin
    sqlcmd
    1> INSERT INTO contestants (contestant_number,contestant_name) VALUES (100,'Homer Simpson');
    (1 row(s) affected)
    2> exit



## C. Recovery ##



## D. Live Catalog Update ##

CLI: Read [Performing a live catalog update using the command line](http://community.voltdb.com/node/1436)


## E. High Availability ## 
### Configuration ###
High Availability in VoltDB (also called K-safety) is achieved by having every record of data stored and every transaction processed in two or more places.  This allows the database cluster to continue functioning with no loss of data if one or more servers fail.  Another advantage to this approach is that since the work is done in parallel, the throughput of the database is not affected when a server fails.

Read [*Using VoltDB* - Chapter 11. Availability](http://community.voltdb.com/docs/UsingVoltDB/ChapKSafety) for a detailed description of how this feature works in VoltDB and how to configure it.

High availability is a configurable option that set before starting VoltDB.  If you're starting the database from the command line interface or with scripts, you set this option by editing the deployment.xml file.  For example, the following deployment.xml file has enabled k-safety by setting the kfactor setting to 2.  This allows for any 2 servers in the cluster to fail without loss of availability.


    <?xml version="1.0"?>
    <deployment>
        <cluster hostcount="6" sitesperhost="4" kfactor="2"/>
    </deployment>


If you are using VoltDB Enterprise Manager, it's one of the [Database Configuration options](http://community.voltdb.com/docs/MgtGuide/HostConfigDBOpts).

### Node Failure and Rejoin ###

## F. Database Replication ##


## Stopping the database for Maintenance ##
If you're starting the database from the command line interface, read [Performing a Maintenance Window using the command-line](http://community.voltdb.com/node/1426).

If you're using VoltDB Enterprise Manager, read [*Management Guide* 5.2. Stopping the Database](http://community.voltdb.com/docs/MgtGuide/StopStopCluster).
VEM
CLI

# Upgrading VoltDB #
See [Upgrade Notes](http://community.voltdb.com/docs/EnterpriseReleaseNotes/index#UpgradeNotes) from Enterprise Release Notes.

# Security #
Read [*Using VoltDB* Chapter 8](http://community.voltdb.com/docs/UsingVoltDB/ChapSecurity)


# Support Overview #