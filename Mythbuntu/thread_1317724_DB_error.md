---
title: "DB error"
date: 2009-11-07
forum: Mythbuntu
---

### Post by micah161 on 2009-11-07
Help!   I am trying to install Mythtv on a cobbled together system.  I have to use Ubuntu 8.10 because that is the last version that supports my ATI video card, but my TV tuner card is a Hauppauge 1600 so I needed to compile and install v4l-dvb (thanks to silverdulcet for helping me figure this out).

I installed the debian package and had the UPnP error so I thought I would go for the rc22 to see if it would fix my problem and have better support for the v4l tuner.   But I am having the same problems and it looks like I can't get Mythtv to talk to Mysql.  

I cant figure out why this isn't working:

[html]micah@macadamia:~$ mysql -h 192.168.2.100 -u mythtv -p
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.2.100' (111)
micah@macadamia:~$ mysql -h 127.0.0.1 -u mythtv -p
Enter password: 
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)
micah@macadamia:~$ mysql -h localhost -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)[/html]But I can get  into mysql with the root and ran the mc.sql script to grant all the permissions but still get error messages when I run myth-setup or mythtv (see below).   Can anyone tell me what is going on or what to try?  

Thanks!



[html]micah@macadamia:~$ mythtv
2009-11-06 23:23:39.135 Using runtime prefix = /usr
2009-11-06 23:23:39.164 XScreenSaver support enabled
2009-11-06 23:23:39.166 DPMS is active.
2009-11-06 23:23:39.167 Using localhost value of macadamia
................................................................................
2009-11-06 23:23:41.798 UPnPautoconf() - No UPnP backends found
2009-11-06 23:23:41.798 No UPnP backends found
2009-11-06 23:23:41.819 New DB connection, total: 1
2009-11-06 23:23:41.965 max_width: 1600 max_height: 1200
2009-11-06 23:23:41.969 Primary screen 0.
2009-11-06 23:23:41.969 Using screen 0, 1600x1200 at 0,0
2009-11-06 23:23:41.970 No theme dir: /home/micah/.mythtv/themes/blue
2009-11-06 23:23:41.972 Switching to square mode (blue)
2009-11-06 23:23:42.598 Using the Qt painter
2009-11-06 23:23:42.599 JoystickMenuClient Error: Joystick disabled - Failed to read /home/micah/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-11-06 23:23:42.601 lirc_init failed for mythtv, see preceding messages
2009-11-06 23:23:45.552 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2009-11-06 23:23:45.552 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2009-11-06 23:23:45.553 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2009-11-06 23:23:45.553 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2009-11-06 23:24:03.972 Writing settings file /home/micah/.mythtv/mysql.txt
2009-11-06 23:24:03.973 Closing DB connection named 'DBManager0'
2009-11-06 23:24:04.045 Testing network connectivity to 192.168.2.100
2009-11-06 23:24:04.076 Cannot connect to port 6543 on database host 192.168.2.100
2009-11-06 23:24:04.077 Cannot connect to port 6543 on database host 192.168.2.100
2009-11-06 23:24:04.369 Primary screen 0.
2009-11-06 23:24:04.370 Using screen 0, 1600x1200 at 0,0
2009-11-06 23:24:04.370 No theme dir: /home/micah/.mythtv/themes/blue
2009-11-06 23:24:04.372 Switching to square mode (blue)
2009-11-06 23:24:04.632 Using the Qt painter
2009-11-06 23:24:04.633 JoystickMenuClient Error: Joystick disabled - Failed to read /home/micah/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-11-06 23:24:04.634 lirc_init failed for mythtv, see preceding messages
2009-11-06 23:24:05.444 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2009-11-06 23:24:05.445 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2009-11-06 23:24:15.018 User cancelled database configuration
2009-11-06 23:24:15.084 Deleting UPnP client...
2009-11-06 23:24:16.268 Failed to init MythContext, exiting.[/html]

---

### Post by micah161 on 2009-11-07
Sorry if it is bad forum etiquette to bump your own post, but I'm really stuck.   If anybody has any guesses, suggestions or URLs to do some background reading, I'd really appreciate it.  Could it be a Qsql problem?  I'm not too familiar with the Qt development kit.

---

