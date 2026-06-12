---
title: "Capture Cards Keep Disappearing"
date: 2016-06-02
forum: Mythbuntu
---

### Post by km782 on 2016-06-02
I have been running Mythtv 0.26 for several years now without any issues.  Once I got it working I turned off all updates and haven't made any changes to my system.  However, all of the sudden it stopped making recordings.  On Mythweb the Upcoming Recordings section is blank even though I have guide data and plenty of shows to record.  The problem is if I go into Mythbackend the capture cards are gone.  If I try to re-add them it doesn't work (the capture card does not show up after I click Finish).  I have to go and select Delete All Capture Cards first.  Then I can go and re-add both tuners (I have the Hauppauge 2250).  Then I link both to Schedules Direct on the Input Connections and I am all set.  Everything will be back to normal until a day or two later when the capture cards disappear again.  I tried running the optimize script and upgrading to 0.27.  This has not helped.  

The log from mythbackend for the last two days is below.  There is something about a driver and/or database error and the capture card marked as crashed.  Can anyone make suggestions for what could be causing this and how to fix it?  I appreciate the help.


```
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.6-18-gaba4858] www.mythtv.org
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I Logger logging.cpp:308 (run) Added logging to the console
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of HTPC
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun  1 07:10:07 HTPC mythbackend: mythbackend[2497]: C CoreContext main.cpp:130 (main) Failed to init MythContext.
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.6-18-gaba4858] www.mythtv.org
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I Logger logging.cpp:308 (run) Added logging to the console
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of HTPC
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: C CoreContext main.cpp:130 (main) Failed to init MythContext.
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Jun  1 07:10:23 HTPC mythbackend: mythbackend[2645]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.6-18-gaba4858] www.mythtv.org
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I Logger logging.cpp:308 (run) Added logging to the console
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of HTPC
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: C CoreContext main.cpp:130 (main) Failed to init MythContext.
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Jun  1 07:10:38 HTPC mythbackend: mythbackend[2778]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.6-18-gaba4858] www.mythtv.org
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I Logger logging.cpp:308 (run) Added logging to the console
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of HTPC
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Jun  1 07:16:00 HTPC mythbackend: mythbackend[1917]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  1 07:16:01 HTPC mythbackend: mythbackend[1917]: N CoreContext mythcorecontext.cpp:1634 (InitLocale) Setting QT default locale to EN_US
Jun  1 07:16:01 HTPC mythbackend: mythbackend[1917]: I CoreContext mythcorecontext.cpp:1667 (SaveLocaleDefaults) Current locale EN_US
Jun  1 07:16:01 HTPC mythbackend: mythbackend[1917]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun  1 07:16:02 HTPC mythbackend: mythbackend[1917]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Jun  1 07:16:02 HTPC mythbackend: mythbackend[1917]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Jun  1 07:16:02 HTPC mythbackend: mythbackend[1917]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: E CoreContext mythdb.cpp:183 (DBError) DB Error (Querying Recorders):#012Query was:#012UPDATE recorded SET basename = CONCAT(chanid, '_', DATE_FORMAT(starttime, '%Y%m%d%H%i00'), '_', DATE_FORMAT(endtime, '%Y%m%d%H%i00'), '.nuv') WHERE basename = '';#012Driver error was [2/144]:#012QMYSQL: Unable to execute query#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Jun  1 07:16:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Jun  1 07:16:04 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6544
Jun  1 07:16:04 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 192.168.1.5:6544
Jun  1 07:16:04 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6544
Jun  1 07:16:04 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::20f:66ff:fe70:465e%wlan0]:6544
Jun  1 07:16:05 HTPC mythbackend: mythbackend[1917]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Jun  1 07:16:05 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6543
Jun  1 07:16:05 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 192.168.1.5:6543
Jun  1 07:16:05 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6543
Jun  1 07:16:05 HTPC mythbackend: mythbackend[1917]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::20f:66ff:fe70:465e%wlan0]:6543
Jun  1 07:16:05 HTPC mythbackend: mythbackend[1917]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 07:16:07 HTPC mythbackend: mythbackend[1917]: I CoreContext bonjourregister.cpp:115 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on HTPC' type '_mythbackend._tcp.' domain: 'local.'
Jun  1 07:16:17 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 07:16:17 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 07:16:17 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 07:16:17 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 1)
Jun  1 07:16:36 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 07:16:36 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 07:16:36 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 07:16:36 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 07:17:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'DBCleanup'.
Jun  1 07:17:03 HTPC mythbackend: mythbackend[1917]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'DBCleanup'.
Jun  1 07:17:06 HTPC mythbackend: mythbackend[1917]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'DBCleanup' Finished Successfully.
Jun  1 07:17:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 07:32:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 07:47:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 08:02:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 08:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 08:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 08:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 08:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 08:17:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 08:32:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 08:47:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 09:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 09:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 09:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 09:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 09:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 09:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 09:32:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 09:47:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 10:02:22 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 10:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 10:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 10:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 10:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 10:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 10:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 10:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 11:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 11:11:21 HTPC mythbackend: mythbackend[1917]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 5
Jun  1 11:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 11:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 11:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 11:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 11:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 11:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 11:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 12:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 12:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 12:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 12:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 12:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 12:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 12:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 12:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 12:48:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'JobQueueRecover'.
Jun  1 12:48:03 HTPC mythbackend: mythbackend[1917]: I HouseKeeping mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 5
Jun  1 12:48:03 HTPC mythbackend: mythbackend[1917]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'JobQueueRecover'.
Jun  1 12:48:03 HTPC mythbackend: mythbackend[1917]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'JobQueueRecover' Finished Successfully.
Jun  1 13:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 13:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 13:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 13:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 13:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 13:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 13:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 13:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 14:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 14:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 14:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 14:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 14:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 14:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 14:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 14:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 15:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 15:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 15:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 15:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 15:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 15:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 15:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 15:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 16:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 16:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 16:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 16:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 16:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 16:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 16:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 16:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 17:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 17:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 17:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 17:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 17:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 17:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 17:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 17:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'MythFillDB'.
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I HouseKeeping mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 5
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'MythFillDB'.
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 17:55:03 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 17:55:30 HTPC mythbackend: mythbackend[1917]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 5
Jun  1 17:55:30 HTPC mythbackend: mythbackend[1917]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'MythFillDB' Finished Successfully.
Jun  1 18:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 18:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 18:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 18:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 18:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 18:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 18:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 18:47:11 HTPC mythbackend: mythbackend[1917]: I SSDP mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 5
Jun  1 18:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 19:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 19:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 19:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 19:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 19:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 19:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 19:32:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 19:47:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 20:02:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 20:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 20:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 20:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 20:16:21 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 20:17:23 HTPC mythbackend: mythbackend[1917]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 20:22:32 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:22:32 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:22:35 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:22:35 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:22:37 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:22:37 HTPC mythbackend: mythbackend[1917]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:23:09 HTPC mythbackend: mythbackend[1917]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 13
Jun  1 20:23:25 HTPC mythbackend: mythbackend[1917]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID 1, UID 0, Value 0x00000000
Jun  1 20:23:25 HTPC mythbackend: mythbackend[1917]: N CoreContext main_helpers.cpp:706 (run_backend) MythBackend exiting
Jun  1 20:23:25 HTPC mythbackend: mythbackend[1917]: I CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_mythbackend._tcp.' on 'Mythbackend on HTPC'
Jun  1 20:23:27 HTPC mythbackend: mythbackend[1917]: I CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.6-18-gaba4858] www.mythtv.org
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I Logger logging.cpp:308 (run) Added logging to the console
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of HTPC
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N CoreContext mythcorecontext.cpp:1634 (InitLocale) Setting QT default locale to EN_US
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I CoreContext mythcorecontext.cpp:1667 (SaveLocaleDefaults) Current locale EN_US
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Jun  1 20:27:56 HTPC mythbackend: mythbackend[3487]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source 'EIT' is defined, but is not attached to a card input.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext programinfo.cpp:2137 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6544
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 192.168.1.5:6544
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6544
Jun  1 20:27:57 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::20f:66ff:fe70:465e%wlan0]:6544
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 127.0.0.1:6543
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP 192.168.1.5:6543
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [::1]:6543
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I CoreContext serverpool.cpp:404 (listen) Listening on TCP [fe80::20f:66ff:fe70:465e%wlan0]:6543
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 20:27:58 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:27:59 HTPC mythbackend: mythbackend[3487]: I CoreContext bonjourregister.cpp:115 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on HTPC' type '_mythbackend._tcp.' domain: 'local.'
Jun  1 20:28:00 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Jun  1 20:28:00 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 106 items in 0.4 = 0.14 match + 0.20 check + 0.08 place
Jun  1 20:28:00 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2319 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Jun  1 20:28:13 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - MythFillDatabase
Jun  1 20:28:14 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 102 items in 0.2 = 0.02 match + 0.13 check + 0.07 place
Jun  1 20:28:57 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'LogClean'.
Jun  1 20:28:57 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'LogClean'.
Jun  1 20:28:57 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'LogClean' Finished Successfully.
Jun  1 20:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 20:29:30 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:29:30 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 1)
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:30:51 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 1)
Jun  1 20:31:07 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 20:31:07 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 20:31:07 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 20:31:07 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 20:31:54 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:31:54 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:31:59 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 20:31:59 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:844 (prepare) Error preparing query: SELECT cardtype, videodevice FROM capturecard WHERE cardid = :CARDID 
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:846 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:844 (prepare) Error preparing query: SELECT cardtype, videodevice FROM capturecard WHERE cardid = :CARDID 
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:846 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:844 (prepare) Error preparing query: SELECT cardtype, videodevice FROM capturecard WHERE cardid = :CARDID 
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:846 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:844 (prepare) Error preparing query: SELECT cardtype, videodevice FROM capturecard WHERE cardid = :CARDID 
Jun  1 20:32:14 HTPC mythbackend: mythbackend[3487]: E HttpServer47 mythdbcon.cpp:846 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  1 20:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 20:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 21:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 21:21:16 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  1 21:21:16 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  1 21:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 21:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 21:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 21:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 21:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 21:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: I Scheduler mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for PLACE PrepareToRecord
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: E Scheduler mythdbcon.cpp:844 (prepare) Error preparing query: SELECT     c.chanid,         c.sourceid,           p.starttime,           p.endtime,        p.title,              p.subtitle,            p.description,    c.channum,            c.callsign,            c.name,           oldrecduplicate,      p.category,            sched_temp_record.recpriority, sched_temp_record.dupin,   recduplicate,          findduplicate,    sched_temp_record.type,        sched_temp_record.recordid,     p.starttime - INTERVAL sched_temp_record.startoffset     minute AS recstartts,     p.endtime + INTERVAL sched_temp_record.endoffset     minute AS recendts,                                             p.previouslyshown,     sched_temp_record.recgroup, sched_temp_record.dupmethod,  c.commmethod,          capturecard.cardid, cardinput.cardinputid,p.seriesid,          p.programid,       sched_temp_record.inetref,    p.category_type,       p.airdate,         p.stars,             p.originalairdate,     sched_temp_record.inactive, sched_temp_record.parentid,   recordmatch.findid,     sched_temp_record.playgroup, oldrecstatus.recstatus,     oldrecstatus.reactivate, p.videoprop+0,         p.subtitletypes+0, p.audioprop+0,   sched_temp_record.storagegroup,     capturecard.hostname, recordmatch.oldrecstatus, NULL,     oldrecstatus.future, cardinput.schedorder,     p.syndicatedepisodenumber, p.partnumber, p.parttotal,     c.mplexid, c.recpriority + cardinput.recpriority + (cardinput.cardinputid = sched_temp_record.prefinput) * 1 + (p.hdtv > 0 OR FIND_IN_SET('HDTV', p.videoprop) > 0) * 1 AS powerpriority FROM recordmatch INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid) INNER JOIN program AS p ON ( recordmatch.chanid    = p.chanid    AND      recordmatch.starttime = p.starttime AND      recordmatch.manualid  = p.manualid ) INNER JOIN channel AS c ON ( c.chanid = p.chanid ) INNER JOIN cardinput ON (c.sourceid = cardinput.sourceid) INNE
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: E Scheduler mythdbcon.cpp:846 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: E Scheduler mythdb.cpp:183 (DBError) DB Error (AddNewRecords):#012Query was:#012SELECT     c.chanid,         c.sourceid,           p.starttime,           p.endtime,        p.title,              p.subtitle,            p.description,    c.channum,            c.callsign,            c.name,           oldrecduplicate,      p.category,            sched_temp_record.recpriority, sched_temp_record.dupin,   recduplicate,          findduplicate,    sched_temp_record.type,        sched_temp_record.recordid,     p.starttime - INTERVAL sched_temp_record.startoffset     minute AS recstartts,     p.endtime + INTERVAL sched_temp_record.endoffset     minute AS recendts,                                             p.previouslyshown,     sched_temp_record.recgroup, sched_temp_record.dupmethod,  c.commmethod,          capturecard.cardid, cardinput.cardinputid,p.seriesid,          p.programid,       sched_temp_record.inetref,    p.category_type,       p.airdate,         p.stars,             p.originalairdate,     sched_temp_record.inactive, sched_temp_record.parentid,   recordmatch.findid,     sched_temp_record.playgroup, oldrecstatus.recstatus,     oldrecstatus.reactivate, p.videoprop+0,         p.subtitletypes+0, p.audioprop+0,   sched_temp_record.storagegroup,     capturecard.hostname, recordmatch.oldrecstatus, NULL,     oldrecstatus.future, cardinput.schedorder,     p.syndicatedepisodenumber, p.partnumber, p.parttotal,     c.mplexid, c.recpriority + cardinput.recpriority + (cardinput.cardinputid = sched_temp_record.prefinput) * 1 + (p.hdtv > 0 OR FIND_IN_SET('HDTV', p.videoprop) > 0) * 1 AS powerpriority FROM recordmatch INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid) INNER JOIN program AS p ON ( recordmatch.chanid    = p.chanid    AND      recordmatch.starttime = p.starttime AND      recordmatch.manualid  = p.manualid ) INNER JOIN channel AS c ON ( c.chanid = p.chanid ) INNER JOIN cardinput ON (c.sourceid = cardinput.
Jun  1 21:57:00 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.00 check + 0.00 place
Jun  1 21:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 22:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 22:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 22:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 22:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 22:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 22:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 22:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 22:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 23:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 23:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 23:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  1 23:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  1 23:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  1 23:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  1 23:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  1 23:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 00:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 00:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 00:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 00:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 00:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 00:30:52 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 00:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 00:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 01:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 01:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 01:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 01:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 01:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 01:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 01:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 01:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 02:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 02:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 02:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 02:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 02:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 02:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 02:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 02:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 03:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 03:21:58 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'DBCleanup'.
Jun  2 03:21:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 03:21:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'DBCleanup'.
Jun  2 03:21:59 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'DBCleanup' Finished Successfully.
Jun  2 03:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 03:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 03:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 03:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 03:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 03:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 03:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 04:12:58 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'ThemeUpdateNotifications'.
Jun  2 04:12:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'ThemeUpdateNotifications'.
Jun  2 04:12:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:386 (DoRun) Loading themes for 0.27
Jun  2 04:12:59 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:400 (DoRun) Loading themes for 0.27.6
Jun  2 04:12:59 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:439 (LoadVersion) HouseKeeper: Failed to download http://themes.mythtv.org/themes/repository/0.27.6/themes.zipremote themes info package.
Jun  2 04:12:59 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:400 (DoRun) Loading themes for 0.27.5
Jun  2 04:12:59 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:400 (DoRun) Loading themes for 0.27.4
Jun  2 04:13:00 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:400 (DoRun) Loading themes for 0.27.3
Jun  2 04:13:00 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:439 (LoadVersion) HouseKeeper: Failed to download http://themes.mythtv.org/themes/repository/0.27.3/themes.zipremote themes info package.
Jun  2 04:13:00 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:400 (DoRun) Loading themes for 0.27.2
Jun  2 04:13:00 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:439 (LoadVersion) HouseKeeper: Failed to download http://themes.mythtv.org/themes/repository/0.27.2/themes.zipremote themes info package.
Jun  2 04:13:00 HTPC mythbackend: mythbackend[3487]: I HouseKeeping backendhousekeeper.cpp:400 (DoRun) Loading themes for 0.27.1
Jun  2 04:13:01 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'ThemeUpdateNotifications' Finished Successfully.
Jun  2 04:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 04:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 04:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 04:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 04:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 04:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 04:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 04:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 05:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 05:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 05:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 05:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 05:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 05:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 05:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 05:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 06:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 06:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 06:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 06:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 06:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 06:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 06:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 06:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 07:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 07:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 07:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 07:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 07:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 07:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 07:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 07:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 08:03:58 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'JobQueueRecover'.
Jun  2 08:03:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 08:03:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'JobQueueRecover'.
Jun  2 08:03:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'JobQueueRecover' Finished Successfully.
Jun  2 08:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 08:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 08:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 08:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 08:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 08:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 08:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 08:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 09:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 09:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 09:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 09:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 09:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 09:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 09:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 09:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 10:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 10:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 10:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 10:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 10:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 10:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 10:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 10:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 11:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 11:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 11:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 11:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 11:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 11:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 11:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 11:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 12:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 12:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 12:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 12:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 12:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 12:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 12:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 12:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 13:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'MythFillDB'.
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'MythFillDB'.
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 13:24:58 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - MythFillDatabase
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: I Scheduler mythdbcon.cpp:241 (Reconnect) MySQL reconnected successfully
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'MythFillDB' Finished Successfully.
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: I Scheduler mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: E Scheduler mythdbcon.cpp:844 (prepare) Error preparing query: SELECT     c.chanid,         c.sourceid,           p.starttime,           p.endtime,        p.title,              p.subtitle,            p.description,    c.channum,            c.callsign,            c.name,           oldrecduplicate,      p.category,            sched_temp_record.recpriority, sched_temp_record.dupin,   recduplicate,          findduplicate,    sched_temp_record.type,        sched_temp_record.recordid,     p.starttime - INTERVAL sched_temp_record.startoffset     minute AS recstartts,     p.endtime + INTERVAL sched_temp_record.endoffset     minute AS recendts,                                             p.previouslyshown,     sched_temp_record.recgroup, sched_temp_record.dupmethod,  c.commmethod,          capturecard.cardid, cardinput.cardinputid,p.seriesid,          p.programid,       sched_temp_record.inetref,    p.category_type,       p.airdate,         p.stars,             p.originalairdate,     sched_temp_record.inactive, sched_temp_record.parentid,   recordmatch.findid,     sched_temp_record.playgroup, oldrecstatus.recstatus,     oldrecstatus.reactivate, p.videoprop+0,         p.subtitletypes+0, p.audioprop+0,   sched_temp_record.storagegroup,     capturecard.hostname, recordmatch.oldrecstatus, NULL,     oldrecstatus.future, cardinput.schedorder,     p.syndicatedepisodenumber, p.partnumber, p.parttotal,     c.mplexid, c.recpriority + cardinput.recpriority + (cardinput.cardinputid = sched_temp_record.prefinput) * 1 + (p.hdtv > 0 OR FIND_IN_SET('HDTV', p.videoprop) > 0) * 1 AS powerpriority FROM recordmatch INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid) INNER JOIN program AS p ON ( recordmatch.chanid    = p.chanid    AND      recordmatch.starttime = p.starttime AND      recordmatch.manualid  = p.manualid ) INNER JOIN channel AS c ON ( c.chanid = p.chanid ) INNER JOIN cardinput ON (c.sourceid = cardinput.sourceid) INNE
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: E Scheduler mythdbcon.cpp:846 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/capturecard' is marked as crashed and last (automatic?) repair failed
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: E Scheduler mythdb.cpp:183 (DBError) DB Error (AddNewRecords):#012Query was:#012SELECT     c.chanid,         c.sourceid,           p.starttime,           p.endtime,        p.title,              p.subtitle,            p.description,    c.channum,            c.callsign,            c.name,           oldrecduplicate,      p.category,            sched_temp_record.recpriority, sched_temp_record.dupin,   recduplicate,          findduplicate,    sched_temp_record.type,        sched_temp_record.recordid,     p.starttime - INTERVAL sched_temp_record.startoffset     minute AS recstartts,     p.endtime + INTERVAL sched_temp_record.endoffset     minute AS recendts,                                             p.previouslyshown,     sched_temp_record.recgroup, sched_temp_record.dupmethod,  c.commmethod,          capturecard.cardid, cardinput.cardinputid,p.seriesid,          p.programid,       sched_temp_record.inetref,    p.category_type,       p.airdate,         p.stars,             p.originalairdate,     sched_temp_record.inactive, sched_temp_record.parentid,   recordmatch.findid,     sched_temp_record.playgroup, oldrecstatus.recstatus,     oldrecstatus.reactivate, p.videoprop+0,         p.subtitletypes+0, p.audioprop+0,   sched_temp_record.storagegroup,     capturecard.hostname, recordmatch.oldrecstatus, NULL,     oldrecstatus.future, cardinput.schedorder,     p.syndicatedepisodenumber, p.partnumber, p.parttotal,     c.mplexid, c.recpriority + cardinput.recpriority + (cardinput.cardinputid = sched_temp_record.prefinput) * 1 + (p.hdtv > 0 OR FIND_IN_SET('HDTV', p.videoprop) > 0) * 1 AS powerpriority FROM recordmatch INNER JOIN sched_temp_record ON (recordmatch.recordid = sched_temp_record.recordid) INNER JOIN program AS p ON ( recordmatch.chanid    = p.chanid    AND      recordmatch.starttime = p.starttime AND      recordmatch.manualid  = p.manualid ) INNER JOIN channel AS c ON ( c.chanid = p.chanid ) INNER JOIN cardinput ON (c.sourceid = cardinput.
Jun  2 13:25:24 HTPC mythbackend: mythbackend[3487]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 0 items in 0.2 = 0.05 match + 0.13 check + 0.02 place
Jun  2 13:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 13:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 13:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 13:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 13:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 13:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 13:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 14:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 14:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 14:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 14:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 14:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 14:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 14:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 14:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 15:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 15:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 15:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 15:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 15:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 15:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 15:38:12 HTPC mythbackend: mythbackend[3487]: I SSDP mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 15:38:14 HTPC mythbackend: mythbackend[3487]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Jun  2 15:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 15:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 16:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 16:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 16:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 16:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 16:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 16:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 16:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 16:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 17:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 17:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 17:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 17:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 17:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 17:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 17:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 17:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 18:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 18:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 18:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 18:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 18:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 18:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 18:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 18:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 19:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 19:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 19:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 19:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 19:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 19:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 19:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 19:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 20:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 20:29:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 20:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 20:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 20:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 20:30:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 20:44:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 20:59:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 21:14:16 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 21:29:17 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 21:44:17 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 21:59:17 HTPC mythbackend: mythbackend[3487]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Jun  2 22:05:50 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  2 22:05:50 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  2 22:05:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  2 22:05:53 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  2 22:05:57 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Jun  2 22:05:57 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: HTPC as a client (events: 0)
Jun  2 22:06:47 HTPC mythbackend: mythbackend[3487]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 11
Jun  2 22:07:03 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Playback
Jun  2 22:07:03 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: htpc as a client (events: 0)
Jun  2 22:07:03 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1564 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun  2 22:07:03 HTPC mythbackend: mythbackend[3487]: I ProcessRequest mainserver.cpp:1566 (HandleAnnounce) adding: htpc as a remote file transfer
Jun  2 22:07:32 HTPC mythbackend: mythbackend[3487]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID 1, UID 0, Value 0x00000000
Jun  2 22:07:32 HTPC mythbackend: mythbackend[3487]: N CoreContext main_helpers.cpp:706 (run_backend) MythBackend exiting
Jun  2 22:07:32 HTPC mythbackend: mythbackend[3487]: I CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_mythbackend._tcp.' on 'Mythbackend on HTPC'
Jun  2 22:07:33 HTPC mythbackend: mythbackend[3487]: I CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.


```

---

### Post by aelfric55 on 2016-06-04
Looks like the /capturecard table (at the very least) is crashed in your mythconverg database. The optimize script doesn't actually repair much of anything; you'll probably do better fixing it from a prompt. It will be nice also if you have a reasonably recent database backup floating around on your system, just in case. You won't be able to do a new backup with any sort of mysqldump utility on a database with crashed tables until the tables are repaired. Mysqldump will just kick off a "database with crashed tables" error and exit.

So from a prompt:```
mysqlcheck -A -e --auto-repair  -u mythtv -p
```assuming the account running your mythtv installation is "mythtv". The password that you'll be prompted to provide is the one for mysql (usually to be found from the config.xml under the ./mythtv directory in the main user's account, among other places.) This command can take some considerable amount of time to run, depending on the size of your mythconverg database. It usually takes between 1 to 2 hours on my system with a ca. 3000 recording database. But the routine is thorough: when it finishes, assuming it finishes correctly, you should be good to go.

---

### Post by km782 on 2016-06-07
> **aelfric55 said:**
> Looks like the /capturecard table (at the very least) is crashed in your mythconverg database. The optimize script doesn't actually repair much of anything; you'll probably do better fixing it from a prompt. It will be nice also if you have a reasonably recent database backup floating around on your system, just in case. You won't be able to do a new backup with any sort of mysqldump utility on a database with crashed tables until the tables are repaired. Mysqldump will just kick off a "database with crashed tables" error and exit.

So from a prompt:```
mysqlcheck -A -e --auto-repair  -u mythtv -p
```assuming the account running your mythtv installation is "mythtv". The password that you'll be prompted to provide is the one for mysql (usually to be found from the config.xml under the ./mythtv directory in the main user's account, among other places.) This command can take some considerable amount of time to run, depending on the size of your mythconverg database. It usually takes between 1 to 2 hours on my system with a ca. 3000 recording database. But the routine is thorough: when it finishes, assuming it finishes correctly, you should be good to go.

Thank you very much for the help. Unfortunately this hasn't fixed the problem. I tried running mysqlcheck and on my system it ran pretty quickly (less than 30 seconds). I'm not sure if that is an indication of a problem. I probably don't have 3000 recordings in the database but it has been running for a few years so it isn't new either. Here is the output from the terminal:

```
htpc@HTPC:~$ mysqlcheck -A -e --auto-repair -u mythtv -p
Enter password: 
mythconverg.archiveitems
warning  : Table is marked as crashed and last repair failed
status   : OK
mythconverg.callsignnetworkmap
warning  : Table is marked as crashed and last repair failed
status   : OK
mythconverg.capturecard
warning  : Table is marked as crashed and last repair failed
status   : OK
mythconverg.cardinput                              OK
mythconverg.channel                                OK
mythconverg.channelgroup                           OK
mythconverg.channelgroupnames                      OK
mythconverg.channelscan                            OK
mythconverg.channelscan_channel                    OK
mythconverg.channelscan_dtv_multiplex              OK
mythconverg.codecparams                            OK
mythconverg.credits                                OK
mythconverg.customexample                          OK
mythconverg.diseqc_config                          OK
mythconverg.diseqc_tree                            OK
mythconverg.displayprofilegroups                   OK
mythconverg.displayprofiles                        OK
mythconverg.dtv_multiplex                          OK
mythconverg.dtv_privatetypes                       OK
mythconverg.dvdbookmark                            OK
mythconverg.dvdinput                               OK
mythconverg.dvdtranscode                           OK
mythconverg.eit_cache                              OK
mythconverg.filemarkup                             OK
mythconverg.gallerymetadata                        OK
mythconverg.gamemetadata                           OK
mythconverg.gameplayers                            OK
mythconverg.housekeeping                           OK
mythconverg.inputgroup                             OK
mythconverg.internetcontent                        OK
mythconverg.internetcontentarticles                OK
mythconverg.inuseprograms                          OK
mythconverg.iptv_channel                           OK
mythconverg.jobqueue                               OK
mythconverg.jumppoints                             OK
mythconverg.keybindings                            OK
mythconverg.keyword                                OK
mythconverg.livestream                             OK
mythconverg.logging                                OK
mythconverg.movies_movies                          OK
mythconverg.movies_showtimes                       OK
mythconverg.movies_theaters                        OK
mythconverg.music_albumart                         OK
mythconverg.music_albums                           OK
mythconverg.music_artists                          OK
mythconverg.music_directories                      OK
mythconverg.music_genres                           OK
mythconverg.music_playlists                        OK
mythconverg.music_radios                           OK
mythconverg.music_smartplaylist_categories         OK
mythconverg.music_smartplaylist_items              OK
mythconverg.music_smartplaylists                   OK
mythconverg.music_songs                            OK
mythconverg.music_stats                            OK
mythconverg.mythlog                                OK
mythconverg.mythweb_sessions                       OK
mythconverg.networkiconmap                         OK
mythconverg.newssites                              OK
mythconverg.oldfind                                OK
mythconverg.oldprogram                             OK
mythconverg.oldrecorded                            OK
mythconverg.people                                 OK
mythconverg.phonecallhistory                       OK
mythconverg.phonedirectory                         OK
mythconverg.pidcache                               OK
mythconverg.playgroup                              OK
mythconverg.powerpriority                          OK
mythconverg.profilegroups                          OK
mythconverg.program                                OK
mythconverg.programgenres                          OK
mythconverg.programrating                          OK
mythconverg.recgrouppassword                       OK
mythconverg.record                                 OK
mythconverg.record_tmp                             OK
mythconverg.recorded                               OK
mythconverg.recordedartwork                        OK
mythconverg.recordedcredits                        OK
mythconverg.recordedfile                           OK
mythconverg.recordedmarkup                         OK
mythconverg.recordedprogram                        OK
mythconverg.recordedrating                         OK
mythconverg.recordedseek                           OK
mythconverg.recordfilter                           OK
mythconverg.recordingprofiles                      OK
mythconverg.recordmatch                            OK
mythconverg.romdb                                  OK
mythconverg.scannerfile                            OK
mythconverg.scannerpath                            OK
mythconverg.schemalock                             OK
mythconverg.settings                               OK
mythconverg.storagegroup                           OK
mythconverg.tvchain                                OK
mythconverg.tvosdmenu                              OK
mythconverg.upnpmedia                              OK
mythconverg.videocast                              OK
mythconverg.videocategory                          OK
mythconverg.videocollection                        OK
mythconverg.videocountry                           OK
mythconverg.videogenre                             OK
mythconverg.videometadata                          OK
mythconverg.videometadatacast                      OK
mythconverg.videometadatacountry                   OK
mythconverg.videometadatagenre                     OK
mythconverg.videopart                              OK
mythconverg.videopathinfo                          OK
mythconverg.videosource                            OK
mythconverg.videotypes                             OK
mythconverg.weatherdatalayout                      OK
mythconverg.weatherscreens                         OK
mythconverg.weathersourcesettings                  OK
mythconverg.websites                               OK


```

There are a few warnings that some of the tables are marked as crashed and the last repair failed but the status is listed as OK. Is there anything else I can try to fix this? Thank you.

---

### Post by aelfric55 on 2016-06-08
msqlcheck seems to have repaired the three tables, after having reported they were crashed and the previous repair attempt on them (the "optimize" script) had failed. Run the command again and see whether the three tables are reported back simply as "OK" without any warning. If so, you're done --except you may or may not have to re-add the tuner cards one last time depending what was in the crashed tables to restore. 

If the tables are still crashed, the next attempt would be to try to repair each table individually. 
So:```
mysqlcheck -r  mythconverg  capturecard  -u mythtv -p
```to attempt to repair the capturecard table in mythconverg. And if it works, (i.e. reports back "mythconverg.capturecard   OK") the command would be run again, with "capturecard" replaced with the name of one of the other crashed tables.

If all this has failed, and you don't have a reasonably recent backup of the mythconverg database to just restore the whole darn thing, you can also try to rebuild the individual table by using the dump and restore method described briefly here: [https://dev.mysql.com/doc/refman/5.6/en/rebuilding-tables.html](https://dev.mysql.com/doc/refman/5.6/en/rebuilding-tables.html) 

But I've never had tables sufficiently hosed to need to try this method.

---

### Post by km782 on 2016-06-18
> **aelfric55 said:**
> msqlcheck seems to have repaired the three tables, after having reported they were crashed and the previous repair attempt on them (the "optimize" script) had failed. Run the command again and see whether the three tables are reported back simply as "OK" without any warning. If so, you're done --except you may or may not have to re-add the tuner cards one last time depending what was in the crashed tables to restore. 

If the tables are still crashed, the next attempt would be to try to repair each table individually. 
So:```
mysqlcheck -r  mythconverg  capturecard  -u mythtv -p
```to attempt to repair the capturecard table in mythconverg. And if it works, (i.e. reports back "mythconverg.capturecard   OK") the command would be run again, with "capturecard" replaced with the name of one of the other crashed tables.

If all this has failed, and you don't have a reasonably recent backup of the mythconverg database to just restore the whole darn thing, you can also try to rebuild the individual table by using the dump and restore method described briefly here: [https://dev.mysql.com/doc/refman/5.6/en/rebuilding-tables.html](https://dev.mysql.com/doc/refman/5.6/en/rebuilding-tables.html) 

But I've never had tables sufficiently hosed to need to try this method.

Thank you again for the help.  When I run mysqlcheck again I get an OK for everything.  Unfortunately within 24 hours the tables will have crashed again.  This time however, the capture cards still show up in the mythbackend setup.  They just don't work.  When I run mysqlcheck I will get the same error that 3 of the tables have crashed that I got previously.  

At this point I've lost my patience and decided to throw in the towel.  I restored the system with the backup I have from 9 months ago.  So far that seems to be working fine, other than losing some of my recordings.

---

