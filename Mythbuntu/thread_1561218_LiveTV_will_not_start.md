---
title: "LiveTV will not start"
date: 2010-08-25
forum: Mythbuntu
---

### Post by coolbeansdude51 on 2010-08-25
Hello all,

I have a brand new box with the latest in MythBuntu.

I try to start Live TV and I get nothing. It just kicks me back to the menu. It doesn't crash or anything.

I have checked the permission in the /var/lib/ directory and everything works there ... 

Specs:
Hauppauge 500
AMD Phenom II X4 965
ECS Black Series A785GM-M

Here is the frontend error log output.

```
2010-08-25 22:52:25.626 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-08-25 22:52:25.627 Using runtime prefix = /usr
2010-08-25 22:52:25.627 Using configuration directory = /home/eveada/.mythtv
2010-08-25 22:52:26.317 Empty LocalHostName.
2010-08-25 22:52:26.317 Using localhost value of eveada-desktop
2010-08-25 22:52:26.327 New DB connection, total: 1
2010-08-25 22:52:26.334 Connected to database 'mythconverg' at host: localhost
2010-08-25 22:52:26.335 Closing DB connection named 'DBManager0'
2010-08-25 22:52:26.352 ScreenSaverX11Private: XScreenSaver support enabled
2010-08-25 22:52:26.353 DPMS is disabled.
2010-08-25 22:52:26.354 Primary screen: 0.
2010-08-25 22:52:26.355 Connected to database 'mythconverg' at host: localhost
2010-08-25 22:52:26.357 Using screen 0, 1280x1024 at 0,0
2010-08-25 22:52:26.379 Desktop video mode: 1280x1024 60.0204 Hz
2010-08-25 22:52:26.506 MythUI Image Cache size set to 20971520 bytes
2010-08-25 22:52:26.528 Enabled verbose msgs:  important general
2010-08-25 22:52:26.532 Primary screen: 0.
2010-08-25 22:52:26.533 Using screen 0, 1280x1024 at 0,0
2010-08-25 22:52:26.533 Using theme base resolution of 1280x720
2010-08-25 22:52:26.538 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-08-25 22:52:26.538 JoystickMenuThread Error: Joystick disabled - Failed to read /home/eveada/.mythtv/joystickmenurc
2010-08-25 22:52:26.577 Using Frameless Window
2010-08-25 22:52:26.577 Using Full Screen Window
2010-08-25 22:52:26.712 Using the Qt painter
2010-08-25 22:52:26.786 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-08-25 22:52:26.793 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-08-25 22:52:26.797 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-08-25 22:52:26.797 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-08-25 22:52:26.808 Current MythTV Schema Version (DBSchemaVer): 1254
2010-08-25 22:52:27.136 Registering Internal as a media playback plugin.
2010-08-25 22:52:27.166 Cannot load language en_us for module mytharchive
2010-08-25 22:52:27.200 MediaMonitorUnix::AddDevice() - empty device path.
2010-08-25 22:52:27.201 MediaMonitorUnix::AddDevice() - empty device path.
2010-08-25 22:52:27.201 MediaMonitorUnix::AddDevice() - empty device path.
2010-08-25 22:52:27.202 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-08-25 22:52:27.202 Cannot load language en_us for module mythgallery
2010-08-25 22:52:27.207 Cannot load language en_us for module mythmovies
2010-08-25 22:52:27.224 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-08-25 22:52:27.242 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-08-25 22:52:27.244 Cannot load language en_us for module mythmusic
2010-08-25 22:52:27.248 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-08-25 22:52:27.260 Cannot load language en_us for module mythvideo
2010-08-25 22:52:27.263 Cannot load language en_us for module mythweather
2010-08-25 22:52:27.264 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-08-25 22:52:27.297 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-08-25 22:52:27.298 Found mainmenu.xml for theme 'Mythbuntu'
2010-08-25 22:52:27.582 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-08-25 22:52:27.583 Using protocol version 56
2010-08-25 22:52:29.073 TV: Attempting to change from None to WatchingLiveTV
2010-08-25 22:52:29.073 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-08-25 22:52:29.074 Using protocol version 56
2010-08-25 22:52:29.091 Spawning LiveTV Recorder -- begin
2010-08-25 22:52:29.174 Spawning LiveTV Recorder -- end
2010-08-25 22:52:29.174 GetEntryAt(-1) failed.
2010-08-25 22:52:29.175 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2010-08-25 22:52:29.175 TV Error: HandleStateChange(): LiveTV not successfully started
2010-08-25 22:52:29.175 We have a RingBuffer
2010-08-25 22:52:29.237 TV Error: LiveTV not successfully started
2010-08-25 22:52:36.522 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-08-25 22:52:38.359 Deleting UPnP client...
```

Any help on this would be great ... can't figure it out. Tried googling as well ... everyone says its a permissions thing. Maybe I am looking in the wrong directory?

Thanks all!

-Adam

---

### Post by DavidOfLondon on 2010-08-26
Did you make sure to be root user before changing permissions? You can change permissions only for them to be knocked back the second you close the settings box.

Also, if you have the firewall up and running be sure that you've added the prog in the permissions there for incoming/outgoing - System>Administration>Firewall Configuration.

Also, have you tried googling some of the fail messages in the Terminal? I'd start with these two below. I always google a terminal response that indicates failure, that usually brings me to someone who has resolved the same problem.

"
2010-08-25 22:52:29.174 GetEntryAt(-1) failed.
2010-08-25 22:52:29.175 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo

---

### Post by coolbeansdude51 on 2010-08-26
It was a combo of bad permissions and not setting the cable channel correctly.

Thanks for the help!

The questions helped a ton!

-Adam

---

