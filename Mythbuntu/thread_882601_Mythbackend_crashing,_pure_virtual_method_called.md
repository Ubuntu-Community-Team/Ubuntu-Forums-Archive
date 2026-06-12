---
title: "Mythbackend crashing, pure virtual method called"
date: 2008-08-07
forum: Mythbuntu
---

### Post by mcine on 2008-08-07
I installed mythbuntu about a week ago and it is upgraded with apt-get. I have a terratec cinergy 1200 dvb-c and technotrend 2100 (well .. hw accelerated anyway, if number is not correct) dvb-c.

Only other problem that I have is that some programs are missing ,but that seems to have something to do with dual scandinavic letters like in the word "sää".

Here is the end of the backend log after the crash:
2008-08-07 07:53:25.750 Reschedule requested for id -1.
2008-08-07 07:53:26.616 Scheduled 26 items in 0.9 = 0.63 match + 0.24 place
2008-08-07 07:56:21.595 Reschedule requested for id -1.
2008-08-07 07:56:22.522 Scheduled 26 items in 0.9 = 0.69 match + 0.23 place
2008-08-07 08:00:46.006 Reschedule requested for id -1.
2008-08-07 08:00:46.879 Scheduled 26 items in 0.9 = 0.63 match + 0.24 place
2008-08-07 08:03:30.455 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-07 08:05:46.608 Reschedule requested for id -1.
2008-08-07 08:05:47.471 Scheduled 26 items in 0.9 = 0.63 match + 0.23 place
2008-08-07 08:15:02.041 MainServer::HandleAnnounce Monitor
2008-08-07 08:15:02.046 adding: mchtpc as a client (events: 0)
2008-08-07 08:16:43.123 Reschedule requested for id -1.
2008-08-07 08:16:43.981 Scheduled 26 items in 0.9 = 0.63 match + 0.23 place
2008-08-07 08:18:30.494 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-07 08:22:50.130 Reschedule requested for id -1.
2008-08-07 08:22:51.122 Scheduled 26 items in 1.0 = 0.76 match + 0.23 place
2008-08-07 08:27:44.100 DB Error (change_program):
Query was:
UPDATE program SET starttime = '2008-08-09T15:00:00',     endtime   = '2008-08-09T15:30:00' WHERE chanid    = 1241 AND       starttime = '2008-08-09T14:00:00'
Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry '1241-2008-08-09 15:00:00-0' for key 1

2008-08-07 08:28:46.892 Reschedule requested for id -1.
2008-08-07 08:28:47.753 Scheduled 26 items in 0.9 = 0.63 match + 0.23 place
2008-08-07 08:31:40.385 Reschedule requested for id -1.
2008-08-07 08:31:41.275 Scheduled 26 items in 0.9 = 0.64 match + 0.24 place
pure virtual method called
terminate called without an active exception2008-08-07 07:53:25.750 Reschedule requested for id -1.
2008-08-07 07:53:26.616 Scheduled 26 items in 0.9 = 0.63 match + 0.24 place
2008-08-07 07:56:21.595 Reschedule requested for id -1.
2008-08-07 07:56:22.522 Scheduled 26 items in 0.9 = 0.69 match + 0.23 place
2008-08-07 08:00:46.006 Reschedule requested for id -1.
2008-08-07 08:00:46.879 Scheduled 26 items in 0.9 = 0.63 match + 0.24 place
2008-08-07 08:03:30.455 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-07 08:05:46.608 Reschedule requested for id -1.
2008-08-07 08:05:47.471 Scheduled 26 items in 0.9 = 0.63 match + 0.23 place
2008-08-07 08:15:02.041 MainServer::HandleAnnounce Monitor
2008-08-07 08:15:02.046 adding: mchtpc as a client (events: 0)
2008-08-07 08:16:43.123 Reschedule requested for id -1.
2008-08-07 08:16:43.981 Scheduled 26 items in 0.9 = 0.63 match + 0.23 place
2008-08-07 08:18:30.494 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-07 08:22:50.130 Reschedule requested for id -1.
2008-08-07 08:22:51.122 Scheduled 26 items in 1.0 = 0.76 match + 0.23 place
2008-08-07 08:27:44.100 DB Error (change_program):
Query was:
UPDATE program SET starttime = '2008-08-09T15:00:00',     endtime   = '2008-08-09T15:30:00' WHERE chanid    = 1241 AND       starttime = '2008-08-09T14:00:00'
Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry '1241-2008-08-09 15:00:00-0' for key 1

2008-08-07 08:28:46.892 Reschedule requested for id -1.
2008-08-07 08:28:47.753 Scheduled 26 items in 0.9 = 0.63 match + 0.23 place
2008-08-07 08:31:40.385 Reschedule requested for id -1.
2008-08-07 08:31:41.275 Scheduled 26 items in 0.9 = 0.64 match + 0.24 place
pure virtual method called
terminate called without an active exception

---

### Post by mcine on 2008-08-10
crashed again , but this time bit different messages. Still relating to scheduling and sql.

2008-08-10 10:16:10.589 DB Error (GetOverlappingPrograms 1):
Query was:
SELECT title,          subtitle,      description,        category,       category_type,        starttime,      endtime,        subtitletypes+0,audioprop+0,   videoprop+0,
      seriesid,       programid,        partnumber,     parttotal,        syndicatedepisodenumber,        airdate,        originalairdate,        previouslyshown FROM progra
m WHERE chanid   = 1017 AND       manualid = 0       AND       ( ( starttime >= '2008-08-10T17:08:07' AND starttime <  '2008-08-10T17:55:29' ) OR         ( endtime   >  '200
8-08-10T17:08:07' AND endtime   <= '2008-08-10T17:55:29' ) )
No error type from QSqlError?  Strange...
2008-08-10 10:16:10.594 DB Error (GetOverlappingPrograms 1):
Query was:
SELECT title,          subtitle,      description,        category,       category_type,        starttime,      endtime,        subtitletypes+0,audioprop+0,   videoprop+0,
      seriesid,       programid,        partnumber,     parttotal,        syndicatedepisodenumber,        airdate,        originalairdate,        previouslyshown FROM progra
m WHERE chanid   = 1017 AND       manualid = 0       AND       ( ( starttime >= '2008-08-10T17:55:29' AND starttime <  '2008-08-10T18:00:00' ) OR         ( endtime   >  '200
8-08-10T17:55:29' AND endtime   <= '2008-08-10T18:00:00' ) )
No error type from QSqlError?  Strange...
2008-08-10 10:16:10.996 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:10.998 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.000 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.002 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.002 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.008 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.014 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.020 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.022 DB Error (GetOverlappingPrograms 1):

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.025 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.029 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.033 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.037 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.041 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.045 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.049 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.053 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.057 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.061 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.065 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.069 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.073 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...
2008-08-10 10:16:11.077 DB Error (GetOverlappingPrograms 1):
Query was:

No error type from QSqlError?  Strange...

---

### Post by laga on 2008-08-10
Can you run optimize_mythdb.pl? It should be located in ```
/usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl
```

---

### Post by mcine on 2008-08-13
I did not find that script, but I found button optimize tables from mythweb and I pressed that .. I did not get any outcome. Lets see if it still crashes.

---

### Post by newlinux on 2008-08-13
/usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

is the location on my system...

---

### Post by mcine on 2008-08-14
thanks, there it was. just needed to add execution rights. . I wonder what I have typoed, since I did not find that with find-command yesterday.

Seemed to do lots of stuff, I hope it fixed the problem:
Analyzed: `mythconverg`.`record`
Repaired/Optimized: `mythconverg`.`recorded`
Analyzed: `mythconverg`.`recorded`
Repaired/Optimized: `mythconverg`.`recordedcredits`
Analyzed: `mythconverg`.`recordedcredits`
Repaired/Optimized: `mythconverg`.`recordedfile`
Analyzed: `mythconverg`.`recordedfile`
Repaired/Optimized: `mythconverg`.`recordedmarkup`
Analyzed: `mythconverg`.`recordedmarkup`
Repaired/Optimized: `mythconverg`.`recordedprogram`
Analyzed: `mythconverg`.`recordedprogram`
Repaired/Optimized: `mythconverg`.`recordedrating`
Analyzed: `mythconverg`.`recordedrating`
Repaired/Optimized: `mythconverg`.`recordedseek`
Analyzed: `mythconverg`.`recordedseek`
Repaired/Optimized: `mythconverg`.`recordingprofiles`
Analyzed: `mythconverg`.`recordingprofiles`
Repaired/Optimized: `mythconverg`.`recordmatch`
Analyzed: `mythconverg`.`recordmatch`
Repaired/Optimized: `mythconverg`.`romdb`
Analyzed: `mythconverg`.`romdb`
Repaired/Optimized: `mythconverg`.`schemalock`
Analyzed: `mythconverg`.`schemalock`
Repaired/Optimized: `mythconverg`.`settings`
Analyzed: `mythconverg`.`settings`
Repaired/Optimized: `mythconverg`.`storagegroup`
Analyzed: `mythconverg`.`storagegroup`
Repaired/Optimized: `mythconverg`.`streams`
Analyzed: `mythconverg`.`streams`
Repaired/Optimized: `mythconverg`.`tvchain`
Analyzed: `mythconverg`.`tvchain`
Repaired/Optimized: `mythconverg`.`upnpmedia`
Analyzed: `mythconverg`.`upnpmedia`
Repaired/Optimized: `mythconverg`.`videocast`
Analyzed: `mythconverg`.`videocast`
Repaired/Optimized: `mythconverg`.`videocategory`
Analyzed: `mythconverg`.`videocategory`
Repaired/Optimized: `mythconverg`.`videocountry`
Analyzed: `mythconverg`.`videocountry`
Repaired/Optimized: `mythconverg`.`videogenre`
Analyzed: `mythconverg`.`videogenre`
Repaired/Optimized: `mythconverg`.`videometadata`
Analyzed: `mythconverg`.`videometadata`
Repaired/Optimized: `mythconverg`.`videometadatacast`
Analyzed: `mythconverg`.`videometadatacast`
Repaired/Optimized: `mythconverg`.`videometadatacountry`
Analyzed: `mythconverg`.`videometadatacountry`
Repaired/Optimized: `mythconverg`.`videometadatagenre`
Analyzed: `mythconverg`.`videometadatagenre`
Repaired/Optimized: `mythconverg`.`videosource`
Analyzed: `mythconverg`.`videosource`
Repaired/Optimized: `mythconverg`.`videotypes`
Analyzed: `mythconverg`.`videotypes`
Repaired/Optimized: `mythconverg`.`weatherdatalayout`
Analyzed: `mythconverg`.`weatherdatalayout`
Repaired/Optimized: `mythconverg`.`weatherscreens`
Analyzed: `mythconverg`.`weatherscreens`
Repaired/Optimized: `mythconverg`.`weathersourcesettings`
Analyzed: `mythconverg`.`weathersourcesettings`
Repaired/Optimized: `mythconverg`.`websites`
Analyzed: `mythconverg`.`websites`

---

