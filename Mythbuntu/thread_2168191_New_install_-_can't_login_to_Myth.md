---
title: "New install - can't login to Myth"
date: 2013-08-16
forum: Mythbuntu
---

### Post by mr_si on 2013-08-16
I've got Ub 13.04 (ona Core2 peecee), I've installed MythTV from the repositories and I can't login.

If I launch MythTVBackend from the GUI it asks me to add the current user to the mythtv group, then it asks for my password which it consistently rejects.

[nb there are three passwords a possibility here - my super user password, the mysql password and the mythtv account password, I've tried all three)

So I followed some instructions from help.ubuntu.com

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)


sudo usermod -a -G mythtv username

grep mythtv: /etc/group now shows mythtv:x:128:simon

and if I run mythbackend

simon@ubDesk:~$ mythbackend
2013-08-16 22:46:19.580883 C  mythbackend version: fixes/0.26 [v0.26.0-37-g340b5d4] [www.mythtv.org](www.mythtv.org)
2013-08-16 22:46:19.580908 C  Qt version: compile: 4.8.3, runtime: 4.8.4
2013-08-16 22:46:19.580913 N  Enabled verbose msgs:  general
2013-08-16 22:46:19.580931 N  Setting Log Level to LOG_INFO
2013-08-16 22:46:19.582146 I  Setup Interrupt handler
2013-08-16 22:46:19.582165 I  Setup Terminated handler
2013-08-16 22:46:19.582178 I  Setup Segmentation fault handler
2013-08-16 22:46:19.582193 I  Setup Aborted handler
2013-08-16 22:46:19.582206 I  Setup Bus error handler
2013-08-16 22:46:19.582245 I  Setup Floating point exception handler
2013-08-16 22:46:19.582260 I  Setup Illegal instruction handler
2013-08-16 22:46:19.582279 I  Setup Real-time signal 0 handler
2013-08-16 22:46:19.582345 N  Using runtime prefix = /usr
2013-08-16 22:46:19.582368 N  Using configuration directory = /home/simon/.mythtv
2013-08-16 22:46:19.582386 I  Added logging to the console
2013-08-16 22:46:19.582462 I  Assumed character encoding: en_GB.UTF-8
2013-08-16 22:46:19.582781 E  DBHostName is not set in config.xml
2013-08-16 22:46:19.582812 E  DBHostName is not set in config.xml
2013-08-16 22:46:19.582835 N  Empty LocalHostName.
2013-08-16 22:46:19.582847 I  Using localhost value of ubDesk
2013-08-16 22:46:19.594922 E  Unable to connect to database!
2013-08-16 22:46:19.594949 E  Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2013-08-16 22:46:19.594984 I  UPNP Search 2 secs
2013-08-16 22:46:19.811137 I  Starting mythlogserver
2013-08-16 22:46:19.811392 I  Starting process manager
2013-08-16 22:46:19.813196 I  Starting process signal handler
2013-08-16 22:46:19.813411 I  Starting IO manager (write)
2013-08-16 22:46:19.813787 I  Starting IO manager (read)
2013-08-16 22:46:19.913437 I  Added logging to mythlogserver at TCP:35327
2013-08-16 22:46:20.043564 I  UPNP Search 1 secs
2013-08-16 22:46:20.358192 I  UPNP Search 1 secs
2013-08-16 22:46:20.761460 I  UPNP Search 1 secs

No UPnP backends found

Would you like to configure the database connection now? [no]  2013-08-16 22:46:21.793255 I  No UPnP backends found

etc etc 

Thanks for looking

---

### Post by steeldriver on 2013-08-16
Try running

```
gksu-properties
```

from the command line, and making sure that 'Authentication mode' is set to 'sudo' (not 'su') - then try starting mythTVbackend again from the GUI

This seems to be a quirk of the gksu/gksudo setup in 13.04 (something to do with it being deprecated in favor of pkexec possibly)

---

### Post by mr_si on 2013-08-17
that's great thanks. 

I'm now on the next step of the mensa challenge that is mythtv... I'll let you know

---

