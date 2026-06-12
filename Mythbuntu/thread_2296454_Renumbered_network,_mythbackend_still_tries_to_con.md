---
title: "Renumbered network, mythbackend still tries to connect to old IP"
date: 2015-09-25
forum: Mythbuntu
---

### Post by whosmatt on 2015-09-25
So, I've looked everywhere I can think to look.  I first tried running mythtv-setup and set my new IP there, then looked at my config files in ~/.mythtv.  Everything has the right IP (at least where I know to look) but looking at /var/etc/mythbackend.log I can see that it tries to connect to my old IP address.  Am I missing config somewhere?

Still actively troubleshooting, but if I'm missing something stupid, I'd love to know about it.

M

Edit:

I think it's making the database connection, but something else is up.  192.168.44.200 is the old IP.  Last few lines of the log file:

```
 Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of mythtv
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network connectivity to '192.168.44.200'
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Sep 25 19:23:16 mythtv mythbackend: mythbackend[3438]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Sep 25 19:23:26 mythtv mythbackend: mythbackend[3438]: C CoreContext main.cpp:116 (main) Failed to init MythContext.

```

---

### Post by whosmatt on 2015-09-25
And one more thing --- I don't get this if I run "mythbackend" in a shell.

---

### Post by whosmatt on 2015-09-25
Got it.  It was /home/mythtv/.mythtv/config.xml.  Dur.

---

