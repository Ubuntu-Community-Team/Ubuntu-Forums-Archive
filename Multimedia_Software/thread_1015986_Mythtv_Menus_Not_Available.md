---
title: "Mythtv Menus Not Available"
date: 2008-12-19
forum: Multimedia Software
---

### Post by dariusmartinez on 2008-12-19
Hello - bit of a noob here.  Have recently installed mythtv on ubuntu 8.10 and am having a few problems with the menu items (no menu at all, just a blue screen).  

Upon using mythtvfrontend I get:

2008-12-19 09:43:58.437 Using runtime prefix = /usr
2008-12-19 09:43:58.620 XScreenSaver support enabled
2008-12-19 09:43:58.621 DPMS is active.
2008-12-19 09:43:58.621 Empty LocalHostName.
2008-12-19 09:43:58.622 Using localhost value of Blackhat
2008-12-19 09:43:58.630 New DB connection, total: 1
2008-12-19 09:43:58.642 Unable to connect to database!
2008-12-19 09:43:58.642 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'darius'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-12-19 09:43:58.706 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2008-12-19 09:44:01.008 UPnPautoconf() - No UPnP backends found
2008-12-19 09:44:01.008 No UPnP backends found
2008-12-19 09:44:01.013 Primary screen 0.
2008-12-19 09:44:01.013 Using screen 0, 1280x1024 at 0,0
2008-12-19 09:44:01.013 No theme dir: /root/.mythtv/themes/blue
2008-12-19 09:44:01.014 Switching to square mode (blue)
2008-12-19 09:44:01.062 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-19 09:44:01.063 lirc_init failed for mythtv, see preceding messages
2008-12-19 09:44:01.067 JoystickMenuClient Error: Joystick disabled - Failed to read /root/.mythtv/joystickmenurc
2008-12-19 09:44:02.656 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-12-19 09:44:02.660 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-12-19 09:44:03.601 User cancelled database configuration
2008-12-19 09:44:03.654 Failed to init MythContext, exiting.

---

### Post by ironslave on 2008-12-27
you simply cannot connect to your Database... 

try this
[URL="https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting"]
https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting[/URL]

---

