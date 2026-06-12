---
title: "help with new install frntend bck end"
date: 2010-09-12
forum: Mythbuntu
---

### Post by blkbx on 2010-09-12
I've been using mythtv for a little while now and thought that I'd try to make things a little quieter by moving the hard drives to a place far far away(yes under the stairs). I built the front end with a 8gig sd card and moved the 2x1 t drives with its loud psu under the stairs. Installation went ok with both boxes but I havn't been able to get the front end to connect to the backend, both will happily ping each other from the command line and any other pc on the local lan. When I first turn on the fe box I get a preferred language option. Then

 No upnp
Then

 Database config page 1/2 details are
hostname mythtv-backend
ping test on port 3306
db name mythconverge
user mythtv
passwrd xxxxx
next 

use custom indentifier for frontend preferance

finish

 error  
 Cannot find(ping) database host
 then again back to the db config page. And then back to the 'Cannot find(ping) database host' error.
 

 

 I think the errors on the backend are network one's and yes you guessed it, I'm finger and thumbs here too. My lan looks like this,  
 backend192.168.2.6 -->adsl modem router -->netgear router-->frontend192.168.2.8
 The reason for the second router is not enough eth ports. The modem/router only has 2eth ports and all up I need 7 eth ports. As I've said both fe/be can ping each other and the modem/router and other pc on the wired lan and also on the wifi.
If this is overly confusing and I'm sure it is please ask me for any specifics you need to help me.
here are log files
first is mysql error.log
100427 12:28:04 [Note] Plugin 'FEDERATED' is disabled.
InnoDB: The first specified data file ./ibdata1 did not exist:
InnoDB: a new database to be created!
100427 12:28:04  InnoDB: Setting file ./ibdata1 size to 10 MB
InnoDB: Database physically writes the file full: wait...
100427 12:28:04  InnoDB: Log file ./ib_logfile0 did not exist: new to be created
InnoDB: Setting log file ./ib_logfile0 size to 5 MB
InnoDB: Database physically writes the file full: wait...
100427 12:28:04  InnoDB: Log file ./ib_logfile1 did not exist: new to be created
InnoDB: Setting log file ./ib_logfile1 size to 5 MB
InnoDB: Database physically writes the file full: wait...
InnoDB: Doublewrite buffer not found: creating new
InnoDB: Doublewrite buffer created
InnoDB: Creating foreign key constraint system tables
InnoDB: Foreign key constraint system tables created
100427 12:28:05  InnoDB: Started; log sequence number 0 0
100427 12:28:05  InnoDB: Starting shutdown...
100427 12:28:06  InnoDB: Shutdown completed; log sequence number 0 44233
100427 12:28:06 [Note] Plugin 'FEDERATED' is disabled.
100427 12:28:06  InnoDB: Started; log sequence number 0 44233
ERROR: 1064  You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ALTER TABLE user ADD column Show_view_priv enum('N','Y') CHARACTER SET utf8 NOT ' at line 1
100427 12:28:06 [ERROR] Aborting

100427 12:28:06  InnoDB: Starting shutdown...
100427 12:28:07  InnoDB: Shutdown completed; log sequence number 0 44233
100427 12:28:07 [Note] /usr/sbin/mysqld: Shutdown complete

100427 12:28:07 [Note] Plugin 'FEDERATED' is disabled.
100427 12:28:07  InnoDB: Started; log sequence number 0 44233
100427 12:28:07  InnoDB: Starting shutdown...
100427 12:28:08  InnoDB: Shutdown completed; log sequence number 0 44233
100427 12:28:08 [Note] Plugin 'FEDERATED' is disabled.
100427 12:28:08  InnoDB: Started; log sequence number 0 44233
ERROR: 1050  Table 'plugin' already exists
100427 12:28:08 [ERROR] Aborting

100427 12:28:08  InnoDB: Starting shutdown...
100427 12:28:09  InnoDB: Shutdown completed; log sequence number 0 44233
100427 12:28:09 [Note] /usr/sbin/mysqld: Shutdown complete




this is mythtv.log
Starting mythfrontend.real..
2010-09-13 12:47:01.923 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-13 12:47:01.923 Using runtime prefix = /usr
2010-09-13 12:47:01.923 Using configuration directory = /home/tomas/.mythtv
2010-09-13 12:47:02.617 Empty LocalHostName.
2010-09-13 12:47:02.617 Using localhost value of mythtv-frontend
2010-09-13 12:47:02.618 Testing network connectivity to 'mythtv-backend'
................................................................................
2010-09-13 12:47:09.807 UPnPautoconf() - No UPnP backends found
2010-09-13 12:47:09.807 No UPnP backends found
2010-09-13 12:47:09.809 Primary screen: 0.
2010-09-13 12:47:09.809 Using screen 0, 1280x720 at 0,0
2010-09-13 12:47:09.809 Could not find theme:  - Switching to Terra
2010-09-13 12:47:09.810 Using theme base resolution of 1280x720
2010-09-13 12:47:09.816 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
2010-09-13 12:47:09.816 Desktop video mode: 0x0 0 Hz
2010-09-13 12:47:09.818 get_ip: Name or service not known
2010-09-13 12:47:09.818 LIRC, Error: Failed to parse IP address ''
2010-09-13 12:47:09.818 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2010-09-13 12:47:09.821 New DB connection, total: 1
2010-09-13 12:47:09.833 Using Frameless Window
2010-09-13 12:47:09.833 Using Full Screen Window
2010-09-13 12:47:09.835 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-09-13 12:54:58.450 Writing settings file /home/tomas/.mythtv/mysql.txt
2010-09-13 12:54:58.450 Closing DB connection named 'DBManager0'
2010-09-13 12:54:58.455 Testing network connectivity to 'mythtv-backend'
2010-09-13 12:55:04.973 Cannot find (ping) database host mythtv-backend on the network
2010-09-13 12:55:04.973 Cannot find (ping) database host mythtv-backend on the network
2010-09-13 12:55:04.974 Primary screen: 0.
2010-09-13 12:55:04.974 Using screen 0, 1280x720 at 0,0
2010-09-13 12:55:04.975 Using theme base resolution of 1280x720
2010-09-13 12:55:04.976 get_ip: Name or service not known
2010-09-13 12:55:04.976 LIRC, Error: Failed to parse IP address ''
2010-09-13 12:55:04.976 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2010-09-13 12:55:04.989 Using Frameless Window
2010-09-13 12:55:04.989 Using Full Screen Window
2010-09-13 12:55:04.991 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0

---

### Post by ian dobson on 2010-09-13
Hi,

Looks as if you have a problem with the SQL database 
```
ERROR: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ALTER TABLE user ADD column Show_view_priv enum('N','Y') CHARACTER SET utf8 NOT ' at line 1
100427 12:28:06 [ERROR] Aborting
```
Note quite sure what, maybe corruption.

Regards
Ian Dobson

---

### Post by blkbx on 2010-09-14
Thanks for the reply Ian,
I have been having alot of trouble with the back end box. So a reinstall there is on cards for that. Though maybe it is the box but when I boot from the mythbuntu lucid dvd I get dumped at the command line whether I try the install from the main menu or load the disc and try from the desktop. I don't actually get to the desktop but to the command line.
The good thing is I've been spending alot of time with mysql. Though it has me up til well after midnight.
I'll pull the drives from the iffy box and load mythbackend on them using another computer and see what happens from there.

---

### Post by blkbx on 2010-09-16
[I]l've tried to connect to mysql client and I got cannot connect to loa=cal MYSQL server through socket '/var/run/mysql/d/mysqld.sock (2)
Later I tried 
mysql -u mythtv -h 192.168.x.x -p mythconverg
enter password xxxxxxx
ERROR 2003 (HY000): can't connect to MSQL server on 192.xxx.x.x -p mythconverg 
Enter password: xxxxxxxx
ERROR 2003 (HY000): Can't connect  to MUSQL server on '192.xxx.x.x -p mythconverg
Please be awear that there has been a fine bottle of red wine drunk during the course of the evening. so I'm not in the byte sorry for my keyboard errors. you wait til friday.
All of these errors are on the clients side
Thanks, hope your having a glass of wine yourself
tgif

[/I]

---

