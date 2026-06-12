---
title: "FE hangs: Watch TV ... Please Wait"
date: 2011-02-09
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-09
I upgraded today from 0.23 to 0.24 and now have a problem that didn't exist before with v0.23.

When I use FE and select Watch TV to view the program guide (I changed the setting to go to program guide rather than to LiveTV), I get a black screen with the message Please Wait...

It just hangs there. The ESC doesn't work but ALT+F4 does work.

What's gone wrong with v0.24?


Below are two sets of responses from mythfrontend. The first response is from a good session. I could see the program guide and the second output is from a bad session - Please Wait...

Here's the output from the good session when I started FE using terminal mode...
>$ mythfrontend

```

:~$ mythfrontend
2011-02-09 17:56:45.527 mythfrontend version: fixes/0.24 [v0.24-153-g6318d52] www.mythtv.org
2011-02-09 17:56:45.527 Using runtime prefix = /usr
2011-02-09 17:56:45.527 Using configuration directory = /home/dad/.mythtv
2011-02-09 17:56:45.528 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-02-09 17:56:46.320 Empty LocalHostName.
2011-02-09 17:56:46.320 Using localhost value of kub3
2011-02-09 17:56:46.320 Testing network connectivity to '192.168.0.8'
2011-02-09 17:56:46.434 New DB connection, total: 1
2011-02-09 17:56:46.442 Connected to database 'mythconverg' at host: 192.168.0.8
2011-02-09 17:56:46.453 Closing DB connection named 'DBManager0'
2011-02-09 17:56:46.455 Connected to database 'mythconverg' at host: 192.168.0.8
2011-02-09 17:56:46.459 Current locale EN_US
2011-02-09 17:56:46.460 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-02-09 17:56:46.623 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-09 17:56:46.625 DPMS is disabled.
2011-02-09 17:56:46.651 Desktop video mode: 1680x1050 59.954 Hz
2011-02-09 17:56:47.328 Enabled verbose msgs:  important general
2011-02-09 17:56:47.333 Loading en_us translation for module mythfrontend
2011-02-09 17:56:47.347 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-02-09 17:56:47.347 JoystickMenuThread: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2011-02-09 17:56:47.387 Using Frameless Window
2011-02-09 17:56:47.387 Using Full Screen Window
2011-02-09 17:56:47.608 Using the Qt painter
2011-02-09 17:56:47.792 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-09 17:56:47.868 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-02-09 17:56:47.868 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-02-09 17:56:47.870 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-02-09 17:56:47.870 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-02-09 17:56:48.386 Registering Internal as a media playback plugin.
2011-02-09 17:56:48.428 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 17:56:48.428 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 17:56:48.428 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 17:56:48.429 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 17:56:48.429 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 17:56:48.429 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 17:56:48.429 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-09 17:56:48.430 Loading en_us translation for module mythgallery
2011-02-09 17:56:48.438 Loading en_us translation for module mythgame
2011-02-09 17:56:48.448 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-09 17:56:48.464 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-09 17:56:48.467 Loading en_us translation for module mythmusic
2011-02-09 17:56:48.472 Loading en_us translation for module mythnews
2011-02-09 17:56:48.476 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-02-09 17:56:48.486 Loading en_us translation for module mythvideo
2011-02-09 17:56:48.493 Loading en_us translation for module mythweather
2011-02-09 17:56:48.883 Found mainmenu.xml for theme 'MythCenter-wide'
2011-02-09 17:56:48.960 MythCoreContext: Connecting to backend server: 192.168.0.8:6543 (try 1 of 1)
2011-02-09 17:56:48.960 Using protocol version 63
2011-02-09 17:56:54.497 TV: Attempting to change from None to WatchingLiveTV
2011-02-09 17:56:54.498 MythCoreContext: Connecting to backend server: 192.168.0.8:6543 (try 1 of 1)
2011-02-09 17:56:54.498 Using protocol version 63
2011-02-09 17:56:54.615 Spawning LiveTV Recorder -- begin
2011-02-09 17:56:54.835 Spawning LiveTV Recorder -- end
2011-02-09 17:56:54.846 We have a playbackURL(/var/lib/mythtv/livetv/3051_20110209175654.mpg) & cardtype(DUMMY)
2011-02-09 17:56:54.846 We have a RingBuffer
2011-02-09 17:56:55.020 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-02-09 17:56:55.051 OSD: Base theme size: 1280x720
2011-02-09 17:56:55.051 OSD: Scaling factors: 0.5625x0.8
2011-02-09 17:56:55.101 OSD: Base theme size: 1280x720
2011-02-09 17:56:55.101 OSD: Scaling factors: 0.5625x0.8
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
2011-02-09 17:56:55.106 Player(0): Video timing method: USleep with busy wait
2011-02-09 17:56:55.106 TV: Changing from None to WatchingLiveTV
2011-02-09 17:56:55.106 TV: State is LiveTV & mctx == ctx
2011-02-09 17:56:55.108 TV: UpdateOSDInput done
2011-02-09 17:56:55.108 TV: UpdateLCD done
2011-02-09 17:56:55.108 TV: ITVRestart done
2011-02-09 17:56:55.206 VideoOutput: Created YV12 OSD.
2011-02-09 17:56:55.539 pause_active: 0
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
2011-02-09 17:56:56.086 Player(0): DecoderGetFrame() called with NULL decoder.
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 528 x 480
YadifDeint: Using existing thread.
2011-02-09 17:56:56.614 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-02-09 17:56:56.662 OSD: Base theme size: 1280x720
2011-02-09 17:56:56.662 OSD: Scaling factors: 1.10156x0.472222
2011-02-09 17:56:56.701 AFD: Opened codec 0xac043e70, id(MPEG2VIDEO) type(Video)
2011-02-09 17:56:56.701 AFD: codec AC3 has 2 channels
2011-02-09 17:56:56.702 AFD: Opened codec 0xac089a30, id(AC3) type(Audio)
2011-02-09 17:56:56.702 AFD: codec AC3 has 1 channels
2011-02-09 17:56:56.702 AFD: Opened codec 0xac03dac0, id(AC3) type(Audio)
2011-02-09 17:56:57.106 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-02-09 17:56:57.162 AudioPlayer: Enabling Audio
2011-02-09 17:58:59.200 OSD: Base theme size: 1280x720
2011-02-09 17:58:59.200 OSD: Scaling factors: 0.4125x0.666667
2011-02-09 17:58:59.303 VideoOutput: Created YV12 OSD.
2011-02-09 17:59:01.756 TV: Attempting to change from WatchingLiveTV to None
2011-02-09 17:59:01.775 MythPainter: 32 images not yet de-allocated.
2011-02-09 17:59:02.018 TV: Changing from WatchingLiveTV to None
2011-02-09 17:59:05.818 Deleting UPnP client...

```Here's the output from the bad session "please wait"
```

:~$ mythfrontend
2011-02-09 18:27:05.632 mythfrontend version: fixes/0.24 [v0.24-153-g6318d52] www.mythtv.org
2011-02-09 18:27:05.632 Using runtime prefix = /usr
2011-02-09 18:27:05.632 Using configuration directory = /home/dad/.mythtv
2011-02-09 18:27:05.633 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-02-09 18:27:06.058 Empty LocalHostName.
2011-02-09 18:27:06.059 Using localhost value of kub3
2011-02-09 18:27:06.059 Testing network connectivity to '192.168.0.8'
2011-02-09 18:27:06.173 New DB connection, total: 1
2011-02-09 18:27:06.182 Connected to database 'mythconverg' at host: 192.168.0.8
2011-02-09 18:27:06.193 Closing DB connection named 'DBManager0'
2011-02-09 18:27:06.195 Connected to database 'mythconverg' at host: 192.168.0.8
2011-02-09 18:27:06.199 Current locale EN_US
2011-02-09 18:27:06.199 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-02-09 18:27:06.362 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-09 18:27:06.364 DPMS is disabled.
2011-02-09 18:27:06.399 Desktop video mode: 1680x1050 59.954 Hz
2011-02-09 18:27:07.083 Enabled verbose msgs:  important general
2011-02-09 18:27:07.091 Loading en_us translation for module mythfrontend
2011-02-09 18:27:07.107 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-02-09 18:27:07.107 JoystickMenuThread: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2011-02-09 18:27:07.143 Using Frameless Window
2011-02-09 18:27:07.143 Using Full Screen Window
2011-02-09 18:27:07.371 Using the Qt painter
2011-02-09 18:27:07.559 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-09 18:27:07.652 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-02-09 18:27:07.652 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-02-09 18:27:07.654 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-02-09 18:27:07.654 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-02-09 18:27:08.065 Registering Internal as a media playback plugin.
2011-02-09 18:27:08.099 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 18:27:08.099 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 18:27:08.099 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-09 18:27:08.100 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-09 18:27:08.100 Loading en_us translation for module mythgallery
2011-02-09 18:27:08.109 Loading en_us translation for module mythgame
2011-02-09 18:27:08.121 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-09 18:27:08.140 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-09 18:27:08.145 Loading en_us translation for module mythmusic
2011-02-09 18:27:08.151 Loading en_us translation for module mythnews
2011-02-09 18:27:08.155 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-02-09 18:27:08.169 Loading en_us translation for module mythvideo
2011-02-09 18:27:08.177 Loading en_us translation for module mythweather
2011-02-09 18:27:08.577 Found mainmenu.xml for theme 'MythCenter-wide'
2011-02-09 18:27:08.657 MythCoreContext: Connecting to backend server: 192.168.0.8:6543 (try 1 of 1)
2011-02-09 18:27:08.658 Using protocol version 63
2011-02-09 18:27:10.472 TV: Attempting to change from None to WatchingLiveTV
2011-02-09 18:27:10.472 MythCoreContext: Connecting to backend server: 192.168.0.8:6543 (try 1 of 1)
2011-02-09 18:27:10.473 Using protocol version 63
2011-02-09 18:27:10.573 Spawning LiveTV Recorder -- begin
2011-02-09 18:27:10.987 Spawning LiveTV Recorder -- end
2011-02-09 18:27:10.997 We have a playbackURL(/var/lib/mythtv/livetv/3051_20110209182710.mpg) & cardtype(DUMMY)
2011-02-09 18:27:10.997 We have a RingBuffer
2011-02-09 18:27:11.174 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-02-09 18:27:11.218 OSD: Base theme size: 1280x720
2011-02-09 18:27:11.218 OSD: Scaling factors: 0.5625x0.8
2011-02-09 18:27:11.267 OSD: Base theme size: 1280x720
2011-02-09 18:27:11.267 OSD: Scaling factors: 0.5625x0.8
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
2011-02-09 18:27:11.271 Player(0): Video timing method: USleep with busy wait
2011-02-09 18:27:11.272 TV: Changing from None to WatchingLiveTV
2011-02-09 18:27:11.272 TV: State is LiveTV & mctx == ctx
2011-02-09 18:27:11.275 TV: UpdateOSDInput done
2011-02-09 18:27:11.275 TV: UpdateLCD done
2011-02-09 18:27:11.275 TV: ITVRestart done
Killed

```

---

### Post by uncle hammy on 2011-02-09
This is a known issue that has been fixed recently.  [http://www.gossamer-threads.com/lists/mythtv/users/471034](http://www.gossamer-threads.com/lists/mythtv/users/471034) it is awaiting back porting.

---

