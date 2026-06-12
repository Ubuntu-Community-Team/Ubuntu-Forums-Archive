---
title: "MythTV window disappearing after changing port number"
date: 2013-11-11
forum: Multimedia Software
---

### Post by scottbomb on 2013-11-11
Once again, MythTV has me pulling my hair out. I installed it fine on a computer in the bedroom. I'd like to be able to access it from a computer in another room so I installed it there as well. The IP address for the server is it's network address (192.168.1.6) and it's using port 6543. On the 2nd installation, MythTV apparently was already aware of the IP address it needed to connect to but it couldn't connect for some reason. I changed the port on the new frontend to match what the backend has for the server: 6543. Then, the window disappeared! I tried to re-open MythTV Frontend and nothing happens. I tried running mythtv-setup and and a shell opens, spills a list of log entried which don't seem to say much of anything, and it just stops. I have to kill the window to make it go away.

Does anyone know what's wrong or how to fix this?

FWIW: I did sudo apt-get remove --purge mythtv

I then rebooted and re-installed it and unfortunately, it's in the same status as before: nothing happens.

So I went into Synaptic and removed everything with the word "myth" in it, re-booted, re-installed, and got stuck with the same result: nothing.

---

### Post by scottbomb on 2013-11-12
Here's the log from this morning's attempt (from /var/log/mythtv/mythfrontend.log) in case there is anything in here that might be helpful:
```
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: C thread_unknown mythcommandlineparser.cpp:2594 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-1-g5b917e8] www.mythtv.org
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: C thread_unknown mythcommandlineparser.cpp:2596 (ConfigureLogging) Qt version: compile: 4.8.4, runtime: 4.8.4
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: N thread_unknown mythcommandlineparser.cpp:2598 (ConfigureLogging) Enabled verbose msgs:  general
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/scottbomb/.mythtv
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I Logger logging.cpp:315 (run) Added logging to the console
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of whitebox
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to '192.168.1.6'
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Nov 12 10:56:18 whitebox mythfrontend.real: mythfrontend[3079]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging

```

---

### Post by scottbomb on 2013-11-12
FWIW, there are 3 processes associated with myth that are running but not doing anything that I can see. I have to kill them:
```
user@linuxbox:/var/log/mythtv$ ps -A | grep myth 
 1805 ?        00:00:05 mythbackend
 3070 ?        00:00:00 mythfrontend
 3079 ?        00:00:04 mythfrontend.re
```

---

