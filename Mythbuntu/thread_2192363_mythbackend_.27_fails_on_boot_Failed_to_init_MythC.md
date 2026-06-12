---
title: "mythbackend .27 fails on boot: Failed to init MythContext"
date: 2013-12-07
forum: Mythbuntu
---

### Post by ajaxmike on 2013-12-07
Fresh reinstall of 13.10 server and .27 mythtv.  mythtv setup is OK.  mythbackend fails to start on boot, but runs OK from command line with errors.    

Output from mythbackend log:

```

Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-115-gf785255] www.mythtv.org
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.4, runtime: 4.8.4
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_CA.UTF-8
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of homeserver
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'h192.168.1.10'
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I Logger logging.cpp:315 (run) Added logging to the console
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Dec  7 14:36:52 homeserver mythbackend: mythbackend[2465]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Dec  7 14:36:57 homeserver mythbackend: mythbackend[2465]: C CoreContext main.cpp:116 (main) Failed to init MythContext.


```

Output from command line:

```

michael@homeserver:~$ mythbackend
2013-12-07 14:42:28.292184 C  mythbackend version: fixes/0.27 [v0.27-115-gf785255] www.mythtv.org
2013-12-07 14:42:28.292203 C  Qt version: compile: 4.8.4, runtime: 4.8.4
2013-12-07 14:42:28.292206 N  Enabled verbose msgs:  general
2013-12-07 14:42:28.292218 N  Setting Log Level to LOG_INFO
2013-12-07 14:42:28.303047 I  Added logging to the console
2013-12-07 14:42:28.303592 I  Setup Interrupt handler
2013-12-07 14:42:28.303602 I  Setup Terminated handler
2013-12-07 14:42:28.303611 I  Setup Segmentation fault handler
2013-12-07 14:42:28.303618 I  Setup Aborted handler
2013-12-07 14:42:28.303626 I  Setup Bus error handler
2013-12-07 14:42:28.303635 I  Setup Floating point exception handler
2013-12-07 14:42:28.303643 I  Setup Illegal instruction handler
2013-12-07 14:42:28.303663 I  Setup Real-time signal 0 handler
2013-12-07 14:42:28.303726 N  Using runtime prefix = /usr
2013-12-07 14:42:28.303743 N  Using configuration directory = /home/michael/.mythtv
2013-12-07 14:42:28.303842 I  Assumed character encoding: 
2013-12-07 14:42:28.303858 W  This application expects to be running a locale that specifies a UTF-8 codeset, and many features may behave improperly with your current language settings. Please set the LC_ALL or LC_CTYPE, and LANG variable(s) in the environment in which this program is executed to include a UTF-8 codeset (such as 'en_US.UTF-8').
2013-12-07 14:42:28.304311 I  Using localhost value of homeserver
2013-12-07 14:42:28.319231 N  Setting QT default locale to en_US
2013-12-07 14:42:28.319311 I  Current locale en_US
2013-12-07 14:42:28.319355 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2013-12-07 14:42:28.323940 I  Current MythTV Schema Version (DBSchemaVer): 1317
2013-12-07 14:42:28.324379 I  Loading en_us translation for module mythfrontend
2013-12-07 14:42:28.324675 N  MythBackend: Starting up as the master server.
2013-12-07 14:42:28.407959 I  New Client:  (#1)
2013-12-07 14:42:28.423987 I  Found 1 distinct programid authorities
2013-12-07 14:42:28.424253 I  New static DB connectionSchedCon
2013-12-07 14:42:28.424327 I  Registering HouseKeeperTask 'LogClean'.
2013-12-07 14:42:28.424358 I  Registering HouseKeeperTask 'DBCleanup'.
2013-12-07 14:42:28.424383 I  Registering HouseKeeperTask 'ThemeUpdateNotifications'.
2013-12-07 14:42:28.424455 I  Registering HouseKeeperTask 'RecordedArtworkUpdate'.
2013-12-07 14:42:28.425403 I  Registering HouseKeeperTask 'MythFillDB'.
2013-12-07 14:42:28.425432 I  Registering HouseKeeperTask 'JobQueueRecover'.
2013-12-07 14:42:28.425450 I  Registering HouseKeeperTask 'HardwareProfiler'.
2013-12-07 14:42:28.426493 I  Starting HouseKeeper.
2013-12-07 14:42:28.429727 I  Listening on TCP 127.0.0.1:6544
2013-12-07 14:42:28.429796 I  Listening on TCP 192.168.1.10:6544
2013-12-07 14:42:28.429887 I  Listening on TCP [::1]:6544
2013-12-07 14:42:28.429974 I  Listening on TCP [fe80::21d:9ff:fe90:a92%eth0]:6544
2013-12-07 14:42:29.398879 I  Main::Registering HttpStatus Extension
2013-12-07 14:42:29.400180 I  Listening on TCP 127.0.0.1:6543
2013-12-07 14:42:29.400244 I  Listening on TCP 192.168.1.10:6543
2013-12-07 14:42:29.400333 I  Listening on TCP [::1]:6543
2013-12-07 14:42:29.400415 I  Listening on TCP [fe80::21d:9ff:fe90:a92%eth0]:6543
2013-12-07 14:42:29.401806 N  AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2013-12-07 14:42:29.599907 C  MainServer::HandleVersion - Client speaks protocol version 8 but we speak 77!
2013-12-07 14:42:30.343982 I  Bonjour: Service registration complete: name 'Mythbackend on homeserver' type '_mythbackend._tcp.' domain: 'local.'
2013-12-07 14:42:31.427625 I  Reschedule requested for MATCH 0 0 0 - SchedulerInit
2013-12-07 14:42:31.444063 I  Scheduled 0 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
2013-12-07 14:42:31.444527 I  Scheduler: Seem to be woken up by USER
2013-12-07 14:42:34.696424 C  MainServer::HandleVersion - Client speaks protocol version 8 but we speak 77!
2013-12-07 14:42:39.796303 C  MainServer::HandleVersion - Client speaks protocol version 8 but we speak 77!


```

Since it works after boot, it strikes me that some device isn't ready in time at boot.  I am using HD Homerun tuners.  How do I get it to run at boot?  I understand that the "Client speaks protocol version 8 but we speak 77!" is a known bug?

---

### Post by ajaxmike on 2013-12-09
IP address had a typo.  BE will not launch automatically with errors.  It would launch manually and I could run a local FE even without the correct IP, so that threw me off.

---

