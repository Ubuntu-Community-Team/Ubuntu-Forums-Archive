---
title: "Myth front end will not start"
date: 2010-09-26
forum: Multimedia Software
---

### Post by rx7haze on 2010-09-26
I have an htpc running mythbuntu 10.04 connected to a plasma tv via hdmi. Initially i was able to boot fine and the front end loaded ok but the resolution was off. My display is 1024x768 but my only options in myth was to use 1024x720. I have since enabled the proprietary ATI video driver. Now my desktop dispay perfect on the tv. However, i can no longer start the mythtv front end. I also ran an update that updated over 100 packages. I don't understand the log, the output is below. Can someone help me track down the problem? Thanks.

hayes@hayes-desktop:~$ mythfrontend
2010-09-26 11:49:15.447 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-26 11:49:15.447 Using runtime prefix = /usr
2010-09-26 11:49:15.447 Using configuration directory = /home/hayes/.mythtv
2010-09-26 11:49:16.139 Empty LocalHostName.
2010-09-26 11:49:16.139 Using localhost value of hayes-desktop
2010-09-26 11:49:16.150 New DB connection, total: 1
2010-09-26 11:49:16.158 Connected to database 'mythconverg' at host: localhost
2010-09-26 11:49:16.159 Closing DB connection named 'DBManager0'
2010-09-26 11:49:16.181 ScreenSaverX11Private: XScreenSaver support enabled
2010-09-26 11:49:16.182 DPMS is disabled.
2010-09-26 11:49:16.186 Primary screen: 0.
2010-09-26 11:49:16.187 Connected to database 'mythconverg' at host: localhost
2010-09-26 11:49:16.189 Using screen 0, 1280x720 at 0,0
2010-09-26 11:49:16.213 Desktop video mode: 1280x720 60.0024 Hz
2010-09-26 11:49:16.290 MythUI Image Cache size set to 20971520 bytes
2010-09-26 11:49:16.309 Enabled verbose msgs:  important general
2010-09-26 11:49:16.316 Primary screen: 0.
2010-09-26 11:49:16.316 Using screen 0, 1280x720 at 0,0
2010-09-26 11:49:16.317 Using theme base resolution of 1280x720
2010-09-26 11:49:16.319 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-09-26 11:49:16.320 JoystickMenuThread Error: Joystick disabled - Failed to read /home/hayes/.mythtv/joystickmenurc
2010-09-26 11:49:16.345 Using Frameless Window
2010-09-26 11:49:16.345 Using Full Screen Window
2010-09-26 11:49:16.401 Using the Qt painter
2010-09-26 11:49:16.457 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-26 11:49:16.462 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-26 11:49:16.467 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-26 11:49:16.467 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-26 11:49:16.474 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-26 11:49:17.009 Registering Internal as a media playback plugin.
2010-09-26 11:49:17.066 Cannot load language en_us for module mytharchive
2010-09-26 11:49:17.122 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.122 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.123 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.125 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.126 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.126 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.128 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.129 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.129 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.131 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.132 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.132 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.134 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.135 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.135 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-26 11:49:17.136 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-26 11:49:17.137 Cannot load language en_us for module mythgallery
2010-09-26 11:49:17.142 Cannot load language en_us for module mythmovies
2010-09-26 11:49:17.153 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-26 11:49:17.197 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-26 11:49:17.206 Cannot load language en_us for module mythmusic
2010-09-26 11:49:17.212 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-26 11:49:17.240 Cannot load language en_us for module mythvideo
2010-09-26 11:49:17.247 Cannot load language en_us for module mythweather
2010-09-26 11:49:17.250 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-26 11:49:17.283 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-09-26 11:49:17.285 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-26 11:49:17.629 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-09-26 11:49:17.630 Using protocol version 56
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault

---

### Post by jalapeno on 2010-11-11
Hi,

I seem to have the same problem. 

My system was working fine until I selected

in mythfrontend:
Utilities / Setup | Setup | General | Media Monitor
Ticked "Monitor CD/DVD (and other removable devices)"

Then mythfrontend started segfaulting. The end of my log looks like this:

```
2010-11-11 22:19:39.268 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-11-11 22:19:39.343 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-11 22:19:39.344 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-11 22:19:39.934 MythContext: Connecting to backend server: 192.168.1.10:6543 (try 1 of 1)
2010-11-11 22:19:39.935 Using protocol version 56
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault
ben@mythtv:~$
```

which appears to be pretty much the same as your log.

Of course, un-checking the option is a bit hard when you can't run mythfrontend. I used phpmyadmin to search for the option. It turns out that the option is:

In the database 'mythconverg'
In the table 'settings'
Has the value 'MonitorDrives'
I get the Segmentation Fault when data = 1, and I get proper operation when data = 0.

It can be changed using phpmyadmin, or using the command line program mysql (or probably lots of other ways too...)

Using mysql:
```

$ mysql mythconverg
mysql> select * from `settings` where `settings`.`value` = 'MonitorDrives';
+---------------+------+------------+
| value         | data | hostname   |
+---------------+------+------------+
| MonitorDrives | 0    | alpha      |
| MonitorDrives | 0    | beta       |
| MonitorDrives | 0    | gamma      |
| MonitorDrives | 1    | delta      |
| MonitorDrives | 0    | epsilon    |
+---------------+------+------------+
5 rows in set (0.00 sec)

mysql> 

```

So now to turn this thing off on the host 'delta' we do

```
mysql> UPDATE `mythconverg`.`settings` SET `data` = '0' WHERE `settings`.`value` = 'MonitorDrives' AND `settings`.`data` = '1' AND `settings`.`hostname` = 'delta' LIMIT 1 ;

```

If you just want to do it for all hosts in the database, then use this:
```
mysql> UPDATE `mythconverg`.`settings` SET `data` = '0' WHERE `settings`.`value` = 'MonitorDrives' AND `settings`.`data` = '1' ;

```

This got my mythfrontend to work again.

Ben.

---

