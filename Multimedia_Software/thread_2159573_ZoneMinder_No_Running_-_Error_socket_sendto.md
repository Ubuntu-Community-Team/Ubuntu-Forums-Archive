---
title: "ZoneMinder No Running - Error socket_sendto"
date: 2013-07-03
forum: Multimedia Software
---

### Post by bikeman4444 on 2013-07-03
Hello all,

Would like some help getting zoneminder up and running. I am getting an error with the debug turned on.  I can create a monitor but am not getting video from the camera in the monitor but, do get video when using xawtv.  

Current system:
Ubuntu 12.10
Zoneminder 1.25 installed using apt-get
BNC card with 4 inputs
xawtv: I can see my camera
zoneminder is running in Firefox, I am able to create a monitor without video.

**When I run with the debug on I look in this director /tmp/zm and see:**

srwxr-xr-x 1 www-data www-data    0 Jul  3 12:32 zmdc.sock
-rw-r--r-- 1 www-data www-data  376 Jul  3 12:32 zm_debug.log.03924
-rw-r--r-- 1 www-data www-data 3918 Jul  3 12:36 zm_debug.log.04012
-rw-r--r-- 1 www-data www-data 3918 Jul  3 14:11 zm_debug.log.04643
-rw-r--r-- 1 www-data www-data 8171 Jul  3 13:23 zm_debug.log.1650
-rw-r--r-- 1 www-data www-data 8361 Jul  3 14:15 zm_debug.log.1651
-rw-r--r-- 1 www-data www-data 9055 Jul  3 14:16 zm_debug.log.1654
-rw-r--r-- 1 www-data www-data 8518 Jul  3 14:15 zm_debug.log.1656
-rw-r--r-- 1 www-data www-data 8865 Jul  3 14:16 zm_debug.log.3408
-rw-r--r-- 1 www-data www-data 8865 Jul  3 14:16 zm_debug.log.3423
-rw-r--r-- 1 www-data www-data 8518 Jul  3 14:16 zm_debug.log.3424
-rw-r--r-- 1 www-data www-data 8171 Jul  3 14:14 zm_debug.log.3425
-rw-r--r-- 1 www-data www-data 8898 Jul  3 14:15 zm_debug.log.3600
-rw-r--r-- 1 www-data www-data 7824 Jul  3 14:12 zm_debug.log.3689
-rw-r--r-- 1 www-data www-data  694 Jul  3 14:15 zm_debug.log.4640
srwxr-xr-x 1 www-data www-data    0 Jul  3 12:12 zms-166625s.sock
drwxr-xr-x 3 www-data www-data 4096 Jul  3 14:11 zmswap-m3


**Looking in the log files I see many lines like this:**

07/03/13 14:11:41.710938 web_php[3600].ERR [socket_sendto( /tmp/zm/zms-726099s.s
ock ) failed: No such file or directory] at includes/functions.php line 2322


**Also I get less of these lines:**

7/03/13 14:12:46.899734 web_php[3689].DBG [LogOpts: level=DBG/DBG, screen=OFF, 
database=INF, logfile=DBG->/tmp/zm/zm_debug.log.3689, weblog=INF, syslog=INF] at
 includes/logger.php line 168


I believe that there is a problem accessing with the the socket_sendto call.  I tried to chmod 777 on /tmp/zm without success.  /tmp/zm has group and oner as: www-data

Any help will be appreciated!

Tom

---

### Post by tgalati4 on 2013-07-03
As I recall, you need to add 777 privileges to your video device, probably /dev/video0, video1, video2, etc.  Or add your username to group video, or both.

---

