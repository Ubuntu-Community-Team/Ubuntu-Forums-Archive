---
title: "Installed Ubuntu Updates - now Mythbackend won't run automatically"
date: 2013-07-31
forum: Mythbuntu
---

### Post by varneyb on 2013-07-31
I installed a host of ubuntu updates, and it seems to have messed something up on my server.

Initially, mysql was not running, but I've fixed that problem.

I have verified that I can log into mysql as the mythtv user using the password that I've always used.

I found that the config.xml and mysql.txt in /etc/mythtv were empty (0 bytes). I replaced those with backup copies.

On startup, myth backend fails. Any attempts to start it using "start mythtv-backend" also fail. Here are the last few lines of the log:

```

Jul 30 19:31:40 ZZTV mythbackend[3578]: E CoreContext mythdbcon.cpp:213 (OpenDatabase) Unable to connect to database!
Jul 30 19:31:40 ZZTV mythbackend[3578]: E CoreContext mythdbcon.cpp:214 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jul 30 19:31:42 ZZTV mythbackend[3578]: I CoreContext mythcontext.cpp:760 (UPnPautoconf) UPnPautoconf() - No UPnP backends found
Jul 30 19:31:42 ZZTV mythbackend[3578]: A CoreContext mythcontext.cpp:414 (FindDatabase) No UPnP backends found
Jul 30 19:31:42 ZZTV mythbackend[3578]: C CoreContext main.cpp:108 (main) Failed to init MythContext.

```

But when I run it from the command line as the mythtv user, it runs fine. Any ideas?

Thanks,

Bruce

---

### Post by j_spam2 on 2013-09-07
Ditto this part:

On startup, myth backend fails. Any attempts to start it using "start  mythtv-backend" also fail. Here are the last few lines of the log:

 	Code:
 	Jul 30 19:31:40 ZZTV mythbackend[3578]: E CoreContext mythdbcon.cpp:213 (OpenDatabase) Unable to connect to database!
Jul 30 19:31:40 ZZTV mythbackend[3578]: E CoreContext mythdbcon.cpp:214 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jul 30 19:31:42 ZZTV mythbackend[3578]: I CoreContext mythcontext.cpp:760 (UPnPautoconf) UPnPautoconf() - No UPnP backends found
Jul 30 19:31:42 ZZTV mythbackend[3578]: A CoreContext mythcontext.cpp:414 (FindDatabase) No UPnP backends found
Jul 30 19:31:42 ZZTV mythbackend[3578]: C CoreContext main.cpp:108 (main) Failed to init MythContext. 
But when I run it from the command line as the mythtv user, it runs fine. Any ideas?

hope somebody knows how to fix it. i am stumped at the moment.
thanks
J S

---

### Post by topcat5 on 2013-09-19
I had a similar problem causes by the fact that the command line options for both mythfrontend & mythbackend changed.  They dropped -nodblog and made the default not to do db logging.  Unfortunately if you changed the automated script(s) to add this, then after upgrade, the real mythfrontend/backend programs throw a return code and exit.   It was pretty easy to track down for the front end.  Unfortunately on the stock mythbuntu system I'm running, Upstart does not seem to recognize this error and reports the backend to be running, but there were never really any processes created for it.    

If this is your issue then removing that now defunct option will fix it.

---

### Post by tgm4883 on 2013-09-20
> **topcat5 said:**
> I had a similar problem causes by the fact that the command line options for both mythfrontend & mythbackend changed.  They dropped -nodblog and made the default not to do db logging.  Unfortunately if you changed the automated script(s) to add this, then after upgrade, the real mythfrontend/backend programs throw a return code and exit.   It was pretty easy to track down for the front end.  Unfortunately on the stock mythbuntu system I'm running, Upstart does not seem to recognize this error and reports the backend to be running, but there were never really any processes created for it.    

If this is your issue then removing that now defunct option will fix it.

Upstart isn't tracking it, because you are running a version of the upstart script that has a bug in it. You don't have the fix for it, precisely because you changed the upstart script (if you alter a file in /etc/, then we can't push an update to that file).

A working upstart file will look very similar to this (or this exactly)
[https://github.com/MythTV/packaging/blob/master/deb/debian/mythtv-backend.upstart](https://github.com/MythTV/packaging/blob/master/deb/debian/mythtv-backend.upstart)

---

### Post by topcat5 on 2013-09-29
> **tgm4883 said:**
>  (if you alter a file in /etc/, then we can't push an update to that file).Updates should not change ".conf" files.

---

