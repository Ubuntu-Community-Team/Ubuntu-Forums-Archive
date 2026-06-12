---
title: "mythbackend won't start"
date: 2014-10-16
forum: Mythbuntu
---

### Post by grygub on 2014-10-16
I installed mythtv via the mythbuntu-control-centre on top of 12.4. I eventually upgraded mythtv to .27 but the problem always existed. If I run mythbackend from a terminal everything seems fine and my frontend can connect. Otherwise even after running ```
sudo start mythtv-backend
``` the response of ```
sudo status mythtv-backend
mythtv-backend stop/waiting
``` I have tried fixing the mythtv user and password in mysql with the commands i found
```
set password for 'mythtv'@'%' = password('mythtv');
set password for 'mythtv'@'localhost' = password('mythtv');
connect mythconverg;
grant all privileges on *.* to 'mythtv'@'%' with grant option;
grant all privileges on *.* to 'mythtv'@'localhost' with grant option;
flush privileges;
exit;
```
I have tried some directions that think its a problem with the .mythtv directory
```
rm -rf /root/.mythtv
cp -a /home/mythtv/.mythtv /root
chown root:root -R /root/.mythtv
```

Can someone please help. I will post logs shortly

---

### Post by grygub on 2014-10-16
The end of the mythbackend log while I was using the start mythtv-backend command

```
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I Logger logging.cpp:308 (run) Added logging to the console
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of myth-server
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: C CoreContext main.cpp:129 (main) Failed to init MythContext.
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3099]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.3-181-ge1d575d] www.mythtv.org
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I Logger logging.cpp:308 (run) Added logging to the console
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of myth-server
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: C CoreContext main.cpp:129 (main) Failed to init MythContext.
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Oct 16 23:15:23 myth-server mythbackend: mythbackend[3114]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27.3-181-ge1d575d] www.mythtv.org
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: N thread_unknown logging.cpp:907 (logStart) Setting Log Level to LOG_INFO
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I Logger logging.cpp:308 (run) Added logging to the console
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I CoreContext mythcorecontext.cpp:257 (Init) Assumed character encoding: en_US.UTF-8
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of myth-server
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: C CoreContext main.cpp:129 (main) Failed to init MythContext.
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I LogForward loggingserver.cpp:1373 (forwardMessage) New Client:  (#1)
Oct 16 23:15:24 myth-server mythbackend: mythbackend[3126]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
```

I notice the line where it says unable to connect to mysql / access denied for mythtv@localhost but I do not know what else to try.

---

### Post by khPWXxF on 2014-10-17
The backend looks in /home/mythtv/.mythtv/config.xml for the database username and password.
The frontend looks in ~/.mythtv/config.xml
Do they match the username/password you are using?
Phil

---

### Post by grygub on 2014-10-17
Thank You, this worked. The backend config password was wrong.

---

