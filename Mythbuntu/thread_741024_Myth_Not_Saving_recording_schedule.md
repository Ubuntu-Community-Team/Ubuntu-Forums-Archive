---
title: "Myth Not Saving recording schedule"
date: 2008-03-31
forum: Mythbuntu
---

### Post by dflipb on 2008-03-31
I am trying to schedule a recording but when I hit save schedule, it says not recording.

I checked my tuners and they are up and running.  

I am using Hardy 8.04 and MythTv .21
Thanks!

---

### Post by dannyboy79 on 2008-03-31
are you scheduling within the listings within the frontend, within mythweb or where? what time are you making the sheduling for? if it's already in progress I don't think the scheduler will start recording if the show already started. you can check in mythweb for upcoming recordings, you may also be able to check in the frontend but I hardly ever use myth frontend. you do have your tuner associated to a source and an input correct? That's done in mythtv-setup. make sure tuner is set to /dev/video0, that you have a source like schedulesdirect, and that the source is tied to the correct tuner.

---

### Post by dflipb on 2008-03-31
I'm scheduling through mythfrontend.  

The show is supposed to record at 10pm tonight

the tuners are set to schedules direct and are working correctly.  

The Program schedule is propigated and all seems to be looking correct.

---

### Post by dannyboy79 on 2008-03-31
within the listings, does the show you want recorded have a highlighted box around it? if so, then it's set to record. you could also go into your recording schedules and ensure that the show is set to record. other than that, I am sorry I can't help. is this your first attempt and scheduling a show to record?

---

### Post by dflipb on 2008-03-31
No, This isn't my first recording.  It was working perfectly until a couple days ago...  

There is nothing listed when I go into the show scheduled recordings

ARGH

---

### Post by dannyboy79 on 2008-03-31
and what happens if you do a find shows, then schedule it that way? I am really at a loss on how to help you.

---

### Post by dflipb on 2008-03-31
This is my mythfrontend log:
```

Starting mythfrontend.real..
2008-03-31 11:43:35.915 New DB connection, total: 2
2008-03-31 11:43:35.916 Connected to database 'mythconverg' at host: localhost
2008-03-31 11:43:35.922 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-03-31 11:43:35.922 Enabled verbose msgs:  important general
2008-03-31 11:43:36.116 Unable to parse themeinfo.xml for glass-wide
2008-03-31 11:43:36.117 The theme (glass-wide) is missing a themeinfo.xml file
2008-03-31 11:43:36.445 Unable to parse themeinfo.xml for glass-wide
2008-03-31 11:43:36.445 The theme (glass-wide) is missing a themeinfo.xml file
2008-03-31 11:43:36.926 Primary screen 0.
2008-03-31 11:43:36.927 Using screen 0, 1024x768 at 0,0
2008-03-31 11:43:36.930 Switching to square mode (MythCenter)
2008-03-31 11:43:36.961 Using the Qt painter
2008-03-31 11:43:36.965 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2008-03-31 11:43:36.965 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2008-03-31 11:43:38.901 Loading from: /usr/share/mythtv/themes/MythCenter/base.xml
2008-03-31 11:43:39.060 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-31 11:43:39.165 Registering Internal as a media playback plugin.
2008-03-31 11:43:39.305 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-03-31 11:43:39.383 Failed to run 'cdrecord --scanbus'
2008-03-31 11:43:39.390 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-03-31 11:43:39.398 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-03-31 11:43:39.483 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-31 11:43:42.429 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:43:42.602 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-31 11:43:42.604 Using protocol version 40
2008-03-31 11:43:48.790 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:43:52.444 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:46:21.354 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:46:40.487 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:47:27.532 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:47:49.989 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:48:45.223 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:49:08.043 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/keyboard/en_us_ui.xml
2008-03-31 11:49:11.034 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:49:54.773 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:50:51.167 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:52:05.103 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:52:22.701 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:52:36.217 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:52:54.226 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 11:53:21.446 Could not find widget to detach
2008-03-31 11:53:21.474 Deleting UPnP client...
Starting mythfrontend.real..
2008-03-31 12:23:56.364 New DB connection, total: 2
2008-03-31 12:23:56.365 Connected to database 'mythconverg' at host: localhost
2008-03-31 12:23:56.371 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-03-31 12:23:56.371 Enabled verbose msgs:  important general
2008-03-31 12:23:56.567 Unable to parse themeinfo.xml for glass-wide
2008-03-31 12:23:56.567 The theme (glass-wide) is missing a themeinfo.xml file
2008-03-31 12:23:56.904 Unable to parse themeinfo.xml for glass-wide
2008-03-31 12:23:56.905 The theme (glass-wide) is missing a themeinfo.xml file
2008-03-31 12:23:57.392 Primary screen 0.
2008-03-31 12:23:57.393 Using screen 0, 1024x768 at 0,0
2008-03-31 12:23:57.395 Switching to square mode (MythCenter)
2008-03-31 12:23:57.425 Using the Qt painter
2008-03-31 12:23:57.429 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2008-03-31 12:23:57.429 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2008-03-31 12:23:59.333 Loading from: /usr/share/mythtv/themes/MythCenter/base.xml
2008-03-31 12:23:59.511 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-31 12:23:59.926 Registering Internal as a media playback plugin.
2008-03-31 12:24:00.080 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-03-31 12:24:00.161 Failed to run 'cdrecord --scanbus'
2008-03-31 12:24:00.169 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-03-31 12:24:00.179 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-03-31 12:24:00.268 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-31 12:24:11.476 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 12:24:13.112 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-31 12:24:13.114 Using protocol version 40
2008-03-31 12:24:14.517 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 12:24:33.220 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 12:24:40.036 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 12:24:51.515 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 12:24:56.789 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-31 12:25:06.491 Deleting UPnP client...
```

This is my BackendLog:
```
2008-03-31 12:12:55.361 mythbackend: MythBackend started as master server
2008-03-31 12:12:55.377 New DB connection, total: 3
2008-03-31 12:12:55.385 Connected to database 'mythconverg' at host: localhost
2008-03-31 12:12:56.138 New DB scheduler connection
2008-03-31 12:12:56.141 Connected to database 'mythconverg' at host: localhost
2008-03-31 12:12:56.177 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-31 12:12:56.178 Main::Registering HttpStatus Extension
2008-03-31 12:12:56.179 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-31 12:12:56.179 Enabled verbose msgs:  important general
2008-03-31 12:12:56.184 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-31 12:12:59.154 Reschedule requested for id -1.
2008-03-31 12:12:59.163 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:12:59.199 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:12:59.618 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:12:59.649 Scheduled 0 items in 0.5 = 0.01 match + 0.48 place
2008-03-31 12:12:59.652 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.5 = 0.01 match + 0.48 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:12:59.654 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:12:59.656 scheduler: Scheduled items: Scheduled 0 items in 0.5 = 0.01 match + 0.48 place
2008-03-31 12:12:59.666 Seem to be woken up by USER
2008-03-31 12:13:05.368 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('mythbackend', 7, now(), 'htpc', 'Running housekeeping thread', '' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:13:07.469 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'mythbackend' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:13:07.472 mythbackend: Running housekeeping thread
2008-03-31 12:14:16.151 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-31 12:15:17.061 Reschedule requested for id -1.
2008-03-31 12:15:20.478 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:15:20.671 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:15:20.701 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:15:20.798 Scheduled 0 items in 3.7 = 3.59 match + 0.15 place
2008-03-31 12:15:21.942 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 3.7 = 3.59 match + 0.15 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:15:25.560 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:15:25.568 scheduler: Scheduled items: Scheduled 0 items in 3.7 = 3.59 match + 0.15 place
2008-03-31 12:20:34.136 Reschedule requested for id -1.
2008-03-31 12:20:34.141 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:20:34.165 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:20:34.174 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:20:34.177 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-03-31 12:20:34.181 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.0 = 0.01 match + 0.03 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:20:34.185 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:20:34.187 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-03-31 12:23:38.171 MainServer::HandleAnnounce Monitor
2008-03-31 12:23:38.205 adding: htpc as a client (events: 0)
2008-03-31 12:23:38.207 MainServer::HandleAnnounce Monitor
2008-03-31 12:23:38.208 adding: htpc as a client (events: 1)
2008-03-31 12:23:38.215 Reschedule requested for id -1.
2008-03-31 12:23:38.248 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:23:38.287 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:23:38.358 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:23:38.366 Scheduled 0 items in 0.1 = 0.04 match + 0.11 place
2008-03-31 12:23:38.369 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.1 = 0.04 match + 0.11 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:23:38.373 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:23:38.374 scheduler: Scheduled items: Scheduled 0 items in 0.1 = 0.04 match + 0.11 place
2008-03-31 12:24:13.115 MainServer::HandleAnnounce Monitor
2008-03-31 12:24:13.120 adding: htpc as a client (events: 0)
2008-03-31 12:24:13.122 MainServer::HandleAnnounce Monitor
2008-03-31 12:24:13.122 adding: htpc as a client (events: 1)
2008-03-31 12:24:18.005 Reschedule requested for id 66.
2008-03-31 12:24:18.053 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch WHERE recordid = 66
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:18.079 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:18.087 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:18.091 Scheduled 0 items in 0.1 = 0.05 match + 0.03 place
2008-03-31 12:24:18.095 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.1 = 0.05 match + 0.03 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:24:18.099 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:24:18.100 scheduler: Scheduled items: Scheduled 0 items in 0.1 = 0.05 match + 0.03 place
2008-03-31 12:24:36.133 Reschedule requested for id 67.
2008-03-31 12:24:36.145 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch WHERE recordid = 67
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:36.183 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:36.200 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:36.206 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-03-31 12:24:36.209 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.1 = 0.01 match + 0.06 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:24:36.213 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:24:36.213 scheduler: Scheduled items: Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-03-31 12:24:54.181 Reschedule requested for id 68.
2008-03-31 12:24:54.194 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch WHERE recordid = 68
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:54.219 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:54.226 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:24:54.237 Scheduled 0 items in 0.1 = 0.01 match + 0.04 place
2008-03-31 12:24:54.241 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.1 = 0.01 match + 0.04 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:24:54.250 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:24:54.251 scheduler: Scheduled items: Scheduled 0 items in 0.1 = 0.01 match + 0.04 place
2008-03-31 12:25:52.761 Reschedule requested for id -1.
2008-03-31 12:25:52.768 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:25:52.799 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:25:52.809 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:25:52.813 Scheduled 0 items in 0.0 = 0.01 match + 0.04 place
2008-03-31 12:25:52.816 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.0 = 0.01 match + 0.04 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:25:52.820 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:25:52.821 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.01 match + 0.04 place
2008-03-31 12:29:18.606 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-31 12:31:10.226 Reschedule requested for id -1.
2008-03-31 12:31:10.233 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:31:10.257 DB Error (AddNewRecords recordmatch):
Query was:
UPDATE recordmatch  INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  LEFT JOIN oldrecorded ON   (     sched_temp_record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle) OR (program.subtitle = ''            AND oldrecorded.subtitle = '' AND program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN sched_temp_recorded recorded ON   (     sched_temp_record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup NOT IN ('LiveTV','Deleted')      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((sched_temp_record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((sched_temp_record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))        AND        (((sched_temp_record.dupmethod & 0x08) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle) OR (program.subtitle = ''            AND recorded.subtitle = '' AND program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE sched_temp_record.type   WHEN 6    THEN sched_temp_record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(sched_temp_record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(sched_temp_record.findtime, '%H:%i') hour_minute)) -                sched_temp_record.findday)/7) * 7 + sched_temp_record.findday   WHEN 7    THEN sched_temp_record.findid   ELSE 0  END) )   SET oldrecduplicate = (oldrecorded.endtime IS NOT NULL),       recduplicate = (recorded.endtime IS NOT NULL),       findduplicate = (oldfind.findid IS NOT NULL),       oldrecstatus = oldrecorded.recstatus
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:31:10.265 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/144]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

2008-03-31 12:31:10.268 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-03-31 12:31:10.271 DB Error (LogEntry):
Query was:
INSERT INTO mythlog (module, priority, logdate, host, message, details) values ('scheduler', 6, now(), 'htpc', 'Scheduled items', 'Scheduled 0 items in 0.0 = 0.01 match + 0.03 place' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:31:10.274 DB Error (DelLogEntry#1):
Query was:
SELECT logid FROM mythlog WHERE module= 'scheduler' ORDER BY logdate ASC ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/mythlog' is marked as crashed and should be repaired

2008-03-31 12:31:10.275 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.01 match + 0.03 place

```

It looks like there is a scheduler error and says it needs repair, but I don't know how to do that.

---

### Post by laga on 2008-03-31
Go to mythbuntu-control-centre, "Advanced Management", "Optimize tables".

---

### Post by dannyboy79 on 2008-03-31
if you're not running mythbuntu, then here's an exact thread solving the same exact issue.

[http://ubuntuforums.org/showthread.php?t=590723](http://ubuntuforums.org/showthread.php?t=590723)

although superm1 says it still appeared that the OP still has table corruption, he didn't post back so your results may vary. good luck

---

### Post by dflipb on 2008-03-31
> **laga said:**
> Go to mythbuntu-control-centre, "Advanced Management", "Optimize tables".

I just found that and was coming back to report that it worked perfectly!  

Thanks for the help and I hope this helps someone else as well.

---

### Post by dannyboy79 on 2008-04-01
mark the thread as solved so people know you solved your issue.

---

