---
title: "Mythtv live recording previews not working after upgrading to 9.10/0.22"
date: 2009-11-19
forum: Mythbuntu
---

### Post by lgiordano on 2009-11-19
Recording preview videos are only showing static images since upgrading from 8.10/0.21 to 9.10/0.22. Live previews are enabled in TV settings. If you look at the bottom of the console output it is grabbing the previews, just not playing them. Worked fine before the upgrade.

```
leandro@PVR:~/Desktop$ mythfrontend
2009-11-19 17:59:09.327 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-19 17:59:09.509 AudioPulseUtil: Suspend Success
2009-11-19 17:59:09.511 Using runtime prefix = /usr
2009-11-19 17:59:09.511 Using configuration directory = /home/leandro/.mythtv
2009-11-19 17:59:10.327 Empty LocalHostName.
2009-11-19 17:59:10.328 Using localhost value of PVR
2009-11-19 17:59:10.343 New DB connection, total: 1
2009-11-19 17:59:10.358 Connected to database 'mythconverg' at host: localhost
2009-11-19 17:59:10.361 Closing DB connection named 'DBManager0'
2009-11-19 17:59:10.413 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-19 17:59:10.417 DPMS is active.
2009-11-19 17:59:10.425 Primary screen: 0.
2009-11-19 17:59:10.426 Connected to database 'mythconverg' at host: localhost
2009-11-19 17:59:10.430 Using screen 0, 1920x1080 at 0,0
2009-11-19 17:59:10.494 MythUI Image Cache size set to 20971520 bytes
2009-11-19 17:59:10.497 Enabled verbose msgs:  important general
2009-11-19 17:59:10.526 Primary screen: 0.
2009-11-19 17:59:10.527 Using screen 0, 1920x1080 at 0,0
2009-11-19 17:59:10.575 Using theme base resolution of 1280x720
2009-11-19 17:59:10.624 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/leandro/.mythtv/lircrc' config
2009-11-19 17:59:10.625 JoystickMenuThread Error: Joystick disabled - Failed to read /home/leandro/.mythtv/joystickmenurc
2009-11-19 17:59:11.275 Using the Qt painter
2009-11-19 17:59:11.488 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-19 17:59:11.553 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-19 17:59:11.587 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-19 17:59:11.588 Unable to load window 'backgroundwindow' from base
2009-11-19 17:59:11.618 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-19 17:59:11.995 WARNING: The theme (ProjectGrayhem-wide) is missing a themeinfo.xml file, ignoring.
2009-11-19 17:59:13.576 WARNING: The theme (ProjectGrayhem-wide) is missing a themeinfo.xml file, ignoring.
2009-11-19 17:59:13.602 Desktop video mode: 1920x1080 60.0024 Hz
2009-11-19 17:59:14.570 Registering Internal as a media playback plugin.
2009-11-19 17:59:14.764 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-19 17:59:14.769 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-19 17:59:14.773 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-19 17:59:14.778 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-19 17:59:14.907 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-19 17:59:15.012 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-19 17:59:15.055 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-19 17:59:15.187 Starting update of ENVCAN
2009-11-19 17:59:15.188 ENVCAN recently updated, skipping.
2009-11-19 17:59:15.195 NetworkControl: Listening for remote connections on port 6546
2009-11-19 17:59:15.199 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-19 17:59:15.330 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-19 17:59:15.334 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-19 17:59:16.853 MythContext: Connecting to backend server: 192.168.1.89:6543 (try 1 of 1)
2009-11-19 17:59:16.855 Using protocol version 50
2009-11-19 17:59:48.670 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2009-11-19 17:59:50.464 Using Password: SetupPinCode
2009-11-19 17:59:54.441 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2009-11-19 17:59:57.529 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2009-11-19 18:00:31.905 Received a remote 'Clear Cache' request
2009-11-19 18:00:34.722 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-11-19 18:00:35.899 New DB connection, total: 2
2009-11-19 18:00:35.900 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:35.904 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-19 18:00:37.007 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-19 18:00:37.008 Using runtime prefix = /usr
2009-11-19 18:00:37.008 Using configuration directory = /home/leandro/.mythtv
2009-11-19 18:00:37.009 Empty LocalHostName.
2009-11-19 18:00:37.010 Using localhost value of PVR
2009-11-19 18:00:37.036 New DB connection, total: 1
2009-11-19 18:00:37.043 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:37.044 Closing DB connection named 'DBManager0'
2009-11-19 18:00:37.045 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:37.057 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-19 18:00:37.060 New DB connection, total: 2
2009-11-19 18:00:37.061 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:37.329 AFD: Opened codec 0x85d05f0, id(MPEG2VIDEO) type(Video)
2009-11-19 18:00:37.330 AFD: codec MP2 has 2 channels
2009-11-19 18:00:37.330 AFD: Opened codec 0x85cfd40, id(MP2) type(Audio)
2009-11-19 18:00:37.465 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-19 18:00:37.466 Using runtime prefix = /usr
2009-11-19 18:00:37.466 Using configuration directory = /home/leandro/.mythtv
2009-11-19 18:00:37.467 Empty LocalHostName.
2009-11-19 18:00:37.468 Using localhost value of PVR
2009-11-19 18:00:37.490 New DB connection, total: 1
2009-11-19 18:00:37.499 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:37.499 Closing DB connection named 'DBManager0'
2009-11-19 18:00:37.501 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:37.508 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-19 18:00:37.512 New DB connection, total: 2
2009-11-19 18:00:37.513 Connected to database 'mythconverg' at host: localhost
2009-11-19 18:00:37.692 Preview: Grabbed preview '/var/lib/mythtv/recordings/1284_20091119180000.mpg' 720x480@31s
[swscaler @ 0xa2d5280]No accelerated colorspace conversion found.
2009-11-19 18:00:37.942 Preview: Grabbed preview '/var/lib/mythtv/recordings/1367_20091119133000.nuv' 720x480@31s
```

---

### Post by trainboy on 2010-06-01
And, therein lies the reason why MythTV is not (nor may never) be ready for prime time.

When your software is developed by volunteers, there is no one in charge to smack people in the head and say, "Cut it out. That's a bad idea."

So, instead of fixing real bugs, somebody decided it would be good to put new lipstick on the pig. In the process of bolting a completely new UI onto the product, stuff that was working got dropped on the floor.

In this case, the new UI framework does not have a video widget that will play the recorded program in the preview box. So, all you get is the static preview. Until someone writes such a widget for the new UI framework, there will be no video preview -- despite the fact that there are flags in the setup menus that would lead you to believe that turning them on would make things work.

Incidentally, its not that I'm complaining. For free software, its a pretty good product. But, the developers can do whatever they like. If they think something is cool, they probably will put it into the product and release it on the world. Too baddy if it breaks something you were using. You could, after all, join the development group and fix things if you don't like them.

So, my advice is, if you get a version that you like, install it on your production systems and stick with it. There's no reason why Mythbuntu 8.04 shouldn't keep running for the next 10 or 15 years. Turn off all automatic updates and never apply any patches. If you must upgrade, build yourself a test system, install the new stuff on it, and check it out thoroughly before you buy.

---

