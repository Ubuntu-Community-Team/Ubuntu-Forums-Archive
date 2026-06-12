---
title: "mythfilldatabase: slow query in cronjob"
date: 2012-12-26
forum: Mythbuntu
---

### Post by Erik-NA on 2012-12-26
mythfilldatabase is running a query which is slow according to mysql slow query log.

```
# Time: 121226  3:37:10
# User@Host: mythtv[mythtv] @ localhost []
# Query_time: 1243.440473  Lock_time: 0.000139 Rows_sent: 0  Rows_examined: 1079647204
SET timestamp=1356489430;
UPDATE program JOIN (SELECT MAX(starttime) AS starttime, title, subtitle,           LEFT(description, 1024) AS partdesc       FROM program       WHERE programid = ''       GROUP BY title, subtitle, partdesc      ) AS lasts ON program.starttime = lasts.starttime   AND program.title = lasts.title   AND program.subtitle = lasts.subtitle   AND LEFT(program.description, 1024) = lasts.partdesc SET program.last = 1 WHERE program.programid = '';
;
```

I am getting suspicious about that the sql query contains some where clauses with programid = ''. 

Could this be a consequence of the line "Dec 26 02:56:04 roes mythlogserver: mythfilldatabase[23493]: E CoreContext filldata.cpp:465 (GrabData) FillData: XMLTV grabber returned error code 2" in mythfilldatabase.log?

What does error code 2 stand for?

mythfilldatabase.log
```
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythfilldatabase version: fixes/0.26 [v0.26.0-64-g637d6d8] www.mythtv.org
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I Logger logging.cpp:306 (run) Added logging to the console
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_US.UTF-8
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mm
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to EN_US
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale EN_US
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: E CoreContext mythtranslation.cpp:73 (load) Error Loading en_us translation for module mythfrontend
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1307
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:594 (Run) Updating source #1 (sweden.tv.swedb.se) with grabber tv_grab_se_swedb
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:608 (Run) Found 35 channels for source 1 which use grabber
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:666 (Run) Grabber has capabilities: baseline manualconfig tkconfig apiconfig cache 
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:758 (Run) Checking day @ offset 0, date: Wed Dec 26 2012
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N CoreContext filldata.cpp:938 (Run) Data is already present for Wed Dec 26 2012, skipping
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:758 (Run) Checking day @ offset 1, date: Thu Dec 27 2012
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:767 (Run) Data Refresh always needed for tomorrow
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: N CoreContext filldata.cpp:916 (Run) Refreshing data for Thu Dec 27 2012
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:396 (GrabData) XMLTV config file is: /home/mythtv/.mythtv/sweden.tv.swedb.se.xmltv
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: E CoreContext filldata.cpp:465 (GrabData) FillData: XMLTV grabber returned error code 2
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: E CoreContext xmltvparser.cpp:605 (parseFile) Error in 1:1: unexpected end of file
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext icondata.cpp:164 (UpdateSourceIcons) IconData: Updating icons for sourceid: 1
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:338 (GrabDataFromFile) No programs found in data.
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext filldata.cpp:930 (Run) Grabber is no longer returning program data, finishing
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: E CoreContext main.cpp:497 (main) Failed to fetch some program info
Dec 26 02:56:04 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:538 (main) Adjusting program database end times.
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:544 (main)     1 replacements made
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:549 (main) Marking generic episodes.
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:561 (main)     Found 1973
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:567 (main) Extending non-unique programids with multiple parts.
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:618 (main)     Found 0
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:623 (main) Marking repeats.
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:637 (main)     Found 0
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:639 (main) Unmarking new episode rebroadcast repeats.
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:649 (main)     Found 0
Dec 26 02:56:05 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:661 (main) Marking episode first showings.
Dec 26 03:16:27 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:691 (main)     Found 50057
Dec 26 03:16:27 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:693 (main) Marking episode last showings.
Dec 26 03:37:10 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:723 (main)     Found 49213
Dec 26 03:37:10 mm mythlogserver: mythfilldatabase[23493]: I CoreContext main.cpp:751 (main) #012===============================================================#012| Attempting to contact the master backend for rescheduling.  |#012| If the master is not running, rescheduling will happen when |#012| the master backend is restarted.                            |#012===============================================================
Dec 26 03:37:10 mm mythlogserver: mythfilldatabase[23493]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 172.16.1.244:6543 (try 1 of 1)
Dec 26 03:37:10 mm mythlogserver: mythfilldatabase[23493]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Dec 26 03:37:10 mm mythlogserver: mythfilldatabase[23493]: I Socket mythcorecontext.cpp:1116 (readyRead) Received remote 'Clear Cache' request
Dec 26 03:37:10 mm mythlogserver: mythfilldatabase[23493]: N CoreContext main.cpp:761 (main) mythfilldatabase run complete.
```

---

