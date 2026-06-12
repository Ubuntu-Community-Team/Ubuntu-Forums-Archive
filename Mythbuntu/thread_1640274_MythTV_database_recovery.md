---
title: "MythTV database recovery"
date: 2010-12-07
forum: Mythbuntu
---

### Post by Erden on 2010-12-07
Hello,

My system has crashed. I copied the backup of database. I also have all the recordings.

I install a fresh copy of Ubuntu 10.04 and MythTV 0.23.

I tried to recover the database with mythconverg_restore.pl

Now it says in a graphic screen:

```
This version of MythTV requires an updated database. (Schema is 1254 versions behind)

Please run MythTV-setup or mythbackend to update your database.

Database Host: Localhost
Database Name: mythconverg
```

Is there any way to recover my database?

---

### Post by nickrout on 2010-12-07
follow the instructions - > Please run MythTV-setup or mythbackend to update your database

---

### Post by Erden on 2010-12-07
I follow the instructions. But nothing happens. I get the same error.

---

### Post by nickrout on 2010-12-07
Is this a combined backend/frontend machine or a standalone frontend or a standalone backend?

Is this message given in the frontedn when you start it up?

what is the output of:

```
dpkg -l mythtv-backend
dpkg -l mythtv-frontend
```

---

### Post by Erden on 2010-12-08
Thanks for your message. 

This is a combined backend/frontend machine.

When I run the frontend, setup or backend. I get the same message on a graphic screen. 

Here is the output of 
```
dpkg -l mythtv-backend
dpkg -l mythtv-frontend
``````
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  mythtv-backend           0.23.0+fixes24158-0ubunt A personal video recorder application (server)

``````
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  mythtv-frontend          0.23.0+fixes24158-0ubunt A personal video recorder application (client)

```

---

### Post by andree_b on 2010-12-08
It rather seems the backed up DB is from an older version.

Which MythTV version did you run before the crash? 

You might have to install an older version to restore the DB and then update to current version which will then upgrade the DB as well.

---

### Post by Erden on 2010-12-08
Thanks for your message.

> **andree_b said:**
> It rather seems the backed up DB is from an older version.

Which MythTV version did you run before the crash?

I think it was an old version, I installed several months ago. But I am not sure which version it is. Is there any way to tell from the recovered harddrive data? I recovered almost all the folders.

> **andree_b said:**
> You might have to install an older version to restore the DB and then update to current version which will then upgrade the DB as well.

I tried to install 0.22 manually. However I could not made it. I don't know how to compile etc. Is there an easy way to install older versions?

Thanks a lot.

---

### Post by nickrout on 2010-12-08
What does the backend log say when you start it?

---

### Post by Erden on 2010-12-08
> **nickrout said:**
> What does the backend log say when you start it?

Here is the log file:

```
2010-12-08 15:34:04.356 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-12-08 15:34:04.939 Using runtime prefix = /usr
2010-12-08 15:34:04.974 Using configuration directory = /home/mythtv/.mythtv
2010-12-08 15:34:05.061 Empty LocalHostName.
2010-12-08 15:34:05.106 Using localhost value of erden-desktop
2010-12-08 15:34:05.449 New DB connection, total: 1
2010-12-08 15:34:05.572 Connected to database 'mythconverg' at host: localhost
2010-12-08 15:34:05.608 Closing DB connection named 'DBManager0'
2010-12-08 15:34:05.617 Connected to database 'mythconverg' at host: localhost
2010-12-08 15:34:05.676 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-08 15:34:05.707 MythBackend: Starting up as the master server.
2010-12-08 15:34:05.758 New DB connection, total: 2
2010-12-08 15:34:05.788 Connected to database 'mythconverg' at host: localhost
2010-12-08 15:34:05.793 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2010-12-08 15:34:05.810 New DB connection, total: 3
2010-12-08 15:34:05.823 Connected to database 'mythconverg' at host: localhost
2010-12-08 15:34:05.937 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-12-08 15:34:05.949 Main::Registering HttpStatus Extension
2010-12-08 15:34:05.957 Enabled verbose msgs:  important general
2010-12-08 15:34:05.974 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-12-08 15:35:25.841 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-12-08 15:40:14.511 MainServer::ANN Monitor
2010-12-08 15:40:14.537 adding: erden-desktop as a client (events: 0)
2010-12-08 15:40:14.549 MainServer::ANN Monitor
2010-12-08 15:40:14.553 adding: erden-desktop as a client (events: 1)
2010-12-08 15:42:15.843 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:42:15.852 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:42:15.861 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:42:25.929 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:42:25.957 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:42:25.968 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:42:25.974 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:43:15.870 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:43:15.917 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:43:15.931 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:43:25.987 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:43:26.010 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:44:15.940 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:44:15.951 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:44:15.960 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:44:22.835 Error preparing query: SELECT lastrun FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:44:22.860 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:22.936 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
2010-12-08 15:44:23.044 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:23.144 DB Error (HouseKeeper::wantToRun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
Bindings were:
:TAG=DailyCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:44:23.254 Error preparing query: DELETE FROM jobqueue WHERE (status in (:FINISHED, :ABORTED, :CANCELLED) AND statustime < :DONEPURGEDATE) OR (status in (:ERRORED) AND statustime < :ERRORSPURGEDATE) 
2010-12-08 15:44:23.361 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:44:23.478 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (:FINISHED, :ABORTED, :CANCELLED) AND statustime < :DONEPURGEDATE) OR (status in (:ERRORED) AND statustime < :ERRORSPURGEDATE) 
Bindings were:
:ABORTED=288, :CANCELLED=320, :DONEPURGEDATE=2010-12-06T15:44:23, :ERRORED=304,
:ERRORSPURGEDATE=2010-12-04T15:44:23, :FINISHED=272
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':FINISHED, :ABORTED, :CANCELLED) AND statustime < :DONEPURGEDATE) OR (status in ' at line 1

2010-12-08 15:44:23.599 Error preparing query: DELETE FROM inuseprograms WHERE lastupdatetime < :FOURHOURSAGO ;
2010-12-08 15:44:23.611 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:44:23.620 DB Error (HouseKeeper::CleanupAllOldInUsePrograms):
Query was:
DELETE FROM inuseprograms WHERE lastupdatetime < :FOURHOURSAGO ;
Bindings were:
:FOURHOURSAGO=2010-12-08T11:44:23
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':FOURHOURSAGO' at line 1

2010-12-08 15:44:23.629 Error preparing query: SELECT DISTINCT chainid FROM tvchain WHERE endtime > :FOURHOURSAGO ;
2010-12-08 15:44:23.636 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.tvchain' doesn't exist

2010-12-08 15:44:23.645 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > :FOURHOURSAGO ;
Bindings were:
:FOURHOURSAGO=2010-12-08T11:44:23
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':FOURHOURSAGO' at line 1

2010-12-08 15:44:23.658 Error preparing query: INSERT INTO temprecordedcleanup ( chanid, starttime ) SELECT DISTINCT chanid, starttime FROM recordedprogram;
2010-12-08 15:44:23.661 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recordedprogram' doesn't exist

2010-12-08 15:44:23.670 DB Error (HouseKeeper Cleaning Recorded Tables):
Query was:
INSERT INTO temprecordedcleanup ( chanid, starttime ) SELECT DISTINCT chanid, starttime FROM recordedprogram;
No error type from QSqlError?  Strange...
2010-12-08 15:44:23.679 Error preparing query: DELETE FROM oldprogram WHERE airdate < DATE_SUB(CURRENT_DATE, INTERVAL 320 DAY);
2010-12-08 15:44:23.686 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:44:23.695 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM oldprogram WHERE airdate < DATE_SUB(CURRENT_DATE, INTERVAL 320 DAY);
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:44:23.704 Error preparing query: REPLACE INTO oldprogram (oldtitle,airdate) SELECT title,starttime FROM program WHERE starttime < NOW() AND manualid = 0 GROUP BY title;
2010-12-08 15:44:23.711 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:44:23.720 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
REPLACE INTO oldprogram (oldtitle,airdate) SELECT title,starttime FROM program WHERE starttime < NOW() AND manualid = 0 GROUP BY title;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:44:23.729 Error preparing query: DELETE FROM program WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:44:23.736 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.program' doesn't exist

2010-12-08 15:44:23.745 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM program WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:44:23.755 Error preparing query: DELETE FROM programrating WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:44:23.761 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.programrating' doesn't exist

2010-12-08 15:44:23.800 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM programrating WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:44:23.821 Error preparing query: DELETE FROM programgenres WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:44:23.928 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.programgenres' doesn't exist

2010-12-08 15:44:24.012 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM programgenres WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:44:24.071 Error preparing query: DELETE FROM credits WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:44:24.112 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.credits' doesn't exist

2010-12-08 15:44:24.154 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM credits WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:44:24.213 Error preparing query: DELETE FROM record WHERE (type = :SINGLE OR type = :OVERRIDE OR type = :DONTRECORD) AND enddate < CURDATE();
2010-12-08 15:44:24.271 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.record' doesn't exist

2010-12-08 15:44:24.304 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM record WHERE (type = :SINGLE OR type = :OVERRIDE OR type = :DONTRECORD) AND enddate < CURDATE();
Bindings were:
:DONTRECORD=8, :OVERRIDE=7, :SINGLE=1
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':SINGLE OR type = :OVERRIDE OR type = :DONTRECORD) AND enddate < CURDATE()' at line 1

2010-12-08 15:44:24.371 Error preparing query: SELECT record.recordid FROM record LEFT JOIN oldfind ON oldfind.recordid = record.recordid WHERE type = :FINDONE AND oldfind.findid IS NOT NULL;
2010-12-08 15:44:24.454 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.record' doesn't exist

2010-12-08 15:44:24.564 Error preparing query: DELETE FROM oldfind WHERE findid < TO_DAYS(NOW()) - 14;
2010-12-08 15:44:24.613 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldfind' doesn't exist

2010-12-08 15:44:24.622 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM oldfind WHERE findid < TO_DAYS(NOW()) - 14;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.oldfind' doesn't exist

2010-12-08 15:44:24.630 Error preparing query: SELECT data FROM settings WHERE value = :KEY AND hostname = :HOSTNAME
2010-12-08 15:44:24.638 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.settings' doesn't exist

2010-12-08 15:44:24.647 Error preparing query: SELECT data FROM settings WHERE value = :KEY AND hostname IS NULL
2010-12-08 15:44:24.703 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.settings' doesn't exist

2010-12-08 15:44:24.797 Error preparing query: DELETE FROM oldrecorded WHERE recstatus <> :RECORDED AND duplicate = 0 AND endtime < DATE_SUB(CURRENT_DATE, INTERVAL :CLEAN DAY);
2010-12-08 15:44:24.805 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldrecorded' doesn't exist

2010-12-08 15:44:24.914 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM oldrecorded WHERE recstatus <> :RECORDED AND duplicate = 0 AND endtime < DATE_SUB(CURRENT_DATE, INTERVAL :CLEAN DAY);
Bindings were:
:CLEAN=10, :RECORDED=-3
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':RECORDED AND duplicate = 0 AND endtime < DATE_SUB(CURRENT_DATE, INTERVAL :CLEAN' at line 1

2010-12-08 15:44:24.956 Error preparing query: DELETE FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:44:24.997 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.022 DB Error (HouseKeeper::updateLastrun -- delete):
Query was:
DELETE FROM housekeeping WHERE tag = :TAG ;
Bindings were:
:TAG=DailyCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG' at line 1

2010-12-08 15:44:25.030 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
2010-12-08 15:44:25.038 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.048 DB Error (HouseKeeper::updateLastrun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
Bindings were:
:TAG=DailyCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:44:25.056 Error preparing query: SELECT lastrun FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:44:25.063 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.073 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
2010-12-08 15:44:25.080 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.098 DB Error (HouseKeeper::wantToRun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
Bindings were:
:TAG=JobQueueRecover-erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:44:25.106 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:44:25.113 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:44:25.122 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:44:25.154 Error preparing query: DELETE FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:44:25.222 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.314 DB Error (HouseKeeper::updateLastrun -- delete):
Query was:
DELETE FROM housekeeping WHERE tag = :TAG ;
Bindings were:
:TAG=JobQueueRecover-erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG' at line 1

2010-12-08 15:44:25.324 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
2010-12-08 15:44:25.330 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.339 DB Error (HouseKeeper::updateLastrun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
Bindings were:
:TAG=JobQueueRecover-erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:44:25.423 Error preparing query: SELECT lastrun FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:44:25.472 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.481 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
2010-12-08 15:44:25.514 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:44:25.556 DB Error (HouseKeeper::wantToRun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
Bindings were:
:TAG=DBCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:44:26.022 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:44:26.040 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:44:26.049 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:44:26.096 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:45:15.969 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:45:15.987 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:45:15.996 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:45:26.135 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:45:26.194 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:46:16.034 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:46:16.052 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:46:16.061 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:46:26.225 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:46:26.240 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:46:26.250 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:46:26.256 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:47:16.070 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:47:16.077 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:47:16.086 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:47:26.268 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:47:26.289 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:48:16.095 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:48:16.112 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:48:16.121 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:48:26.328 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:48:26.349 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:48:26.361 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:48:26.366 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:49:16.130 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:49:16.143 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:49:16.152 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:49:26.377 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:49:26.389 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:49:26.574 Error preparing query: SELECT lastrun FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:49:26.581 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:26.590 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
2010-12-08 15:49:26.598 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:26.606 DB Error (HouseKeeper::wantToRun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
Bindings were:
:TAG=DailyCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:49:26.638 Error preparing query: DELETE FROM jobqueue WHERE (status in (:FINISHED, :ABORTED, :CANCELLED) AND statustime < :DONEPURGEDATE) OR (status in (:ERRORED) AND statustime < :ERRORSPURGEDATE) 
2010-12-08 15:49:26.652 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:49:26.661 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (:FINISHED, :ABORTED, :CANCELLED) AND statustime < :DONEPURGEDATE) OR (status in (:ERRORED) AND statustime < :ERRORSPURGEDATE) 
Bindings were:
:ABORTED=288, :CANCELLED=320, :DONEPURGEDATE=2010-12-06T15:49:26, :ERRORED=304,
:ERRORSPURGEDATE=2010-12-04T15:49:26, :FINISHED=272
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':FINISHED, :ABORTED, :CANCELLED) AND statustime < :DONEPURGEDATE) OR (status in ' at line 1

2010-12-08 15:49:26.670 Error preparing query: DELETE FROM inuseprograms WHERE lastupdatetime < :FOURHOURSAGO ;
2010-12-08 15:49:26.677 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:49:26.686 DB Error (HouseKeeper::CleanupAllOldInUsePrograms):
Query was:
DELETE FROM inuseprograms WHERE lastupdatetime < :FOURHOURSAGO ;
Bindings were:
:FOURHOURSAGO=2010-12-08T11:49:26
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':FOURHOURSAGO' at line 1

2010-12-08 15:49:26.695 Error preparing query: SELECT DISTINCT chainid FROM tvchain WHERE endtime > :FOURHOURSAGO ;
2010-12-08 15:49:26.702 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.tvchain' doesn't exist

2010-12-08 15:49:26.711 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > :FOURHOURSAGO ;
Bindings were:
:FOURHOURSAGO=2010-12-08T11:49:26
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':FOURHOURSAGO' at line 1

2010-12-08 15:49:26.722 Error preparing query: INSERT INTO temprecordedcleanup ( chanid, starttime ) SELECT DISTINCT chanid, starttime FROM recordedprogram;
2010-12-08 15:49:26.727 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recordedprogram' doesn't exist

2010-12-08 15:49:26.736 DB Error (HouseKeeper Cleaning Recorded Tables):
Query was:
INSERT INTO temprecordedcleanup ( chanid, starttime ) SELECT DISTINCT chanid, starttime FROM recordedprogram;
No error type from QSqlError?  Strange...
2010-12-08 15:49:26.745 Error preparing query: DELETE FROM oldprogram WHERE airdate < DATE_SUB(CURRENT_DATE, INTERVAL 320 DAY);
2010-12-08 15:49:26.752 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:49:26.761 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM oldprogram WHERE airdate < DATE_SUB(CURRENT_DATE, INTERVAL 320 DAY);
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:49:26.769 Error preparing query: REPLACE INTO oldprogram (oldtitle,airdate) SELECT title,starttime FROM program WHERE starttime < NOW() AND manualid = 0 GROUP BY title;
2010-12-08 15:49:26.777 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:49:26.813 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
REPLACE INTO oldprogram (oldtitle,airdate) SELECT title,starttime FROM program WHERE starttime < NOW() AND manualid = 0 GROUP BY title;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.oldprogram' doesn't exist

2010-12-08 15:49:26.828 Error preparing query: DELETE FROM program WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:49:26.836 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.program' doesn't exist

2010-12-08 15:49:26.844 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM program WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:49:26.853 Error preparing query: DELETE FROM programrating WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:49:26.861 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.programrating' doesn't exist

2010-12-08 15:49:26.870 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM programrating WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:49:26.878 Error preparing query: DELETE FROM programgenres WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:49:26.886 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.programgenres' doesn't exist

2010-12-08 15:49:26.897 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM programgenres WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:49:26.903 Error preparing query: DELETE FROM credits WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
2010-12-08 15:49:26.911 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.credits' doesn't exist

2010-12-08 15:49:26.920 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM credits WHERE starttime <= DATE_SUB(CURRENT_DATE, INTERVAL :OFFSET DAY);
Bindings were:
:OFFSET=7
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':OFFSET DAY)' at line 1

2010-12-08 15:49:26.929 Error preparing query: DELETE FROM record WHERE (type = :SINGLE OR type = :OVERRIDE OR type = :DONTRECORD) AND enddate < CURDATE();
2010-12-08 15:49:26.936 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.record' doesn't exist

2010-12-08 15:49:26.945 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM record WHERE (type = :SINGLE OR type = :OVERRIDE OR type = :DONTRECORD) AND enddate < CURDATE();
Bindings were:
:DONTRECORD=8, :OVERRIDE=7, :SINGLE=1
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':SINGLE OR type = :OVERRIDE OR type = :DONTRECORD) AND enddate < CURDATE()' at line 1

2010-12-08 15:49:26.972 Error preparing query: SELECT record.recordid FROM record LEFT JOIN oldfind ON oldfind.recordid = record.recordid WHERE type = :FINDONE AND oldfind.findid IS NOT NULL;
2010-12-08 15:49:26.986 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.record' doesn't exist

2010-12-08 15:49:26.995 Error preparing query: DELETE FROM oldfind WHERE findid < TO_DAYS(NOW()) - 14;
2010-12-08 15:49:27.003 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldfind' doesn't exist

2010-12-08 15:49:27.012 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM oldfind WHERE findid < TO_DAYS(NOW()) - 14;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.oldfind' doesn't exist

2010-12-08 15:49:27.020 Error preparing query: DELETE FROM oldrecorded WHERE recstatus <> :RECORDED AND duplicate = 0 AND endtime < DATE_SUB(CURRENT_DATE, INTERVAL :CLEAN DAY);
2010-12-08 15:49:27.028 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.oldrecorded' doesn't exist

2010-12-08 15:49:27.036 DB Error (HouseKeeper Cleaning Program Listings):
Query was:
DELETE FROM oldrecorded WHERE recstatus <> :RECORDED AND duplicate = 0 AND endtime < DATE_SUB(CURRENT_DATE, INTERVAL :CLEAN DAY);
Bindings were:
:CLEAN=10, :RECORDED=-3
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':RECORDED AND duplicate = 0 AND endtime < DATE_SUB(CURRENT_DATE, INTERVAL :CLEAN' at line 1

2010-12-08 15:49:27.045 Error preparing query: DELETE FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:49:27.053 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.061 DB Error (HouseKeeper::updateLastrun -- delete):
Query was:
DELETE FROM housekeeping WHERE tag = :TAG ;
Bindings were:
:TAG=DailyCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG' at line 1

2010-12-08 15:49:27.070 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
2010-12-08 15:49:27.078 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.087 DB Error (HouseKeeper::updateLastrun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
Bindings were:
:TAG=DailyCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:49:27.095 Error preparing query: SELECT lastrun FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:49:27.103 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.112 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
2010-12-08 15:49:27.119 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.128 DB Error (HouseKeeper::wantToRun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
Bindings were:
:TAG=JobQueueRecover-erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:49:27.156 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:49:27.170 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:49:27.179 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:49:27.187 Error preparing query: DELETE FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:49:27.195 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.203 DB Error (HouseKeeper::updateLastrun -- delete):
Query was:
DELETE FROM housekeeping WHERE tag = :TAG ;
Bindings were:
:TAG=JobQueueRecover-erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG' at line 1

2010-12-08 15:49:27.212 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
2010-12-08 15:49:27.220 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.228 DB Error (HouseKeeper::updateLastrun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now()) ;
Bindings were:
:TAG=JobQueueRecover-erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:49:27.237 Error preparing query: SELECT lastrun FROM housekeeping WHERE tag = :TAG ;
2010-12-08 15:49:27.245 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.254 Error preparing query: INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
2010-12-08 15:49:27.261 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.housekeeping' doesn't exist

2010-12-08 15:49:27.272 DB Error (HouseKeeper::wantToRun -- insert):
Query was:
INSERT INTO housekeeping(tag,lastrun) values(:TAG ,now());
Bindings were:
:TAG=DBCleanup
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':TAG ,now())' at line 1

2010-12-08 15:50:16.161 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:50:16.179 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:50:16.188 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:50:26.404 Error preparing query: SELECT MIN(id),dirname FROM storagegroup WHERE hostname = :HOSTNAME AND groupname NOT IN ( 'DB Backups', 'Videos', 'Trailers', 'Coverart', 'Fanart', 'Screenshots', 'Banners' ) GROUP BY dirname;
2010-12-08 15:50:26.416 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.storagegroup' doesn't exist

2010-12-08 15:50:26.425 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-12-08 15:50:26.434 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:50:26.441 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:50:26.451 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:50:26.458 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:50:26.468 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' DAY)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:50:26.475 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:50:26.485 Error preparing query: SELECT recordid, maxepisodes, title FROM record WHERE maxepisodes > 0 ORDER BY recordid ASC, maxepisodes DESC
2010-12-08 15:50:26.491 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.record' doesn't exist

2010-12-08 15:50:26.501 Error preparing query: SELECT MIN(id),dirname FROM storagegroup WHERE hostname = :HOSTNAME AND groupname NOT IN ( 'DB Backups', 'Videos', 'Trailers', 'Coverart', 'Fanart', 'Screenshots', 'Banners' ) GROUP BY dirname;
2010-12-08 15:50:26.508 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.storagegroup' doesn't exist

2010-12-08 15:50:26.517 AutoExpire: ERROR: Filesystem Info cache is empty, unable to determine what Recordings to expire
2010-12-08 15:51:16.229 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:51:16.243 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:51:16.252 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:51:26.527 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:51:26.536 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:52:16.320 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:52:16.338 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:52:16.346 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:52:26.548 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:52:26.566 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:52:26.576 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:52:26.583 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:53:16.356 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:53:16.376 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:53:16.385 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.jobqueue' doesn't exist

2010-12-08 15:53:26.594 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-12-08 15:53:26.661 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.inuseprograms' doesn't exist

2010-12-08 15:53:58.511 MainServer::ANN Monitor
2010-12-08 15:53:58.532 adding: erden-desktop as a client (events: 0)
2010-12-08 15:53:58.621 MainServer::ANN Monitor
2010-12-08 15:53:58.996 adding: erden-desktop as a client (events: 1)
2010-12-08 15:55:02.325 MainServer::ANN Monitor
2010-12-08 15:55:02.335 adding: erden-desktop as a client (events: 0)
2010-12-08 15:55:02.343 MainServer::ANN Monitor
2010-12-08 15:55:02.349 adding: erden-desktop as a client (events: 1)
2010-12-08 15:56:16.400 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:56:16.437 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:56:16.479 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:56:26.703 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:56:26.725 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:57:16.489 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:57:16.507 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:57:16.516 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:58:16.525 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 15:58:16.544 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:58:16.553 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 15:58:26.741 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-12-08 15:58:26.799 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

```

It asks for upgrade the database. This is after trying to upgrade:

```
2010-12-08 16:01:16.627 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-12-08 16:01:16.641 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 16:01:16.650 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/1146]:
QMYSQL: Unable to execute query
Database error was:
Table 'mythconverg.recorded' doesn't exist

2010-12-08 16:02:07.297 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-12-08 16:02:07.316 Using runtime prefix = /usr
2010-12-08 16:02:07.345 Using configuration directory = /home/mythtv/.mythtv
2010-12-08 16:02:07.355 Empty LocalHostName.
2010-12-08 16:02:07.362 Using localhost value of erden-desktop
2010-12-08 16:02:07.441 New DB connection, total: 1
2010-12-08 16:02:07.458 Connected to database 'mythconverg' at host: localhost
2010-12-08 16:02:07.462 Closing DB connection named 'DBManager0'
2010-12-08 16:02:07.472 Connected to database 'mythconverg' at host: localhost
2010-12-08 16:02:07.487 DataDirectProcessor::FixProgramIDs() -- begin
2010-12-08 16:02:07.502 New DB DataDirect connection
2010-12-08 16:02:07.506 Connected to database 'mythconverg' at host: localhost
2010-12-08 16:02:08.041 DataDirectProcessor::FixProgramIDs() -- end
2010-12-08 16:02:08.050 No current database version?
2010-12-08 16:02:08.058 MythTV database schema is old. Waiting to see if DB is being upgraded.
2010-12-08 16:02:09.063 New DB connection, total: 2
2010-12-08 16:02:09.073 Connected to database 'mythconverg' at host: localhost
2010-12-08 16:02:09.087 No current database version?
2010-12-08 16:02:10.100 No current database version?
2010-12-08 16:02:11.118 No current database version?
2010-12-08 16:02:12.135 No current database version?
2010-12-08 16:02:13.264 No current database version?
2010-12-08 16:02:13.273 Timed out waiting.
2010-12-08 16:02:13.322 DB Error (StorageGroup::StorageGroup()):
Query was:
SELECT DISTINCT dirname FROM storagegroup WHERE groupname = :GROUP AND hostname = :HOSTNAME
Bindings were:
:GROUP=DB Backups, :HOSTNAME=erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':GROUP AND hostname = :HOSTNAME' at line 1

2010-12-08 16:02:13.345 DB Error (StorageGroup::StorageGroup()):
Query was:
SELECT DISTINCT dirname FROM storagegroup WHERE groupname = :GROUP
Bindings were:
:GROUP=DB Backups
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':GROUP' at line 1

2010-12-08 16:02:13.353 DB Error (StorageGroup::StorageGroup()):
Query was:
SELECT DISTINCT dirname FROM storagegroup WHERE groupname = :GROUP AND hostname = :HOSTNAME
Bindings were:
:GROUP=Default, :HOSTNAME=erden-desktop
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':GROUP AND hostname = :HOSTNAME' at line 1

2010-12-08 16:02:13.362 DB Error (StorageGroup::StorageGroup()):
Query was:
SELECT DISTINCT dirname FROM storagegroup WHERE groupname = :GROUP
Bindings were:
:GROUP=Default
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':GROUP' at line 1

2010-12-08 16:02:13.371 SG(DB Backups) Error: Unable to find any Storage Group Directories.  Using hardcoded default value of '/var/lib/mythtv/recordings'
2010-12-08 16:02:13.383 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
```

---

### Post by elgordo123 on 2010-12-08
If you think it is an older version, look at the date on the backup file.   If you go into the mythbuntu downloads, and click "Historical Downloads", you can grab an older version of mythbuntu iso.  

Install that then do a restore of the database and see if it comes up.  Dont worry about restoring your folders at that point, just make sure the database comes up.   Then do an upgrade (again checking the database) then restore your folders. 

If that doesn't work, you should probably check the actual sql backup itself and see if that 'Recorded' table is even there. 
This will take a little digging, but not much.  Assuming you are doing this on windows, or copying to a windows box: 
-Install winrar, extract the backup to your desktop 
-Go into that extacted folder, then (probably) into /var/lib/mythtv/db_backups and untar the actual SQL backup itself.
-Now open that .SQL file with notepad (or similar) it will take a while to load.   Then do a search for CREATE TABLE  (I tried CREATE TABLE 'Recorded' on mine and it didnt' work becuase of the ' symbols)
-Keep hitting Find Next until you see CREATE TABLE 'recorded' (they will probably be in alphabetical order)so you'll have to do find next a few times. 
-If it is there then you know your backup is ok, if not, then your backup is bad. If so, you will probably have to install as fresh system and do all of the scanning/setup again. 

However if I were you I'd just install the latest and rescan the music/videos etc as if you are doing a fresh install.   For your recordings just rename them and put them in the video folder.  That might be easier than fighting with all the installing/upgrading/restoring steps.   It will probably take you just as much time to do that as it will to do the above steps. 

Have fun

---

