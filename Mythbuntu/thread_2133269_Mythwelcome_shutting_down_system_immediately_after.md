---
title: "Mythwelcome shutting down system immediately after boot?"
date: 2013-04-07
forum: Mythbuntu
---

### Post by tez1982 on 2013-04-07
Problem:

As soon as system boots the system starts shutdown process - no time to hit start frontend.

System:
AMD Phenom 2 3ghz
8gb Ram
500gb Primary HDD
2tb Secondary HDD
Mythbuntu 12.04 
Mythtv 0.26

My system has been using ACPI wakeup and shutdown for a long time with no problems, but as soon as I installed the 2tb hard drive this week problems have started. Now the system shutsdown before I have a chance to do anything (including get logs!).

The couple of things I have noticed that may be a clue?
I am now getting the mmio address already in use error on boot, which I never got before?
The shutdown doesn't appear to be "clean" as the boot option menu pops up when I boot now?

I'll keep trying to get the logs, any help would really be appreciated!

Thanks

---

### Post by tez1982 on 2013-04-07
Okay managed to get into the the system, as it was booting I managed to call the backend-setup - which seemed to stop it from shutting down. I then alt-tabbed to mythwelcome and manually locked the shutdown - now it is fine

Mythshutdown.log
```

Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 19:06:58 mediacentre mythlogserver: mythshutdown[2267]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 19:06:59 mediacentre mythlogserver: mythshutdown[2267]: N CoreContext main.cpp:342 (getStatus) Setup is running...
Apr  7 19:06:59 mediacentre mythlogserver: mythshutdown[2267]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 255
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB

Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I Logger logging.cpp:487 (launchLogServer) Starting mythlogserver
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: N CoreContext main.cpp:342 (getStatus) Setup is running...
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2290]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 255
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler

Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:07:00 mediacentre mythlogserver: mythshutdown[2380]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:07:01 mediacentre mythlogserver: mythshutdown[2380]: N CoreContext main.cpp:342 (getStatus) Setup is running...
Apr  7 20:07:01 mediacentre mythlogserver: mythshutdown[2380]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 255
Apr  7 20:07:30 mediacentre mythlogserver: mythshutdown[2742]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
.............................................
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:13:21 mediacentre mythlogserver: mythshutdown[4390]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:13:51 mediacentre mythlogserver: mythshutdown[4416]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:14:20 mediacentre mythlogserver: mythshutdown[4545]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:14:21 mediacentre mythlogserver: mythshutdown[4570]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:14:51 mediacentre mythlogserver: mythshutdown[4594]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:15:21 mediacentre mythlogserver: mythshutdown[4748]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:15:51 mediacentre mythlogserver: mythshutdown[4772]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4901]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:16:21 mediacentre mythlogserver: mythshutdown[4925]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:16:22 mediacentre mythlogserver: mythshutdown[4925]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:16:51 mediacentre mythlogserver: mythshutdown[4951]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:16:51 mediacentre mythlogserver: mythshutdown[4951]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:16:51 mediacentre mythlogserver: mythshutdown[4951]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:16:51 mediacentre mythlogserver: mythshutdown[4951]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:16:51 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//l$
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I CoreContext main.cpp:234 (getStatus) Mythshutdown: --status
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: N CoreContext main.cpp:264 (getStatus) Shutdown is locked
Apr  7 20:16:52 mediacentre mythlogserver: mythshutdown[4951]: I CoreContext main.cpp:347 (getStatus) Mythshutdown: --status returned: 16
Apr  7 20:17:21 mediacentre mythlogserver: mythshutdown[5109]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythshutdown version: fixes/0.26 [v0.$
Apr  7 20:17:21 mediacentre mythlogserver: mythshutdown[5109]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: $
Apr  7 20:17:21 mediacentre mythlogserver: mythshutdown[5109]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:17:21 mediacentre mythlogserver: mythshutdown[5109]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:17:21 mediacentre mythlogserver: mythshutdown[5109]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler

```

Mythbackend.log
```

Apr  7 19:06:52 mediacentre mythlogserver: mythbackend[1691]: N CoreContext main_helpers.cpp:575 (run_backend) MythBackend: Starting up as the master server.
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext programinfo.cpp:2062 (CheckProgramIDAuthorities) Found 3 distinct programid authorities
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6544
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.1.102:6544
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6544
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::beae:c5ff:fe5c:a8b7%eth0]:6544
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext main_helpers.cpp:645 (run_backend) Main::Registering HttpStatus Extension
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6543
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.1.102:6543
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6543
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::beae:c5ff:fe5c:a8b7%eth0]:6543
Apr  7 19:06:55 mediacentre mythlogserver: mythbackend[1691]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w$
Apr  7 19:06:56 mediacentre mythlogserver: mythbackend[1691]: I CoreContext bonjourregister.cpp:100 (BonjourCallback) Bonjour: Service registration complete: name 'Myt$
Apr  7 19:06:57 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 19:06:57 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 0)
Apr  7 19:06:57 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 19:06:57 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)
Apr  7 19:06:58 mediacentre mythlogserver: mythbackend[1691]: I Scheduler scheduler.cpp:2130 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Apr  7 19:06:58 mediacentre mythlogserver: mythbackend[1691]: I Scheduler scheduler.cpp:2243 (HandleReschedule) Scheduled 120 items in 0.7 = 0.49 match + 0.06 check + $
Apr  7 19:06:58 mediacentre mythlogserver: mythbackend[1691]: I Scheduler scheduler.cpp:2310 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 273 MB for 1007 at 2013-04-02T22:24:00Z => "Fam$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 653 MB for 1007 at 2013-04-02T22:33:00Z => "Fam$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1007_20130402222400.mpg): GetPlaybackURL:$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlayback$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1007_20130402223300.mpg): GetPlaybackURL:$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlayback$
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 0)
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:07:00 mediacentre mythlogserver: mythbackend[1691]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)
Apr  7 20:07:19 mediacentre mythlogserver: mythbackend[1691]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID 1, UID 0, Value 0x00$
Apr  7 20:07:19 mediacentre mythlogserver: mythbackend[1691]: N CoreContext main_helpers.cpp:683 (run_backend) MythBackend exiting
Apr  7 20:07:19 mediacentre mythlogserver: mythbackend[1691]: I CoreContext bonjourregister.cpp:26 (~BonjourRegister) Bonjour: De-registering service '_mythbackend-mas$
Apr  7 20:07:21 mediacentre mythlogserver: mythbackend[1691]: I CoreContext mythcontext.cpp:1169 (~MythContext) Waiting for threads to exit.
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythbackend version: fixes/0.26 [v0.26$
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4$
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//lo$
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1307
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I CoreContext mythtranslation.cpp:65 (load) Loading en_gb translation for module mythfrontend
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: N CoreContext main_helpers.cpp:575 (run_backend) MythBackend: Starting up as the master server.
Apr  7 20:08:13 mediacentre mythlogserver: mythbackend[3075]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 20:08:15 mediacentre mythlogserver: mythbackend[3075]: I CoreContext programinfo.cpp:2062 (CheckProgramIDAuthorities) Found 3 distinct programid authorities
Apr  7 20:08:15 mediacentre mythlogserver: mythbackend[3075]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Apr  7 20:08:15 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6544
Apr  7 20:08:15 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.1.102:6544
Apr  7 20:08:15 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6544
Apr  7 20:08:15 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::beae:c5ff:fe5c:a8b7%eth0]:6544
Apr  7 20:08:16 mediacentre mythlogserver: mythbackend[3075]: I CoreContext main_helpers.cpp:645 (run_backend) Main::Registering HttpStatus Extension
Apr  7 20:08:16 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6543
Apr  7 20:08:16 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.1.102:6543
Apr  7 20:08:16 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6543
Apr  7 20:08:16 mediacentre mythlogserver: mythbackend[3075]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::beae:c5ff:fe5c:a8b7%eth0]:6543
Apr  7 20:08:16 mediacentre mythlogserver: mythbackend[3075]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w$
Apr  7 20:08:17 mediacentre mythlogserver: mythbackend[3075]: I CoreContext bonjourregister.cpp:100 (BonjourCallback) Bonjour: Service registration complete: name 'Myt$
Apr  7 20:08:18 mediacentre mythlogserver: mythbackend[3075]: I Scheduler scheduler.cpp:2130 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Apr  7 20:08:18 mediacentre mythlogserver: mythbackend[3075]: I Scheduler scheduler.cpp:2243 (HandleReschedule) Scheduled 120 items in 0.3 = 0.06 match + 0.06 check + $
Apr  7 20:08:18 mediacentre mythlogserver: mythbackend[3075]: I Scheduler scheduler.cpp:2310 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Apr  7 20:08:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:08:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)
Apr  7 20:08:25 mediacentre mythlogserver: mythbackend[3075]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 0)
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:09:18 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq$
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 273 MB for 1007 at 2013-04-02T22:24:00Z => "Fam$
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 653 MB for 1007 at 2013-04-02T22:33:00Z => "Fam$
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1007_20130402222400.mpg): GetPlaybackURL:$
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlayback$
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1007_20130402223300.mpg): GetPlaybackURL:$
Apr  7 20:09:34 mediacentre mythlogserver: mythbackend[3075]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlayback$
Apr  7 20:11:19 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:11:19 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 0)
Apr  7 20:11:19 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:11:19 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)
Apr  7 20:13:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:13:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 0)
Apr  7 20:13:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:13:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)
Apr  7 20:13:31 mediacentre mythlogserver: mythbackend[3075]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Apr  7 20:15:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:15:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 0)
Apr  7 20:15:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Apr  7 20:15:20 mediacentre mythlogserver: mythbackend[3075]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mediacentre as a client (events: 1)

```

Mythwelcome.log
```

Apr  7 18:58:33 mediacentre mythlogserver: mythwelcome[1799]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 18:58:33 mediacentre mythlogserver: mythwelcome[1799]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 19:58:34 mediacentre mythlogserver: mythwelcome[1799]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 19:58:34 mediacentre mythlogserver: mythwelcome[1799]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 19:58:34 mediacentre mythlogserver: mythwelcome[1799]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythwelcome version: fixes/0.26 [v0.26$
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4$
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I Logger logging.cpp:306 (run) Added logging to the console
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/media/.mythtv
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of mediacentre
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//lo$
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr  7 19:06:56 mediacentre mythlogserver: mythwelcome[1811]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support $
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythtranslation.cpp:65 (load) Loading en_gb translation for module mythfrontend
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno:$
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/media/.my$
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 192.168.1.102:6948
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [::1]:6948
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [fe80::beae:c5ff:fe5c:a8b7%eth0]:6948
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 192.168.1.255:6948
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:954 (Init) Using Frameless Window
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:967 (Init) Using Full Screen Window
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:1058 (Init) Using the Qt painter
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Apr  7 19:06:57 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 19:06:58 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 19:06:58 mediacentre mythlogserver: mythwelcome[1811]: N CoreContext welcomedialog.cpp:135 (checkAutoStart) mythshutdown --startup returned: 1
Apr  7 19:06:58 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:06:59 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:06:59 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:06:59 mediacentre mythlogserver: mythwelcome[1811]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event
Apr  7 20:06:59 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:00 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:00 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:00 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:01 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 1
Apr  7 20:07:01 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:22 mediacentre mythlogserver: mythwelcome[1811]: N Socket mythcorecontext.cpp:1134 (connectionClosed) Event socket closed.  No connection to the backend.
Apr  7 20:07:30 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:07:30 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:07:30 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:31 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:35 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:07:35 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:07:35 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:36 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:40 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:07:40 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:07:40 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:41 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:45 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:07:45 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:07:45 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:46 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:50 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:07:50 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:07:50 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:51 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:07:55 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:07:55 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:07:55 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:07:56 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:00 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:08:00 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:08:00 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:01 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:05 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:08:05 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:08:05 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:06 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:10 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:08:10 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:08:10 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:11 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:15 mediacentre mythlogserver: mythwelcome[1811]: E CoreContext mythcorecontext.cpp:445 (ConnectCommandSocket) Connection to master server timed out.#012#0$
Apr  7 20:08:15 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:16 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:20 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend serve$
Apr  7 20:08:20 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Apr  7 20:08:20 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:21 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:22 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:22 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:28 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:29 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:30 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:30 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:31 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:31 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:08:51 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:08:52 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:09:21 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:09:22 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices
Apr  7 20:09:51 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2553 (LockInputDevices) Locking input devices
Apr  7 20:09:52 mediacentre mythlogserver: mythwelcome[1811]: I CoreContext mythmainwindow.cpp:2555 (LockInputDevices) Unlocking input devices

```

---

### Post by tez1982 on 2013-04-07
oh and here is my fstab - only thing I remember changing before all the problems started

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=15e12c46-6e77-40e4-a0cd-082074da7a44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eadf2f34-e0d1-4e1b-a63a-36032b904406 none            swap    sw              0       0
# 2nd drive
UUID=c1c443db-4ef7-4554-a7f7-4032105c4f62 /var/lib/mythtv/recordings2 ext4 defaults 0 2


```

---

