---
title: "Frontend Not Starting / Crashing during start up"
date: 2014-04-22
forum: Mythbuntu
---

### Post by griggs2 on 2014-04-22
Suddenly my frontend is suddenly not starting. <grumble> I'm having trouble figuring out why not - I get a brief flash of the theme like it's about to start - but then it crashes... Additionally it seems to take a very long time to get to that point - almost like something is timing out. I looked at the log file, and while I see some errors, I'm not sure which are critical (crucial) to the start up and what isn't - I don't want to chase around things that aren't germane to the current problem.

Any assistance would be greatly appreciated!

Below is a selection of log entries from the mythfrontend.log file for this evening - some are most likely duplicated.

```

Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-109-gcb744f8] www.mythtv.org
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 18:35:31 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-109-gcb744f8] www.mythtv.org
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 18:36:04 mythtvfe-lr mythfrontend.real: mythfrontend[2223]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-109-gcb744f8] www.mythtv.org
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 18:36:17 mythtvfe-lr mythfrontend.real: mythfrontend[2249]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-109-gcb744f8] www.mythtv.org
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 18:36:26 mythtvfe-lr mythfrontend.real: mythfrontend[2275]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-109-gcb744f8] www.mythtv.org
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 18:36:50 mythtvfe-lr mythfrontend.real: mythfrontend[2301]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 18:37:35 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N CoreContext mythcorecontext.cpp:1272 (InitLocale) Setting QT default locale to en_US
Apr 22 18:37:35 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythcorecontext.cpp:1305 (SaveLocaleDefaults) Current locale en_US
Apr 22 18:37:35 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 18:37:35 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 18:37:35 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 18:37:35 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 18:37:37 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 18:37:37 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 18:37:37 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 18:37:37 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 18:37:37 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythmainwindow.cpp:973 (Init) Using Frameless Window
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythmainwindow.cpp:986 (Init) Using Full Screen Window
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythmainwindow.cpp:1077 (Init) Using the Qt painter
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 18:37:38 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N CoreContext mythmainwindow.cpp:1906 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: N CoreContext mythmainwindow.cpp:1906 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 18:37:39 mythtvfe-lr mythfrontend.real: mythfrontend[2149]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnews
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-109-gcb744f8] www.mythtv.org
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 18:38:29 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 18:40:36 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext mythcorecontext.cpp:1272 (InitLocale) Setting QT default locale to en_US
Apr 22 18:40:36 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythcorecontext.cpp:1305 (SaveLocaleDefaults) Current locale en_US
Apr 22 18:40:36 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 18:40:36 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 18:40:36 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 18:40:36 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 18:40:37 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 18:40:37 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 18:40:37 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 18:40:37 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythmainwindow.cpp:973 (Init) Using Frameless Window
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythmainwindow.cpp:986 (Init) Using Full Screen Window
Apr 22 18:40:38 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythmainwindow.cpp:1077 (Init) Using the Qt painter
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext mythmainwindow.cpp:1906 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext mythmainwindow.cpp:1906 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnews
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythweather
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6546
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6546
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6546
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6546
Apr 22 18:40:39 mythtvfe-lr mythfrontend.real: mythfrontend[2144]: N CoreContext main.cpp:1059 (RunMenu) Found mainmenu.xml for theme 'MythCenter-wide'
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 19:38:07 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 19:38:36 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 19:40:13 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Apr 22 19:40:13 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Apr 22 19:40:13 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 19:40:13 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 19:40:13 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 19:40:13 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 19:40:15 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 19:40:15 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 19:40:15 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 19:40:15 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 19:40:16 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnews
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythweather
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6546
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6546
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6546
Apr 22 19:40:17 mythtvfe-lr mythfrontend.real: mythfrontend[1857]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6546
Apr 22 19:40:42 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Apr 22 19:40:42 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Apr 22 19:40:42 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 19:40:42 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 19:40:42 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 19:40:42 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 19:40:44 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 19:40:44 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 19:40:44 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 19:40:44 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 19:40:44 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 19:40:45 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 19:40:46 mythtvfe-lr mythfrontend.real: mythfrontend[2185]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 19:57:40 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 19:58:34 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 19:59:23 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 19:59:46 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Apr 22 19:59:46 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Apr 22 19:59:46 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 19:59:46 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 19:59:46 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 19:59:46 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
Apr 22 19:59:48 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 19:59:49 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnews
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythweather
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6546
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6546
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6546
Apr 22 19:59:50 mythtvfe-lr mythfrontend.real: mythfrontend[1904]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6546
Apr 22 20:00:41 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Apr 22 20:00:41 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Apr 22 20:00:41 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 20:00:41 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 20:00:41 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 20:00:41 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 20:00:42 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 20:00:42 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 20:00:42 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 20:00:42 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
Apr 22 20:00:43 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnews
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythweather
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6546
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6546
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6546
Apr 22 20:00:44 mythtvfe-lr mythfrontend.real: mythfrontend[2315]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6546
Apr 22 20:01:29 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Apr 22 20:01:29 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Apr 22 20:01:29 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 20:01:29 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 20:01:29 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 20:01:29 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 20:01:31 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 20:01:32 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 20:01:33 mythtvfe-lr mythfrontend.real: mythfrontend[2343]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 20:10:05 mythtvfe-lr mythfrontend.real: mythfrontend[2512]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythfrontend version: fixes/0.27 [v0.27-212-gb93fb14] www.mythtv.org
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtvfe-lr/.mythtv
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvfe-lr
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to 'mtvbe'
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I Logger logging.cpp:315 (run) Added logging to the console
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Apr 22 20:11:15 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 22 20:13:21 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Apr 22 20:13:21 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Apr 22 20:13:21 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 22 20:13:21 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 22 20:13:21 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Apr 22 20:13:21 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Apr 22 20:13:23 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
Apr 22 20:13:23 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6547
Apr 22 20:13:23 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
Apr 22 20:13:23 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6547
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythtvfe-lr/.mythtv/joystickmenurc
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.120:6948
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::201:2eff:fe4c:47f6%eth0]:6948
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 10.0.0.255:6948
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
Apr 22 20:13:24 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mytharchive
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering WebBrowser as a media playback plugin.
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythbrowser
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgallery
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythgame
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythmusic
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnetvision
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythnews
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythweather
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6546
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.0.0.120:6546
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6546
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::201:2eff:fe4c:47f6%eth0]:6546
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: N CoreContext main.cpp:1063 (RunMenu) Found mainmenu.xml for theme 'MythCenter-wide'
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Apr 22 20:13:25 mythtvfe-lr mythfrontend.real: mythfrontend[1916]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.

```

---

### Post by blm-ubunet on 2014-04-23
Mythbuntu wraps the actual FE program with auto-spawning nonsense that makes this confusing.

Use system monitor or terminal to kill mythfrontend & mythfrontend.real.

Launch frontend from terminal:
```
mythfrontend.real -v all --log-level=debug > FE-log.txt
```

Post the FE log file as attachment..

---

### Post by griggs2 on 2014-04-23
[[COLOR=#000000]blm-ubunet[/COLOR]]("http://ubuntuforums.org/member.php?u=1899844"): 

Thanks for your timely reply!

I went ahead and updated the backend this evening so that the FE and BE were in MythTV parity - Beforehand, I discovered that the BE had cacked and I had to wipe and reconfigure the CMOS - all sorts of bad juju goin on around here! ugh.

I just restarted the FrontEnd and it seems to be loading OK now... <puzzled> I'll run with this for a bit and see if things work ok, otherwise I'll revisit this thread, pull the startup logs and we can go thru them.

Thanks again for the help!

./g

---

