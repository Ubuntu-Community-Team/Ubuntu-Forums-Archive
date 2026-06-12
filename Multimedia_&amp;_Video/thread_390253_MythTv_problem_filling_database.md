---
title: "MythTv problem filling database"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by zanyspydude on 2007-03-21
i've been following this guide:  [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

everything goes great until the
```
sudo /etc/cron.daily/mythtv-backend
```
step

I get this output:
```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open

```


i have phpmyadmin installed.  The mythtv setup went great.  The only thing i didn't know about was the MasterServer settings.  I left it at 127.0.0.1:6543 but when i launced mythfrontend it complained

here was the console output

```
david@david-desktop:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-03-21 18:50:58.847 Using runtime prefix = /usr
2007-03-21 18:50:58.859 Gnome-Screensaver support enabled
2007-03-21 18:50:58.863 DPMS is disabled.
2007-03-21 18:50:58.892 New DB connection, total: 1
2007-03-21 18:50:58.897 Connected to database 'mythconverg' at host: localhost
2007-03-21 18:50:58.900 Total desktop dim: 1680x1050, with 1 screen[s].
2007-03-21 18:50:58.903 Using screen 0, 1680x1050 at 0,0
2007-03-21 18:50:58.918 Current Schema Version: 1160
2007-03-21 18:50:58.918 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-03-21 18:50:58.919 Enabled verbose msgs:  important general
2007-03-21 18:50:59.250 Total desktop dim: 1680x1050, with 1 screen[s].
2007-03-21 18:50:59.252 Using screen 0, 1680x1050 at 0,0
2007-03-21 18:50:59.253 Switching to square mode (G.A.N.T.)
2007-03-21 18:50:59.273 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-03-21 18:50:59.633 Joystick disabled.
2007-03-21 18:51:00.287 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-03-21 18:51:00.502 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-03-21 18:51:00.597 Registering Internal as a media playback plugin.
2007-03-21 18:51:05.108 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-21 18:51:05.109 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

```

---

### Post by zanyspydude on 2007-03-21
if you have this problem change the password in /etc/mythtv/mysql.txt to be something non-ubnutu generated.

---

