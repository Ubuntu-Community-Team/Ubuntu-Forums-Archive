---
title: "Can't Connect To Backend Server"
date: 2011-11-20
forum: Mythbuntu
---

### Post by fullmoonguru on 2011-11-20
I have a new install from remastersys.  I can still see the old install on the other partition & everything looks the same.  I did use a different password for the computer  user this time.

Here is the frontend log:

```
Starting mythfrontend.real..
2011-11-20 18:49:28.914 mythfrontend version: fixes/0.24 [v0.24.1-99-gfdfc989] www.mythtv.org
2011-11-20 18:49:28.915 Using runtime prefix = /usr
2011-11-20 18:49:28.915 Using configuration directory = /home/mammy/.mythtv
2011-11-20 18:49:28.918 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-20 18:49:29.384 Empty LocalHostName.
2011-11-20 18:49:29.385 Using localhost value of mammy
2011-11-20 18:49:29.386 Testing network connectivity to '192.168.0.194'
2011-11-20 18:49:29.530 New DB connection, total: 1
2011-11-20 18:49:29.574 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-20 18:49:29.586 Closing DB connection named 'DBManager0'
2011-11-20 18:49:29.588 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-20 18:49:29.594 Current locale en_US
2011-11-20 18:49:29.594 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-11-20 18:49:29.792 ScreenSaverX11Private: XScreenSaver support enabled
2011-11-20 18:49:29.794 DPMS is disabled.
2011-11-20 18:49:29.838 Desktop video mode: 1920x1080 60.000 Hz
2011-11-20 18:49:29.902 Enabled verbose msgs:  important general
2011-11-20 18:49:29.912 Loading en_us translation for module mythfrontend
2011-11-20 18:49:29.943 LIRC: Successfully initialized '/dev/lircd' using '/home/mammy/.mythtv/lircrc' config
2011-11-20 18:49:29.944 JoystickMenuThread: Joystick disabled - Failed to read /home/mammy/.mythtv/joystickmenurc
2011-11-20 18:49:30.072 Using Frameless Window
2011-11-20 18:49:30.072 Using Full Screen Window
2011-11-20 18:49:30.863 Using the OpenGL painter
2011-11-20 18:49:31.011 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-11-20 18:49:31.011 OpenGL: OpenGL renderer: ION/PCI/SSE2
2011-11-20 18:49:31.011 OpenGL: OpenGL version : 3.3.0 NVIDIA 270.41.06
2011-11-20 18:49:31.011 OpenGL: Max texture size: 8192 x 8192
2011-11-20 18:49:31.012 OpenGL: Max texture units: 4
2011-11-20 18:49:31.012 OpenGL: Direct rendering: Yes
2011-11-20 18:49:31.012 OpenGL: Initialised MythRenderOpenGL
2011-11-20 18:49:40.972 New DB connection, total: 2
2011-11-20 18:49:40.975 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-20 18:49:40.980 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-20 18:49:42.204 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-20 18:49:42.204 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-20 18:49:42.208 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-20 18:49:42.208 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-20 18:49:43.029 Registering Internal as a media playback plugin.
2011-11-20 18:49:43.048 Registering WebBrowser as a media playback plugin.
2011-11-20 18:49:43.049 Loading en_us translation for module mythbrowser
2011-11-20 18:49:43.140 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-20 18:49:43.141 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-20 18:49:43.141 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-20 18:49:43.143 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-11-20 18:49:43.143 Loading en_us translation for module mythgallery
2011-11-20 18:49:43.197 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-11-20 18:49:43.334 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-11-20 18:49:43.356 Loading en_us translation for module mythmusic
2011-11-20 18:49:43.383 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-11-20 18:49:43.449 Loading en_us translation for module mythvideo
2011-11-20 18:49:43.471 Loading en_us translation for module mythweather
2011-11-20 18:49:43.495 Found mainmenu.xml for theme 'blue-abstract-wide'
2011-11-20 18:49:44.139 MythCoreContext: Connecting to backend server: 192.168.0.194:6543 (try 1 of 1)
2011-11-20 18:49:44.139 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2011-11-20 18:49:44.139 Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
2011-11-20 18:49:51.644 MythCoreContext: Connecting to backend server: 192.168.0.194:6543 (try 1 of 1)
2011-11-20 18:49:51.644 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2011-11-20 18:49:58.575 OpenGL: Deleting OpenGL Resources
2011-11-20 18:49:58.619 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
```and the backend log:

```
2011-11-20 18:48:14.904 mythbackend version: fixes/0.24 [v0.24.1-99-gfdfc989] www.mythtv.org
2011-11-20 18:48:15.074 Using runtime prefix = /usr
2011-11-20 18:48:15.119 Using configuration directory = /home/mythtv/.mythtv
2011-11-20 18:48:15.143 Unable to read configuration file mysql.txt
2011-11-20 18:48:15.187 Empty LocalHostName.
2011-11-20 18:48:15.210 Using localhost value of mammy
2011-11-20 18:48:15.280 New DB connection, total: 1
2011-11-20 18:48:15.487 Unable to connect to database!
2011-11-20 18:48:15.546 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-11-20 18:48:17.700 UPnPautoconf() - No UPnP backends found
2011-11-20 18:48:17.844 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-11-20 18:48:18.337 Deleting UPnP client...
2011-11-20 18:48:18.687 Failed to init MythContext.
2011-11-20 18:48:20.020 mythbackend version: fixes/0.24 [v0.24.1-99-gfdfc989] www.mythtv.org
2011-11-20 18:48:20.085 Using runtime prefix = /usr
2011-11-20 18:48:20.140 Using configuration directory = /home/mythtv/.mythtv
2011-11-20 18:48:20.175 Unable to read configuration file mysql.txt
2011-11-20 18:48:20.219 Empty LocalHostName.
2011-11-20 18:48:20.265 Using localhost value of mammy
2011-11-20 18:48:20.387 New DB connection, total: 1
2011-11-20 18:48:20.442 Unable to connect to database!
2011-11-20 18:48:20.478 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-11-20 18:48:22.571 UPnPautoconf() - No UPnP backends found
2011-11-20 18:48:22.609 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-11-20 18:48:22.956 Deleting UPnP client...
2011-11-20 18:48:23.563 Failed to init MythContext.
2011-11-20 18:48:24.749 mythbackend version: fixes/0.24 [v0.24.1-99-gfdfc989] www.mythtv.org
2011-11-20 18:48:24.803 Using runtime prefix = /usr
2011-11-20 18:48:24.836 Using configuration directory = /home/mythtv/.mythtv
2011-11-20 18:48:24.882 Unable to read configuration file mysql.txt
2011-11-20 18:48:24.926 Empty LocalHostName.
2011-11-20 18:48:24.971 Using localhost value of mammy
2011-11-20 18:48:25.086 New DB connection, total: 1
2011-11-20 18:48:25.157 Unable to connect to database!
2011-11-20 18:48:25.371 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-11-20 18:48:27.472 UPnPautoconf() - No UPnP backends found
2011-11-20 18:48:27.611 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-11-20 18:48:27.837 Deleting UPnP client...
2011-11-20 18:48:28.467 Failed to init MythContext.
```Obviously "Access denied for user 'mythtv'@'localhost'" looks like the probem.  I just can't figure out why, or how to fix it.  The install asked if I wanted to join the mythtv group like normal.  It's also strange that it's showing @localhost, because I have is setup with my ip instead.

---

### Post by nickrout on 2011-11-21
```
sudo dpkg-reconfigure mythtv-database
```

answer 'Yes'

```
sudo dpkg-reconfigure mythtv-common
```

set it up appropriately, using the fixed IP address for your backend, and a known password.

make sure you have the right password and other details in the relevant mysql.txt file.

---

