---
title: "No UPnP backends found"
date: 2010-06-02
forum: Mythbuntu
---

### Post by sinkyboy2000 on 2010-06-02
I'm using Mythbuntu 9.10 on an Acer Revo as a Frontend/backend.  All has been working well for a few months.  Tonight it crashed.  When I tried to launch the frontend I got the language selection screen and then the error msg in the thread title. 

I'm a real noob and don't really know where to start.  The frontend log has the following entries since the crash.  Can some kind soul help get my digital life back on track?

```
2010-06-02 20:46:48.278 NVP(3): Prebuffer wait timed out 920 times.
2010-06-02 20:46:48.278 NVP(3), Error: Timed out waiting for prebuffering too long. Exiting..
2010-06-02 20:46:48.279 NVP(3), Error: Video frame buffering failed too many times.
2010-06-02 20:46:48.288 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:48.389 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:48.489 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:48.589 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:48.690 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:48.790 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:48.907 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:49.007 NVP(3), Warning: Waited too long for decoder to pause
2010-06-02 20:46:49.107 NVP(3), Warning: Waited too long for decoder to pause
Starting mythfrontend.real..
2010-06-02 20:47:51.739 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-06-02 20:47:51.740 Using runtime prefix = /usr
2010-06-02 20:47:51.740 Using configuration directory = /home/alan/.mythtv
2010-06-02 20:47:51.745 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-06-02 20:47:51.746 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-06-02 20:47:51.748 Empty LocalHostName.
2010-06-02 20:47:51.748 Using localhost value of Revo
2010-06-02 20:47:51.764 New DB connection, total: 1
2010-06-02 20:47:51.772 Unable to connect to database!
2010-06-02 20:47:51.818 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

SSDP::PerformSearch - did not write entire buffer.
2010-06-02 20:47:51.845 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
............................................................................
2010-06-02 20:47:53.962 UPnPautoconf() - No UPnP backends found
2010-06-02 20:47:53.962 No UPnP backends found
2010-06-02 20:47:54.156 Primary screen: 0.
2010-06-02 20:47:54.156 Using screen 0, 1360x768 at 0,0
2010-06-02 20:47:54.293 Using theme base resolution of 1280x720
2010-06-02 20:47:54.413 LIRC: Successfully initialized '/dev/lircd' using '/home/alan/.mythtv/lircrc' config
2010-06-02 20:47:54.432 JoystickMenuThread Error: ReadConfig(9) unrecognized or malformed line "is released" 
2010-06-02 20:47:54.432 JoystickMenuThread Error: ReadConfig(96) unrecognized or malformed line "axis 0 15000 20000]" 
2010-06-02 20:47:54.446 JoystickMenuThread: Initialization of /dev/input/js0 succeeded using config file /home/alan/.mythtv/joystickmenurc
2010-06-02 20:47:54.521 Using the Qt painter
2010-06-02 21:08:18.294 LIRC: GetCodes -- eof?
mythfrontend.real: Fatal IO error: client killed
Starting mythfrontend.real..
2010-06-02 22:21:38.675 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-06-02 22:21:38.676 Using runtime prefix = /usr
2010-06-02 22:21:38.676 Using configuration directory = /home/alan/.mythtv
2010-06-02 22:21:39.584 Empty LocalHostName.
2010-06-02 22:21:39.584 Using localhost value of Revo
2010-06-02 22:21:39.621 New DB connection, total: 1
2010-06-02 22:21:39.628 Unable to connect to database!
2010-06-02 22:21:39.628 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-06-02 22:21:41.887 UPnPautoconf() - No UPnP backends found
2010-06-02 22:21:41.887 No UPnP backends found
2010-06-02 22:21:41.893 Primary screen: 0.
2010-06-02 22:21:41.893 Using screen 0, 1360x768 at 0,0
2010-06-02 22:21:41.896 Using theme base resolution of 1280x720
2010-06-02 22:21:41.933 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: Connection refused (111)
2010-06-02 22:21:41.934 JoystickMenuThread Error: ReadConfig(9) unrecognized or malformed line "is released" 
2010-06-02 22:21:41.935 JoystickMenuThread Error: ReadConfig(96) unrecognized or malformed line "axis 0 15000 20000]" 
2010-06-02 22:21:41.949 JoystickMenuThread: Initialization of /dev/input/js0 succeeded using config file /home/alan/.mythtv/joystickmenurc
2010-06-02 22:21:41.978 Using the Qt painter
```

---

### Post by larsolav on 2010-06-03
This may be a long shot, but look in this thread:
[http://ubuntuforums.org/showthread.php?t=726680](http://ubuntuforums.org/showthread.php?t=726680)
I had the same problem a couple of years back. For me it turned out that I had stupidly filled up /dev/sda1. 
I have seen others getting the error message as well, but for other reasons...
Edit: Maybe also see if this link may help:
[http://ubuntuforums.org/showthread.php?t=1452792](http://ubuntuforums.org/showthread.php?t=1452792)

---

### Post by petatkinson on 2010-06-03
Sounds like a problem connecting with MySQL.Open the mysql.txt file and check the logon settings.Sounds like something changed there.It sorted my UPnP problem

---

### Post by sinkyboy2000 on 2010-06-11
> **larsolav said:**
> This may be a long shot, but look in this thread:
[http://ubuntuforums.org/showthread.php?t=726680](http://ubuntuforums.org/showthread.php?t=726680)
I had the same problem a couple of years back. For me it turned out that I had stupidly filled up /dev/sda1. 
I have seen others getting the error message as well, but for other reasons...
Edit: Maybe also see if this link may help:
[http://ubuntuforums.org/showthread.php?t=1452792](http://ubuntuforums.org/showthread.php?t=1452792)

Thanks.  I'd seen your post about sda1 filling up.  Wasn't the problem here.  Also tried the modified /etc/init/mythtv-backend.conf, to no avail.

My mythbackend.log is 

```
Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-06-11 23:32:25.174 Deleting UPnP client...
2010-06-11 23:32:25.643 Failed to init MythContext, exiting.
2010-06-11 23:32:36.109 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-06-11 23:32:36.166 Using runtime prefix = /usr
2010-06-11 23:32:36.211 Using configuration directory = /home/mythtv/.mythtv
2010-06-11 23:32:36.255 Empty LocalHostName.
2010-06-11 23:32:36.300 Using localhost value of Revo
2010-06-11 23:32:36.361 New DB connection, total: 1
2010-06-11 23:32:36.406 Unable to connect to database!
2010-06-11 23:32:36.456 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

...............................................................................
2010-06-11 23:32:39.017 UPnPautoconf() - No UPnP backends found
2010-06-11 23:32:39.078 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-06-11 23:32:39.346 Deleting UPnP client...
2010-06-11 23:32:39.798 Failed to init MythContext, exiting.
```

There aren't any recordings I'm worried about saving - I just want it working again.  Would uninstalling and reinstalling myth be something I should try.  If so, is there anything I should watch out for when doing that?

---

### Post by sinkyboy2000 on 2010-06-15
Shameless Bump!
 
Sorry about that, but I would really appreciate it if someone could help with this.  It took me a long time to work out how to set this up with my TV Card and lots of other little problems.  I was loving it until it crashed and now I've no idea what's wrong, let alone how to fix.
 
I would consider doing a re-install of the mythtv packages, but there seems to be lots of reports on the forums of problems of trying to do that.

---

### Post by andree_b on 2010-06-15
```

...
2010-06-02 22:21:39.628 Unable to connect to database!
2010-06-02 22:21:39.628 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
...
```

Looks like your database password  changed and mythtv cant access it anymore.

Maybe this thread can help you: 
[http://ubuntuforums.org/archive/index.php/t-580710.html](http://ubuntuforums.org/archive/index.php/t-580710.html)

---

### Post by bance on 2010-06-15
I've had similar problems before, I used this:-

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

hth.

steve

---

### Post by ultimbro on 2011-11-10
I solved this problem with these :

sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common

seems like after mythbuntu installation the database wasn't ceated or something like that.

---

