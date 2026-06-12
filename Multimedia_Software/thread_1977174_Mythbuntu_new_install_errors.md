---
title: "Mythbuntu new install errors"
date: 2012-05-09
forum: Multimedia Software
---

### Post by speed32219 on 2012-05-09
using the latest Mythbuntu 12.04 lte release.  After configuring the backend when I try to start, it looks like it goes out and downloads the channels and epg date for the database (so it does see the new ceton tuner with m-card).  But when I try and start the backend I get errors.

I am at work, but when I get home late this evening I will post a section of the log, but the erros are telling me that many of the libs are not for the current relase of Mythbuntu.  I did an update, but still many errors in syslog stating the current version is not compatible with an older installed libs.  Anyone see anything similar?

As stated I will post a small section of the errors I see.

Here is part of the log from **mythbackend.log.**


May 10 00:04:46 Myth-Box mythbackend[1989]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 10 00:04:46 Myth-Box mythbackend[1989]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 10 00:04:46 Myth-Box mythbackend[1989]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 10 00:04:46 Myth-Box mythbackend[1989]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 10 00:04:46 Myth-Box mythbackend[1989]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 10 00:04:46 Myth-Box mythbackend[1989]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
May 10 00:04:46 Myth-Box mythbackend[1989]: C CoreContext mythcorecontext.cpp:195 (Init) **Application binary version (0.25.20120408-1) does not match libraries** (0.25.20120506-1)
May 10 00:04:46 Myth-Box mythbackend[1989]: W CoreContext mythcorecontext.cpp:201 (Init) **This application is not compatible** with the installed MythTV libraries. Please recompile after a make distclean
May 10 00:04:46 Myth-Box mythbackend[1989]: ! CoreContext mythcontext.cpp:1031 (MythContext) MythContext: Unable to allocate MythCoreContext
May 10 00:04:46 Myth-Box mythbackend[1989]: ! CoreContext mythcontext.cpp:1052 (Init) **Application binary version (0.25.20120408-1) does not match libraries** (0.25.20120506-1)
May 10 00:04:46 Myth-Box mythbackend[1989]: W CoreContext mythcontext.cpp:1062 (Init) This application is not compatible with the installed MythTV libraries.
May 10 00:04:46 Myth-Box mythbackend[1989]: C CoreContext main.cpp:108 (main) Failed to init MythContext.
May 10 00:04:46 Myth-Box mythbackend[2047]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25-82-g7fbcfb4] [www.mythtv.org](www.mythtv.org)
May 10 00:04:46 Myth-Box mythbackend[2047]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
May 10 00:04:46 Myth-Box mythbackend[2047]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
May 10 00:04:46 Myth-Box mythbackend[2047]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 10 00:04:46 Myth-Box mythbackend[2047]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 10 00:04:46 Myth-Box mythbackend[2047]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 10 00:04:46 Myth-Box mythbackend[2047]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 10 00:04:46 Myth-Box mythbackend[2047]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 10 00:04:46 Myth-Box mythbackend[2047]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 10 00:04:46 Myth-Box mythbackend[2047]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
May 10 00:04:46 Myth-Box mythbackend[2047]: C CoreContext mythcorecontext.cpp:195 (Init) Application binary version (0.25.20120408-1) does not match libraries (0.25.20120506-1)
May 10 00:04:46 Myth-Box mythbackend[2047]: W CoreContext mythcorecontext.cpp:201 (Init) **This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean**
May 10 00:04:46 Myth-Box mythbackend[2047]: ! CoreContext mythcontext.cpp:1031 (MythContext) MythContext: Unable to allocate MythCoreContext
May 10 00:04:46 Myth-Box mythbackend[2047]: ! CoreContext mythcontext.cpp:1052 (Init) Application binary version (0.25.20120408-1) does not match libraries (0.25.20120506-1)
May 10 00:04:46 Myth-Box mythbackend[2047]: W CoreContext mythcontext.cpp:1062 (Init) This application is not compatible with the installed MythTV libraries.
May 10 00:04:46 Myth-Box mythbackend[2047]: C CoreContext main.cpp:108 (main) Failed to init MythContext.

And part of the syslog:

May  9 01:33:49 Myth-Box kernel: [ 1190.365303] init: mythtv-backend respawning too fast, stopped
May  9 01:43:53 Myth-Box kernel: [   18.689130] init: mythtv-backend main process (1881) terminated with status 
1
May  9 01:43:53 Myth-Box kernel: [   18.689170] init: mythtv-backend main process ended, respawning
May  9 01:43:53 Myth-Box kernel: [   19.506602] init: mythtv-backend main process (2265) terminated with status 
1
May  9 01:43:53 Myth-Box kernel: [   19.506644] init: mythtv-backend main process ended, respawning
May  9 01:43:54 Myth-Box kernel: [   20.336671] init: mythtv-backend main process (2277) terminated with status 
1
May  9 01:43:54 Myth-Box kernel: [   20.336703] init: mythtv-backend respawning too fast, stopped
May  9 01:45:47 Myth-Box &#65279;AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'mythbrowser'), 
dbus.String(u'mythnetvision')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Sig
nature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signa
ture=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String
(u'')], signature=dbus.Signature('s'))
May  9 01:45:55 Myth-Box &#65279;AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'mythbrowser'), d
bus.String(u'mythnetvision')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbu
s.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signatu
re=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
May 10 00:04:46 Myth-Box kernel: [   16.830533] init: mythtv-backend main process (1962) terminated with status 
130
May 10 00:04:46 Myth-Box kernel: [   16.830565] init: mythtv-backend main process ended, respawning
May 10 00:04:46 Myth-Box kernel: [   17.131877] init: mythtv-backend main process (1987) terminated with status 
130
May 10 00:04:46 Myth-Box kernel: [   17.131909] init: mythtv-backend main process ended, respawning
May 10 00:04:46 Myth-Box kernel: [   17.460945] init: mythtv-backend main process (2045) terminated with status 
130
May 10 00:04:46 Myth-Box kernel: [   17.460990] init: mythtv-backend respawning too fast, stopped

I hope some of this helps someone able to point me in the right direction.  After a fresh installed mythbuntu, I was asked to update from the from within the mythbuntu manager, I usually select no, but this time I selected yes and it took a while for everything to update.

---

### Post by speed32219 on 2012-05-10
Posted the logs in the original post

---

### Post by speed32219 on 2012-05-12
Reloaded Mythbuntu and did NOT upgrade from the Ubuntu repos.  Just a basic install worked. I have enabled the upgrade from repo .25 version in the Mythbuntu control center to just keep up with MythTV changes/fixes to .25 release. DO not upgrade from the main Ubuntu repo from the control center.

I haven't double checked, but that is what I believe is where my problems  with packages not current with my release errors came from.

---

