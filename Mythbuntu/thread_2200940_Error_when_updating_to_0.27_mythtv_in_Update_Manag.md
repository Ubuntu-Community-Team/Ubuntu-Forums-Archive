---
title: "Error when updating to 0.27 mythtv in Update Manager"
date: 2014-01-21
forum: Mythbuntu
---

### Post by mcapaldo on 2014-01-21
I ran the partial upgrade to install 0.26 and got this error from ujpdate manager.


installArchives() failed: Setting up mythtv-database (2:0.27.0+fixes.20140114.99f5464-0ubuntu0mythbuntu2) ... 
ERROR 1046 (3D000) at line 22: No database selected 
dpkg: error processing mythtv-database (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mythtv-backend-master: 
 mythtv-backend-master depends on mythtv-database; however: 
  Package mythtv-database is not configured yet. 
dpkg: error processing mythtv-backend-master (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 mythtv-database 
 mythtv-backend-master 
Error in function:  
Setting up mythtv-database (2:0.27.0+fixes.20140114.99f5464-0ubuntu0mythbuntu2) ... 
ERROR 1046 (3D000) at line 22: No database selected 
dpkg: error processing mythtv-database (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of mythtv-backend-master: 
 mythtv-backend-master depends on mythtv-database; however: 
  Package mythtv-database is not configured yet. 
dpkg: error processing mythtv-backend-master (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 mythtv-database 
 mythtv-backend-master 

now I can run backend setup and it works, sees all my tuners but front end can not eonnec t to it,  IP has not changed, did a reboot, let it update the schema and it looked like it was working until I tried to run frontend and it can not connect to backend 

I ran the following and get nothing at all, this is bad I think.

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][COLOR=#007777]xpath  -q -e 'string(//DBName)' /etc/mythtv/config.xml 2>/dev/null 
xpath  -q -e 'string(//DBUserName)' /etc/mythtv/config.xml 2>/dev/null 
xpath  -q -e 'string(//DBPassword)' /etc/mythtv/config.xml 2>/dev/null 
xpath  -q -e 'string(//DBHostName)' /etc/mythtv/config.xml 2>/dev/null [/COLOR][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by ibjsb4 on 2014-01-22
About partial upgrades

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by tgm4883 on 2014-01-22
> **mcapaldo said:**
> I ran the partial upgrade to install 0.26 and got this error from ujpdate manager.


installArchives() failed: Setting up mythtv-database (2:0.27.0+fixes.20140114.99f5464-0ubuntu0mythbuntu2) ... 
ERROR 1046 (3D000) at line 22: No database selected 
dpkg: error processing mythtv-database (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mythtv-backend-master: 
 mythtv-backend-master depends on mythtv-database; however: 
  Package mythtv-database is not configured yet. 
dpkg: error processing mythtv-backend-master (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 mythtv-database 
 mythtv-backend-master 
Error in function:  
Setting up mythtv-database (2:0.27.0+fixes.20140114.99f5464-0ubuntu0mythbuntu2) ... 
ERROR 1046 (3D000) at line 22: No database selected 
dpkg: error processing mythtv-database (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of mythtv-backend-master: 
 mythtv-backend-master depends on mythtv-database; however: 
  Package mythtv-database is not configured yet. 
dpkg: error processing mythtv-backend-master (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 mythtv-database 
 mythtv-backend-master 

now I can run backend setup and it works, sees all my tuners but front end can not eonnec t to it,  IP has not changed, did a reboot, let it update the schema and it looked like it was working until I tried to run frontend and it can not connect to backend 

I ran the following and get nothing at all, this is bad I think.

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][COLOR=#007777]xpath  -q -e 'string(//DBName)' /etc/mythtv/config.xml 2>/dev/null 
xpath  -q -e 'string(//DBUserName)' /etc/mythtv/config.xml 2>/dev/null 
xpath  -q -e 'string(//DBPassword)' /etc/mythtv/config.xml 2>/dev/null 
xpath  -q -e 'string(//DBHostName)' /etc/mythtv/config.xml 2>/dev/null [/COLOR][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

You don't have valid information in /etc/mythtv/config.xml. I'd check /etc/mythtv/mysql.txt and if it has valid data then configure config.xml properly.

---

### Post by mcapaldo on 2014-01-22
/etc/mythtv/config.xml neede to be filled in, but still can not get update to work, nor can front end see the backend.   and above 4 commands to talk to database still show nothing.

---

### Post by mcapaldo on 2014-01-22
mythtv backend log

Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: I CoreContext mythcontext.cpp:808 (UPnPautoconf) UPNP Search 2 secs
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 18:51:39 mythtvserver mythbackend: mythbackend[2716]: I CoreContext mythcontext.cpp:823 (UPnPautoconf) UPNP Search 1 secs
Jan 22 18:51:40 mythtvserver mythbackend: mythbackend[2716]: I CoreContext mythcontext.cpp:823 (UPnPautoconf) UPNP Search 1 secs
Jan 22 18:51:41 mythtvserver mythbackend: mythbackend[2716]: I CoreContext mythcontext.cpp:833 (UPnPautoconf) No UPnP backends found
Jan 22 18:51:41 mythtvserver mythbackend: mythbackend[2716]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I CoreContext mythcontext.cpp:808 (UPnPautoconf) UPNP Search 2 secs
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 18:51:42 mythtvserver mythbackend: mythbackend[2753]: I CoreContext mythcontext.cpp:823 (UPnPautoconf) UPNP Search 1 secs
Jan 22 18:51:43 mythtvserver mythbackend: mythbackend[2753]: I CoreContext mythcontext.cpp:823 (UPnPautoconf) UPNP Search 1 secs
Jan 22 18:51:44 mythtvserver mythbackend: mythbackend[2753]: I CoreContext mythcontext.cpp:833 (UPnPautoconf) No UPnP backends found
Jan 22 18:51:44 mythtvserver mythbackend: mythbackend[2753]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I CoreContext mythcontext.cpp:808 (UPnPautoconf) UPNP Search 2 secs
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 18:51:45 mythtvserver mythbackend: mythbackend[2765]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 18:51:46 mythtvserver mythbackend: mythbackend[2765]: I CoreContext mythcontext.cpp:823 (UPnPautoconf) UPNP Search 1 secs
Jan 22 18:51:46 mythtvserver mythbackend: mythbackend[2765]: I CoreContext mythcontext.cpp:823 (UPnPautoconf) UPNP Search 1 secs
Jan 22 18:51:48 mythtvserver mythbackend: mythbackend[2765]: I CoreContext mythcontext.cpp:833 (UPnPautoconf) No UPnP backends found
Jan 22 18:51:48 mythtvserver mythbackend: mythbackend[2765]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 18:57:57 mythtvserver mythbackend: mythbackend[3235]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 19:00:13 mythtvserver mythbackend: mythbackend[2835]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[2835]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[2835]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'mythserver' (110)
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[2835]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 19:02:20 mythtvserver mythbackend: mythbackend[3237]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3237]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3237]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'mythserver' (110)
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3237]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 19:04:26 mythtvserver mythbackend: mythbackend[3471]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 19:06:32 mythtvserver mythbackend: mythbackend[3471]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 19:06:32 mythtvserver mythbackend: mythbackend[3471]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'mythserver' (110)
Jan 22 19:06:32 mythtvserver mythbackend: mythbackend[3471]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 19:09:15 mythtvserver mythbackend: mythbackend[3772]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3772]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3772]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'mythserver' (110)
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3772]: C CoreContext main.cpp:116 (main) Failed to init MythContext.
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-134-g5a5e1cd] [www.mythtv.org](www.mythtv.org)
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I Logger logging.cpp:315 (run) Added logging to the console
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I CoreContext mythcorecontext.cpp:249 (Init) Assumed character encoding: en_US.UTF-8
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtvserver
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Jan 22 19:11:21 mythtvserver mythbackend: mythbackend[3916]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging

Mythtv frontend log

Jan 22 19:09:25 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800c960:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:25 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800c960:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: I CoreContext mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(15b6240:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: E CoreContext mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800c960:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:26 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800be70:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: N CoreContext mythmainwindow.cpp:2643 (PauseIdleTimer) Resuming idle timer
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: N CoreContext mythmainwindow.cpp:2643 (PauseIdleTimer) Resuming idle timer
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: I CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mythtvserver'
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: I CoreContext AirPlay/mythraopdevice.cpp:71 (Cleanup) RAOP Device: Cleaning up.
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: I CoreContext AirPlay/mythairplayserver.cpp:376 (Cleanup) AirPlay: Cleaning up.
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: I thread_unknown bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_airplay._tcp.' on 'MythTV on mythtvserver'
Jan 22 19:09:27 mythtvserver mythfrontend.real: mythfrontend[3790]: I CoreContext main.cpp:258 (cleanup) Shutting down UPnP client...
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800c030:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2bc01ff90:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800fc60:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2ac00bce0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b000d680:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2ac00bad0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b0002d70:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2ac00f790:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b0018a00:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2ac0111a0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b0019840:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2ac017a70:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b00193b0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2bc020150:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2b800c370:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I SendMessage mythcorecontext.cpp:418 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E MythSocketThread(-1) mythsocket.cpp:661 (ConnectToHostReal) MythSocket(7fd2ac00f850:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: E SendMessage mythcorecontext.cpp:488 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jan 22 19:09:28 mythtvserver mythfrontend.real: mythfrontend[3790]: I CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.

---

### Post by mcapaldo on 2014-01-22
Well I found a type in /etc/mythtv/config.xml on the hostname line, mythtv is working again, will try update manager tomorrow to see what happens.

---

