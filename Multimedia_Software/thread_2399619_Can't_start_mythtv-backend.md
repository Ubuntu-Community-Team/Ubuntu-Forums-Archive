---
title: "Can't start mythtv-backend"
date: 2018-08-27
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2018-08-27
When I run the ssh -X mythtv.mylan.home mythtv-setup it loads for a second then goes straight to asking if I want to start the backend. Doesn't give me the configuration screen. 

I'm running a mythtv backend with a separate database server.

```
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.orgAug 27 23:34:24 failbox mythbackend: mythbackend[189]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:24 failbox mythbackend: mythbackend[189]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:25 failbox mythbackend: mythbackend[219]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:26 failbox mythbackend: mythbackend[219]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:27 failbox mythbackend: mythbackend[225]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:28 failbox mythbackend: mythbackend[231]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:29 failbox mythbackend: mythbackend[247]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:30 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:31 failbox mythbackend: mythbackend[253]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:32 failbox mythbackend: mythbackend[259]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:33 failbox mythbackend: mythbackend[265]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:34 failbox mythbackend: mythbackend[272]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:34:35 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:34:36 failbox mythbackend: mythbackend[279]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:20 failbox mythbackend: mythbackend[188]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:21 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:22 failbox mythbackend: mythbackend[219]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:23 failbox mythbackend: mythbackend[225]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:24 failbox mythbackend: mythbackend[231]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:25 failbox mythbackend: mythbackend[237]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:26 failbox mythbackend: mythbackend[243]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:27 failbox mythbackend: mythbackend[243]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:28 failbox mythbackend: mythbackend[249]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:29 failbox mythbackend: mythbackend[257]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:30 failbox mythbackend: mythbackend[263]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:44:31 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: E CoreContext main_helpers.cpp:563 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:44:32 failbox mythbackend: mythbackend[269]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
```

```
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handlerAug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/jason/.mythtv
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Aug 27 23:35:19 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcontext.cpp:809 (UPnPautoconf) UPNP Search 2 secs
Aug 27 23:35:20 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcontext.cpp:824 (UPnPautoconf) UPNP Search 1 secs
Aug 27 23:35:20 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcontext.cpp:824 (UPnPautoconf) UPNP Search 1 secs
Aug 27 23:35:21 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcontext.cpp:834 (UPnPautoconf) No UPnP backends found
Aug 27 23:35:21 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythuihelper.cpp:1048 (FindThemeDir) MythUIHelper: No theme dir: '/usr/share/mythtv/themes/Mythbuntu'
Aug 27 23:35:21 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythuihelper.cpp:1067 (FindThemeDir) MythUIHelper: No default theme dir: '/usr/share/mythtv/themes/Mythbuntu'
Aug 27 23:35:21 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythuihelper.cpp:1076 (FindThemeDir) MythUIHelper: Could not find theme: Mythbuntu - Switching to Terra
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 59.996 Hz
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.1.7:0
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::216:3eff:fe31:6d57%eth0]:0
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::2ff:22ff:fe32:653c%eth1]:0
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.1.255:0
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1920 x 1080
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Aug 27 23:35:22 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:35:23 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythdownloadmanager.cpp:1655 (load) MythCookieJar::load() failed to open file for reading: /home/jason/.mythtv/MythBrowser/cookiejar.txt
Aug 27 23:35:23 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Aug 27 23:35:23 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Aug 27 23:35:24 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en)
Aug 27 23:35:25 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.freedesktop.ScreenSaver was not provided by any .service files
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.freedesktop.PowerManagement.Inhibit was not provided by any .service files
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.mate.SessionManager was not provided by any .service files
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.gnome.SessionManager was not provided by any .service files
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythuihelper.cpp:1048 (FindThemeDir) MythUIHelper: No theme dir: '/usr/share/mythtv/themes/Mythbuntu'
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythuihelper.cpp:1067 (FindThemeDir) MythUIHelper: No default theme dir: '/usr/share/mythtv/themes/Mythbuntu'
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythuihelper.cpp:1076 (FindThemeDir) MythUIHelper: Could not find theme: Mythbuntu - Switching to Terra
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.1.7:0
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::216:3eff:fe31:6d57%eth0]:0
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::2ff:22ff:fe32:653c%eth1]:0
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.1.255:0
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1920 x 1080
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Aug 27 23:35:35 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Aug 27 23:35:36 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Aug 27 23:35:36 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext main.cpp:533 (main) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I Logger logging.cpp:313 (run) Added logging to the console
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/jason/.mythtv
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of failbox
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.freedesktop.ScreenSaver was not provided by any .service files
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.freedesktop.PowerManagement.Inhibit was not provided by any .service files
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.mate.SessionManager was not provided by any .service files
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.gnome.SessionManager was not provided by any .service files
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 59.996 Hz
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythuihelper.cpp:1048 (FindThemeDir) MythUIHelper: No theme dir: '/usr/share/mythtv/themes/Mythbuntu'
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: W CoreContext mythuihelper.cpp:1067 (FindThemeDir) MythUIHelper: No default theme dir: '/usr/share/mythtv/themes/Mythbuntu'
Aug 27 23:46:03 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext mythuihelper.cpp:1076 (FindThemeDir) MythUIHelper: Could not find theme: Mythbuntu - Switching to Terra
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: C CoreContext serverpool.cpp:269 (SelectDefaultListen) ServerPool: Host is configured to listen on 192.168.1.2, but address is not used on any local network interfaces.
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::216:3eff:fee2:a6d3%eth0]:0
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::2ff:22ff:fe32:653c%eth1]:0
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1920 x 1080
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Aug 27 23:46:04 failbox mythtv-setup.real: mythtv-setup[326]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Aug 27 23:46:05 failbox mythtv-setup.real: mythtv-setup[326]: E CoreContext main.cpp:533 (main) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
```

---

### Post by Tadaen_Sylvermane on 2018-08-27
I've added the mysql tz info to the database server.

---

### Post by Tadaen_Sylvermane on 2018-08-27
I found that the instructions I followed to add the tz data tables were not complete. Found the proper answer on the arch wiki. I am now fully functional.

---

