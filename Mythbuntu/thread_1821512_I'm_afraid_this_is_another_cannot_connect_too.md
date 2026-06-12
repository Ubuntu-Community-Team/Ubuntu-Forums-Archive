---
title: "I'm afraid this is another cannot connect too"
date: 2011-08-09
forum: Mythbuntu
---

### Post by blkbx on 2011-08-09
hi 
Yes the full error on the f/e gui is "Could not connectto master backend server. Is it running? Is the IP address set for it in mythtv-setup correct".
Here is the log

<code>Starting mythfrontend.real..
2011-08-09 22:56:24.912 mythfrontend version: fixes/0.24 [v0.24.1-61-gcccad82] [www.mythtv.org](www.mythtv.org)
2011-08-09 22:56:24.912 Using runtime prefix = /usr
2011-08-09 22:56:24.912 Using configuration directory = /home/tomas/.mythtv
2011-08-09 22:56:24.912 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-08-09 22:56:25.601 Empty LocalHostName.
2011-08-09 22:56:25.601 Using localhost value of myth-backend
2011-08-09 22:56:25.601 Testing network connectivity to '192.168.2.6'
2011-08-09 22:56:25.706 New DB connection, total: 1
2011-08-09 22:56:25.947 Connected to database 'mythconverg' at host: 192.168.2.6
2011-08-09 22:56:25.952 Closing DB connection named 'DBManager0'
2011-08-09 22:56:26.188 Connected to database 'mythconverg' at host: 192.168.2.6
2011-08-09 22:56:26.190 Current locale en_NZ
2011-08-09 22:56:26.190 No locale defaults file for en_NZ, skipping
2011-08-09 22:56:26.302 ScreenSaverX11Private: XScreenSaver support enabled
2011-08-09 22:56:26.303 DPMS is disabled.
2011-08-09 22:56:26.315 Desktop video mode: 1920x1080 60.000 Hz
2011-08-09 22:56:27.126 Enabled verbose msgs:  important general
2011-08-09 22:56:27.130 Loading en_us translation for module mythfrontend
2011-08-09 22:56:27.139 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-08-09 22:56:27.139 JoystickMenuThread: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2011-08-09 22:56:27.197 Using Frameless Window
2011-08-09 22:56:27.197 Using Full Screen Window
2011-08-09 22:56:27.351 Using the Qt painter
2011-08-09 22:56:27.455 New DB connection, total: 2
2011-08-09 22:56:27.455 New DB connection, total: 3
2011-08-09 22:56:27.458 Current MythTV Schema Version (DBSchemaVer): 1264
2011-08-09 22:56:27.567 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-08-09 22:56:27.567 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-08-09 22:56:27.569 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-08-09 22:56:27.569 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-08-09 22:56:27.601 Connected to database 'mythconverg' at host: 192.168.2.6
2011-08-09 22:56:27.844 Connected to database 'mythconverg' at host: 192.168.2.6
2011-08-09 22:56:27.979 Registering Internal as a media playback plugin.
2011-08-09 22:56:28.008 Loading en_us translation for module mytharchive
2011-08-09 22:56:28.044 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-09 22:56:28.044 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-09 22:56:28.046 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-09 22:56:28.046 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-09 22:56:28.047 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-09 22:56:28.047 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-09 22:56:28.047 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-08-09 22:56:28.047 Loading en_us translation for module mythgallery
2011-08-09 22:56:28.060 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-08-09 22:56:28.114 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-08-09 22:56:28.121 Loading en_us translation for module mythmusic
2011-08-09 22:56:28.130 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-08-09 22:56:28.156 Loading en_us translation for module mythvideo
2011-08-09 22:56:28.165 Loading en_us translation for module mythweather
2011-08-09 22:56:28.335 Found mainmenu.xml for theme 'Mythbuntu'
2011-08-09 22:56:28.482 MythCoreContext: Connecting to backend server: 192.168.2.6:6543 (try 1 of 1)
2011-08-09 22:56:28.482 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2011-08-09 22:56:28.482 Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
</code>

Output from ps aux | grep mysql
mysql     1166  0.0  2.2 150100 23120 ?        Ssl  Aug08   0:32 /usr/sbin/mysqld
tomas     5943  0.0  0.0   3328   872 pts/1    S+   23:07   0:00 grep --color=auto mysql
All the passwords and 'localhost' in the config.xml have been changed.
I can log into mysql using su password and mythtv password. Ip address 192.168.2.9 has been bind in the my.cf file. Though a line in the my.cf file points to a mysql.sock that doen't exist. Making one makes no difference however.
Both machines primary front and back are using mythbuntu 10.04 pae 2.6.32-33-generic
thanks in advance

---

### Post by klc5555 on 2011-08-09
One possibility, anyway:

Your frontend is trying to connect to the backend on 192.168.2.6 On the other hand, you indicate the bind address in my.cnf is 192.168.2.9 rather than the backend's ip address. Therefore, the master server would appear to be listening at the wrong interface for incoming connections. 

You may have had an easier time enabling the master backend stuff in Mythbuntu's control centre.


Mythtv's frontend connection troubleshooter on their wiki is here: [http://www.mythtv.org/wiki/Mythfrontend](http://www.mythtv.org/wiki/Mythfrontend)

A good writeup on the my.cnf file is here: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch34_:_Basic_MySQL_Configuration#The_.2Fetc.2Fmy.cnf_File](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch34_:_Basic_MySQL_Configuration#The_.2Fetc.2Fmy.cnf_File)

---

### Post by blkbx on 2011-08-10
Hey 
thanks for the reply. The ip ***.9 was a typo. The ip was the same as the one in the backend machine.

One thing I noticed though, the backend machine also has a the front end installed aswell. It must have been done when I did my upgrade via the repos repository. When I try to remove it it say it will remove mythtv, mythfront end and alot of other myth apps. Have you any ideas on that?.
Sorry in a rush again If something doesn't make sence let me know I'll get on to it when I get back.
thanks

---

### Post by uteck on 2011-08-10
Having a frontend on the backend should not be a problem.  Before you remove it, see if it connects.  Might help find the problem.

I have a feeling the backend is not setup to allow remote frontends to connect.  Mythbuntu-control-center should have a section to configure it to allow remote connections.  

When you do remove the forntend, make sure it is not removing mythtv-backend.  Otherwise the stuff it removes is not needed by a backend only box.

---

### Post by blkbx on 2011-08-10
Hey 
thanks for the reply.
I removed myth-frontend and everything worked after that. I never thought about maybe I installed the frontend when I downloaded the upgrades. I would have kept plugging away from a ssh screen on the real frontend never thinking that a frontend on the backend end may have been the issue. 
I think I'll see if I can get an ansaw from mythbuntu.org/repos as to why the upgrades includes the tool box and the front yard.

---

### Post by williammanda on 2011-08-12
> **blkbx said:**
> Hey 
thanks for the reply.
I removed myth-frontend and everything worked after that. I never thought about maybe I installed the frontend when I downloaded the upgrades. I would have kept plugging away from a ssh screen on the real frontend never thinking that a frontend on the backend end may have been the issue. 
I think I'll see if I can get an ansaw from mythbuntu.org/repos as to why the upgrades includes the tool box and the front yard.

I always setup static IP's. One reason is for nfs and the other is for Mythtv. I never use "localhost" but the actual IP address.

---

