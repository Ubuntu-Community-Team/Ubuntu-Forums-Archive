---
title: "segmentation fault.. what a nice cryptic message"
date: 2010-09-23
forum: Mythbuntu
---

### Post by LowSky on 2010-09-23
I try to watch a recording on mythtv and mythtv just quits
anyone know what is going wrong?
Ubutnu 10.04, mythtv .23.1


here's the terminal output

```
john@jpc-desktop:~$ mythfrontend
2010-09-23 14:14:25.553 mythfrontend version:
branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 14:14:25.553 Using runtime prefix = /usr
2010-09-23 14:14:25.553 Using configuration directory
= /home/john/.mythtv
2010-09-23 14:14:26.302 Empty LocalHostName.
2010-09-23 14:14:26.302 Using localhost value of jpc-desktop
2010-09-23 14:14:26.310 New DB connection, total: 1
2010-09-23 14:14:26.317 Connected to database 'mythconverg' at host:
localhost
2010-09-23 14:14:26.318 Closing DB connection named 'DBManager0'
2010-09-23 14:14:26.333 ScreenSaverX11Private: Gnome screen saver
support enabled
2010-09-23 14:14:26.335 DPMS is active.
2010-09-23 14:14:26.336 Primary screen: 0.
2010-09-23 14:14:26.337 Connected to database 'mythconverg' at host:
localhost
2010-09-23 14:14:26.339 Using screen 0, 1440x900 at 0,0
2010-09-23 14:14:26.398 Desktop video mode: 1440x900 59.891 Hz
2010-09-23 14:14:26.415 MythUI Image Cache size set to 20971520 bytes
2010-09-23 14:14:26.436 AudioPulseUtil: Suspend Success
2010-09-23 14:14:26.436 Enabled verbose msgs:  important general
2010-09-23 14:14:26.443 Primary screen: 0.
2010-09-23 14:14:26.444 Using screen 0, 1440x900 at 0,0
2010-09-23 14:14:26.445 Using theme base resolution of 1280x720
2010-09-23 14:14:26.451 LIRC: Successfully initialized '/dev/lircd'
using '/home/john/.mythtv/lircrc' config
2010-09-23 14:14:26.451 JoystickMenuThread Error: Joystick disabled -
Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 14:14:26.492 Using Frameless Window
2010-09-23 14:14:26.492 Using Full Screen Window
2010-09-23 14:14:26.647 Using the Qt painter
2010-09-23 14:14:26.782 XMLParseBase: Loaded base theme from
'/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 14:14:26.786 XMLParseBase: Loaded base theme from
'/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 14:14:26.792 XMLParseBase: Loaded base theme from
'/usr/share/mythtv/themes/default/base.xml'
2010-09-23 14:14:26.792 XMLParseBase, Error: Unable to load window
'backgroundwindow' from base
2010-09-23 14:14:26.795 Current MythTV Schema Version (DBSchemaVer):
1254
2010-09-23 14:14:27.147 Registering Internal as a media playback plugin.
2010-09-23 14:14:27.182 Cannot load language en_us for module
mytharchive
2010-09-23 14:14:27.187 Cannot load language en_us for module
mythbrowser
2010-09-23 14:14:27.192 Registering WebBrowser as a media playback
plugin.
2010-09-23 14:14:27.192 Cannot load language en_us for module
mythbrowser
2010-09-23 14:14:27.231 MediaMonitorUnix::AddDevice() - empty device
path.
2010-09-23 14:14:27.231 MediaMonitorUnix::AddDevice() - empty device
path.
2010-09-23 14:14:27.232 MediaMonitorUnix::AddDevice() - empty device
path.
2010-09-23 14:14:27.233 MediaMonitorUnix::AddDevice() - empty device
path.
2010-09-23 14:14:27.233 MediaMonitorUnix::AddDevice() - empty device
path.
2010-09-23 14:14:27.233 MediaMonitorUnix::AddDevice() - empty device
path.
2010-09-23 14:14:27.233 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 14:14:27.234 Cannot load language en_us for module
mythgallery
2010-09-23 14:14:27.237 Cannot load language en_us for module mythgame
2010-09-23 14:14:27.239 Cannot load language en_us for module mythmovies
2010-09-23 14:14:27.248 Current MythMusic Schema Version
(MusicDBSchemaVer): 1017
2010-09-23 14:14:27.284 MonitorRegisterExtensions(0x40,
mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 14:14:27.290 Cannot load language en_us for module mythmusic
2010-09-23 14:14:27.295 Cannot load language en_us for module mythnews
2010-09-23 14:14:27.305 Current MythVideo Schema Version
(mythvideo.DBSchemaVer): 1032
2010-09-23 14:14:27.338 Cannot load language en_us for module mythvideo
2010-09-23 14:14:27.348 Cannot load language en_us for module
mythweather
2010-09-23 14:14:27.350 NetworkControl: Listening for remote connections
on port 6546
2010-09-23 14:14:27.352 XMLParseBase: Loading window theme
from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 14:14:27.407 Loading menu theme
from /home/john/.mythtv/mainmenu.xml
2010-09-23 14:14:27.409 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 14:14:27.410 CD/DVD '/media/20100921-lucid' contained none of
                        /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 14:14:27.410 Searching CD statistically - file by file!
2010-09-23 14:14:27.716 MythContext: Connecting to backend server:
192.168.0.244:6543 (try 1 of 1)
2010-09-23 14:14:27.717 Using protocol version 23056
2010-09-23 14:14:33.752 Loading menu theme
from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 14:14:35.035 New DB connection, total: 2
2010-09-23 14:14:35.036 Connected to database 'mythconverg' at host:
localhost
2010-09-23 14:14:35.038 XMLParseBase: Loading window theme
from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 14:14:37.729 TV: Attempting to change from None to
WatchingPreRecorded
2010-09-23 14:14:37.978 AFD: Opened codec 0x8c352c0, id(H264)
type(Video)
2010-09-23 14:14:37.978 AFD: codec AAC has 2 channels
2010-09-23 14:14:37.978 AFD: Opened codec 0x8c2f6a0, id(AAC) type(Audio)
2010-09-23 14:14:38.066 Opening audio device 'default'. ch 2(2) sr 48000
(reenc 0)
2010-09-23 14:14:38.067 Opening ALSA audio device 'default'.
2010-09-23 14:14:38.122 mixer unable to find control Master 1
2010-09-23 14:14:38.154 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video
Texture'
2010-09-23 14:14:38.291 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 14:14:38.948 TV: Changing from None to WatchingPreRecorded
2010-09-23 14:14:38.949 Realtime priority would require SUID as root.
2010-09-23 14:14:38.953 OpenGLVideoSync()
Segmentation fault


```



here's mythtv frontend log from the past day

```

2010-09-23 06:18:08.104 mythfrontend version: branches/release-0-23-fixes [26434] www.mythtv.org
2010-09-23 06:18:08.104 Using runtime prefix = /usr
2010-09-23 06:18:08.104 Using configuration directory = /home/john/.mythtv
2010-09-23 06:18:08.449 Empty LocalHostName.
2010-09-23 06:18:08.449 Using localhost value of jpc-desktop
2010-09-23 06:18:08.452 New DB connection, total: 1
2010-09-23 06:18:08.454 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:18:08.455 Closing DB connection named 'DBManager0'
2010-09-23 06:18:08.467 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:18:08.467 DPMS is active.
2010-09-23 06:18:08.467 Primary screen: 0.
2010-09-23 06:18:08.468 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:18:08.468 Using screen 0, 1440x900 at 0,0
2010-09-23 06:18:08.521 Desktop video mode: 1440x900 59.891 Hz
2010-09-23 06:18:08.532 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:18:08.553 AudioPulseUtil: Suspend Success
2010-09-23 06:18:08.553 Enabled verbose msgs:  important general
2010-09-23 06:18:08.574 Primary screen: 0.
2010-09-23 06:18:08.574 Using screen 0, 1440x900 at 0,0
2010-09-23 06:18:08.597 Using theme base resolution of 1280x720
2010-09-23 06:18:08.614 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:18:08.614 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:18:08.646 Using Frameless Window
2010-09-23 06:18:08.646 Using Full Screen Window
2010-09-23 06:18:08.811 Using the OpenGL painter
Starting mythfrontend.real..
2010-09-23 06:21:42.114 mythfrontend version: branches/release-0-23-fixes [26434] www.mythtv.org
2010-09-23 06:21:42.114 Using runtime prefix = /usr
2010-09-23 06:21:42.114 Using configuration directory = /home/john/.mythtv
2010-09-23 06:21:42.736 Empty LocalHostName.
2010-09-23 06:21:42.737 Using localhost value of jpc-desktop
2010-09-23 06:21:42.747 New DB connection, total: 1
2010-09-23 06:21:42.755 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:21:42.756 Closing DB connection named 'DBManager0'
2010-09-23 06:21:42.771 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:21:42.772 DPMS is active.
2010-09-23 06:21:42.774 Primary screen: 1.
2010-09-23 06:21:42.774 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:21:42.776 Using screen 1, 1366x768 at 0,0
2010-09-23 06:21:42.832 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:21:42.865 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:21:42.899 AudioPulseUtil: Suspend Success
2010-09-23 06:21:42.899 Enabled verbose msgs:  important general
2010-09-23 06:21:42.904 Primary screen: 1.
2010-09-23 06:21:42.904 Using screen 1, 1366x768 at 0,0
2010-09-23 06:21:42.906 Using theme base resolution of 1280x720
2010-09-23 06:21:42.913 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:21:42.913 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:21:42.951 Using Frameless Window
2010-09-23 06:21:42.951 Using Full Screen Window
2010-09-23 06:21:43.099 Using the Qt painter
2010-09-23 06:21:43.100 Removing stale cache dir: /home/john/.mythtv/themecache/Mythbuntu.1440.900
2010-09-23 06:21:43.223 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:21:43.227 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:21:43.232 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:21:43.232 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:21:43.234 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:21:43.235 New DB connection, total: 2
2010-09-23 06:21:43.235 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:21:43.235 New DB connection, total: 3
2010-09-23 06:21:43.236 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:21:43.643 Registering Internal as a media playback plugin.
2010-09-23 06:21:43.675 Cannot load language en_us for module mytharchive
2010-09-23 06:21:43.679 Cannot load language en_us for module mythbrowser
2010-09-23 06:21:43.683 Registering WebBrowser as a media playback plugin.
2010-09-23 06:21:43.683 Cannot load language en_us for module mythbrowser
2010-09-23 06:21:43.721 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:21:43.721 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:21:43.722 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:21:43.724 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:21:43.725 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:21:43.725 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:21:43.726 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:21:43.726 Cannot load language en_us for module mythgallery
2010-09-23 06:21:43.736 Cannot load language en_us for module mythgame
2010-09-23 06:21:43.740 Cannot load language en_us for module mythmovies
2010-09-23 06:21:43.762 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:21:43.778 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:21:43.781 Cannot load language en_us for module mythmusic
2010-09-23 06:21:43.784 Cannot load language en_us for module mythnews
2010-09-23 06:21:43.789 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:21:43.803 Cannot load language en_us for module mythvideo
2010-09-23 06:21:43.808 Cannot load language en_us for module mythweather
2010-09-23 06:21:43.809 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:21:43.809 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:21:43.869 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:21:43.869 Searching CD statistically - file by file!
2010-09-23 06:21:43.876 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:21:43.879 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:21:46.154 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:21:46.156 Using protocol version 23056
2010-09-23 06:21:47.560 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:21:48.078 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:22:49.899 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:22:50.100 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.101 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.102 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.102 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.103 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.103 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.103 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.104 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.104 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.105 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.106 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.106 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.107 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.119 [mpeg2video @ 0xb668c960]mpeg_decode_postinit() failure
2010-09-23 06:22:50.208 AFD: Opened codec 0x9a13820, id(MPEG2VIDEO) type(Video)
2010-09-23 06:22:50.208 AFD: codec AC3 has 6 channels
2010-09-23 06:22:50.209 AFD: Opened codec 0x9a106a0, id(AC3) type(Audio)
2010-09-23 06:22:50.209 AFD: codec AC3 has 2 channels
2010-09-23 06:22:50.210 AFD: Opened codec 0x9a10a50, id(AC3) type(Audio)
2010-09-23 06:22:50.280 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:22:50.281 Opening ALSA audio device 'default'.
2010-09-23 06:22:50.336 mixer unable to find control Master 1
2010-09-23 06:22:50.712 WriteAudio: buffer underrun
2010-09-23 06:22:51.027 VDPAU: Created 2 output surfaces.
2010-09-23 06:22:51.028 VDPAU: Version 1
2010-09-23 06:22:51.028 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:22:51.028 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:22:51.100 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:22:51.101 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:22:51.623 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:22:51.625 Realtime priority would require SUID as root.
2010-09-23 06:22:51.630 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:22:57.595 mythfrontend version: branches/release-0-23-fixes [26434] www.mythtv.org
2010-09-23 06:22:57.595 Using runtime prefix = /usr
2010-09-23 06:22:57.595 Using configuration directory = /home/john/.mythtv
2010-09-23 06:22:58.174 Empty LocalHostName.
2010-09-23 06:22:58.174 Using localhost value of jpc-desktop
2010-09-23 06:22:58.184 New DB connection, total: 1
2010-09-23 06:22:58.191 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:22:58.192 Closing DB connection named 'DBManager0'
2010-09-23 06:22:58.208 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:22:58.209 DPMS is active.
2010-09-23 06:22:58.224 Primary screen: 1.
2010-09-23 06:22:58.225 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:22:58.226 Using screen 1, 1366x768 at 0,0
2010-09-23 06:22:58.280 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:22:58.296 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:22:58.324 AudioPulseUtil: Suspend Success
2010-09-23 06:22:58.325 Enabled verbose msgs:  important general
2010-09-23 06:22:58.329 Primary screen: 1.
2010-09-23 06:22:58.330 Using screen 1, 1366x768 at 0,0
2010-09-23 06:22:58.330 Using theme base resolution of 1280x720
2010-09-23 06:22:58.335 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:22:58.335 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:22:58.363 Using Frameless Window
2010-09-23 06:22:58.363 Using Full Screen Window
2010-09-23 06:22:58.508 Using the Qt painter
2010-09-23 06:22:58.632 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:22:58.640 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:22:58.644 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:22:58.644 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:22:58.650 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:22:58.997 Registering Internal as a media playback plugin.
2010-09-23 06:22:59.028 Cannot load language en_us for module mytharchive
2010-09-23 06:22:59.032 Cannot load language en_us for module mythbrowser
2010-09-23 06:22:59.036 Registering WebBrowser as a media playback plugin.
2010-09-23 06:22:59.036 Cannot load language en_us for module mythbrowser
2010-09-23 06:22:59.072 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:22:59.073 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:22:59.073 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:22:59.075 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:22:59.076 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:22:59.076 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:22:59.077 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:22:59.078 Cannot load language en_us for module mythgallery
2010-09-23 06:22:59.085 Cannot load language en_us for module mythgame
2010-09-23 06:22:59.087 Cannot load language en_us for module mythmovies
2010-09-23 06:22:59.096 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:22:59.147 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:22:59.154 Cannot load language en_us for module mythmusic
2010-09-23 06:22:59.161 Cannot load language en_us for module mythnews
2010-09-23 06:22:59.173 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:22:59.204 Cannot load language en_us for module mythvideo
2010-09-23 06:22:59.213 Cannot load language en_us for module mythweather
2010-09-23 06:22:59.216 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:22:59.217 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:22:59.220 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:22:59.220 Searching CD statistically - file by file!
2010-09-23 06:22:59.287 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:22:59.288 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:22:59.629 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:22:59.630 Using protocol version 23056
2010-09-23 06:23:02.193 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:23:02.833 New DB connection, total: 2
2010-09-23 06:23:02.836 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:02.837 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:23:08.725 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:23:08.876 AFD: Opened codec 0x8de9910, id(MPEG2VIDEO) type(Video)
2010-09-23 06:23:08.876 AFD: codec AC3 has 6 channels
2010-09-23 06:23:08.877 AFD: Opened codec 0x8de8280, id(AC3) type(Audio)
2010-09-23 06:23:08.878 AFD: codec AC3 has 2 channels
2010-09-23 06:23:08.879 AFD: Opened codec 0x8de8800, id(AC3) type(Audio)
2010-09-23 06:23:08.948 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:23:08.949 Opening ALSA audio device 'default'.
2010-09-23 06:23:09.015 mixer unable to find control Master 1
2010-09-23 06:23:09.148 VDPAU: Created 2 output surfaces.
2010-09-23 06:23:09.148 VDPAU: Version 1
2010-09-23 06:23:09.148 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:23:09.148 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:23:09.185 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:23:09.186 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:23:09.278 Realtime priority would require SUID as root.
2010-09-23 06:23:09.279 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:23:09.307 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:23:17.017 mythfrontend version: branches/release-0-23-fixes [26434] www.mythtv.org
2010-09-23 06:23:17.017 Using runtime prefix = /usr
2010-09-23 06:23:17.017 Using configuration directory = /home/john/.mythtv
Starting mythfrontend.real..
2010-09-23 06:23:17.194 mythfrontend version: branches/release-0-23-fixes [26434] www.mythtv.org
2010-09-23 06:23:17.194 Using runtime prefix = /usr
2010-09-23 06:23:17.194 Using configuration directory = /home/john/.mythtv
2010-09-23 06:23:17.195 MediaRenderer::HttpServer Create Error
2010-09-23 06:23:17.196 Empty LocalHostName.
2010-09-23 06:23:17.196 Using localhost value of jpc-desktop
2010-09-23 06:23:17.199 New DB connection, total: 1
2010-09-23 06:23:17.202 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:17.202 Closing DB connection named 'DBManager0'
2010-09-23 06:23:17.212 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:23:17.213 DPMS is active.
2010-09-23 06:23:17.214 Primary screen: 1.
2010-09-23 06:23:17.215 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:17.216 Using screen 1, 1366x768 at 0,0
2010-09-23 06:23:17.267 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:23:17.283 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:23:17.318 AudioPulseUtil: Suspend Success
2010-09-23 06:23:17.318 Enabled verbose msgs:  important general
2010-09-23 06:23:17.324 Primary screen: 1.
2010-09-23 06:23:17.325 Using screen 1, 1366x768 at 0,0
2010-09-23 06:23:17.326 Using theme base resolution of 1280x720
2010-09-23 06:23:17.334 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:23:17.334 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:23:17.371 Using Frameless Window
2010-09-23 06:23:17.372 Using Full Screen Window
2010-09-23 06:23:17.516 Using the Qt painter
2010-09-23 06:23:17.642 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:23:17.651 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:23:17.657 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:23:17.657 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:23:17.662 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:23:17.745 Empty LocalHostName.
2010-09-23 06:23:17.745 Using localhost value of jpc-desktop
2010-09-23 06:23:17.756 New DB connection, total: 1
2010-09-23 06:23:17.763 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:17.764 Closing DB connection named 'DBManager0'
2010-09-23 06:23:17.780 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:23:17.782 DPMS is active.
2010-09-23 06:23:17.784 Primary screen: 1.
2010-09-23 06:23:17.784 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:17.786 Using screen 1, 1366x768 at 0,0
2010-09-23 06:23:17.842 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:23:17.859 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:23:17.903 AudioPulseUtil: Suspend Success
2010-09-23 06:23:17.903 Enabled verbose msgs:  important general
2010-09-23 06:23:17.908 Primary screen: 1.
2010-09-23 06:23:17.909 Using screen 1, 1366x768 at 0,0
2010-09-23 06:23:17.910 Using theme base resolution of 1280x720
2010-09-23 06:23:17.917 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:23:17.917 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:23:17.955 Using Frameless Window
2010-09-23 06:23:17.956 Using Full Screen Window
2010-09-23 06:23:18.033 Registering Internal as a media playback plugin.
2010-09-23 06:23:18.063 Cannot load language en_us for module mytharchive
2010-09-23 06:23:18.067 Cannot load language en_us for module mythbrowser
2010-09-23 06:23:18.071 Registering WebBrowser as a media playback plugin.
2010-09-23 06:23:18.071 Cannot load language en_us for module mythbrowser
2010-09-23 06:23:18.108 Using the Qt painter
2010-09-23 06:23:18.118 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.119 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.119 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.122 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.122 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.123 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.124 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:23:18.124 Cannot load language en_us for module mythgallery
2010-09-23 06:23:18.133 Cannot load language en_us for module mythgame
2010-09-23 06:23:18.138 Cannot load language en_us for module mythmovies
2010-09-23 06:23:18.156 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:23:18.193 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:23:18.201 Cannot load language en_us for module mythmusic
2010-09-23 06:23:18.209 Cannot load language en_us for module mythnews
2010-09-23 06:23:18.221 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:23:18.233 Cannot load language en_us for module mythvideo
2010-09-23 06:23:18.235 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:23:18.240 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:23:18.241 Cannot load language en_us for module mythweather
2010-09-23 06:23:18.242 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:23:18.243 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:23:18.245 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:23:18.245 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:23:18.248 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:23:18.259 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:23:18.259 Searching CD statistically - file by file!
2010-09-23 06:23:18.302 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:23:18.303 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:23:18.532 Registering Internal as a media playback plugin.
2010-09-23 06:23:18.541 Cannot load language en_us for module mytharchive
2010-09-23 06:23:18.543 Cannot load language en_us for module mythbrowser
2010-09-23 06:23:18.544 Registering WebBrowser as a media playback plugin.
2010-09-23 06:23:18.544 Cannot load language en_us for module mythbrowser
2010-09-23 06:23:18.549 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:23:18.549 Using protocol version 23056
2010-09-23 06:23:18.568 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.569 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.569 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.570 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.570 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.570 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:23:18.571 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:23:18.571 Cannot load language en_us for module mythgallery
2010-09-23 06:23:18.575 Cannot load language en_us for module mythgame
2010-09-23 06:23:18.577 Cannot load language en_us for module mythmovies
2010-09-23 06:23:18.591 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:23:18.612 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:23:18.615 Cannot load language en_us for module mythmusic
2010-09-23 06:23:18.618 Cannot load language en_us for module mythnews
2010-09-23 06:23:18.623 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:23:18.636 Cannot load language en_us for module mythvideo
2010-09-23 06:23:18.640 Cannot load language en_us for module mythweather
2010-09-23 06:23:18.641 NetworkControl failed to bind to port 6546.
2010-09-23 06:23:18.642 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:23:18.647 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:23:18.647 Searching CD statistically - file by file!
2010-09-23 06:23:18.700 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:23:18.701 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:23:18.976 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:23:18.977 Using protocol version 23056
2010-09-23 06:23:20.831 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:23:21.447 New DB connection, total: 2
2010-09-23 06:23:21.448 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:21.450 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:23:22.749 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:23:22.956 AFD: Opened codec 0x9f00b6e0, id(H264) type(Video)
2010-09-23 06:23:22.957 AFD: codec AAC has 2 channels
2010-09-23 06:23:22.957 AFD: Opened codec 0x9f00a470, id(AAC) type(Audio)
2010-09-23 06:23:23.028 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:23:23.029 Opening ALSA audio device 'default'.
2010-09-23 06:23:23.084 mixer unable to find control Master 1
2010-09-23 06:23:23.196 VDPAU: Created 2 output surfaces.
2010-09-23 06:23:23.196 VDPAU: Version 1
2010-09-23 06:23:23.196 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:23:23.196 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:23:23.269 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:23:23.271 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:23:23.356 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:23:23.356 Realtime priority would require SUID as root.
2010-09-23 06:23:23.358 OpenGLVideoSync()
2010-09-23 06:23:34.534 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:23:35.668 New DB connection, total: 2
2010-09-23 06:23:35.668 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:23:35.670 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:23:41.945 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:23:42.114 AFD: Opened codec 0xa75f060, id(MPEG2VIDEO) type(Video)
2010-09-23 06:23:42.114 AFD: codec AC3 has 6 channels
2010-09-23 06:23:42.115 AFD: Opened codec 0xa75f7b0, id(AC3) type(Audio)
2010-09-23 06:23:42.115 AFD: codec AC3 has 2 channels
2010-09-23 06:23:42.115 AFD: Opened codec 0xa4d06a0, id(AC3) type(Audio)
2010-09-23 06:23:42.172 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:23:42.173 Opening ALSA audio device 'default'.
2010-09-23 06:23:42.227 mixer unable to find control Master 1
2010-09-23 06:23:42.378 VDPAU: Created 2 output surfaces.
2010-09-23 06:23:42.378 VDPAU: Version 1
2010-09-23 06:23:42.378 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:23:42.378 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:23:42.414 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:23:42.415 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:23:42.489 Realtime priority would require SUID as root.
2010-09-23 06:23:42.489 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:23:42.492 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:27:36.894 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 06:27:36.894 Using runtime prefix = /usr
2010-09-23 06:27:36.894 Using configuration directory = /home/john/.mythtv
2010-09-23 06:27:37.513 Empty LocalHostName.
2010-09-23 06:27:37.513 Using localhost value of jpc-desktop
2010-09-23 06:27:37.521 New DB connection, total: 1
2010-09-23 06:27:37.528 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:27:37.529 Closing DB connection named 'DBManager0'
2010-09-23 06:27:37.542 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:27:37.543 DPMS is active.
2010-09-23 06:27:37.545 Primary screen: 1.
2010-09-23 06:27:37.546 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:27:37.547 Using screen 1, 1366x768 at 0,0
2010-09-23 06:27:37.603 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:27:37.622 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:27:37.651 AudioPulseUtil: Suspend Success
2010-09-23 06:27:37.652 Enabled verbose msgs:  important general
2010-09-23 06:27:37.657 Primary screen: 1.
2010-09-23 06:27:37.657 Using screen 1, 1366x768 at 0,0
2010-09-23 06:27:37.658 Using theme base resolution of 1280x720
2010-09-23 06:27:37.663 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:27:37.663 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:27:37.701 Using Frameless Window
2010-09-23 06:27:37.701 Using Full Screen Window
2010-09-23 06:27:37.849 Using the Qt painter
2010-09-23 06:27:37.984 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:27:37.990 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:27:37.994 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:27:37.994 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:27:37.997 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:27:38.832 Registering Internal as a media playback plugin.
2010-09-23 06:27:38.863 Cannot load language en_us for module mytharchive
2010-09-23 06:27:38.867 Cannot load language en_us for module mythbrowser
2010-09-23 06:27:38.870 Registering WebBrowser as a media playback plugin.
2010-09-23 06:27:38.871 Cannot load language en_us for module mythbrowser
2010-09-23 06:27:38.906 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:27:38.907 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:27:38.907 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:27:38.910 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:27:38.910 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:27:38.911 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:27:38.912 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:27:38.912 Cannot load language en_us for module mythgallery
2010-09-23 06:27:38.915 Cannot load language en_us for module mythgame
2010-09-23 06:27:38.917 Cannot load language en_us for module mythmovies
2010-09-23 06:27:38.926 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:27:38.962 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:27:38.969 Cannot load language en_us for module mythmusic
2010-09-23 06:27:38.976 Cannot load language en_us for module mythnews
2010-09-23 06:27:38.988 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:27:39.021 Cannot load language en_us for module mythvideo
2010-09-23 06:27:39.032 Cannot load language en_us for module mythweather
2010-09-23 06:27:39.035 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:27:39.037 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:27:39.094 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:27:39.094 Searching CD statistically - file by file!
2010-09-23 06:27:39.153 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:27:39.160 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:27:39.349 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:27:39.350 Using protocol version 23056
2010-09-23 06:27:40.317 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:27:40.739 New DB connection, total: 2
2010-09-23 06:27:40.740 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:27:40.742 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:27:48.746 Received a remote 'Clear Cache' request
2010-09-23 06:27:51.321 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:27:51.482 AFD: Opened codec 0xa1782f0, id(H264) type(Video)
2010-09-23 06:27:51.482 AFD: codec AAC has 2 channels
2010-09-23 06:27:51.482 AFD: Opened codec 0xa17bdd0, id(AAC) type(Audio)
2010-09-23 06:27:51.544 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:27:51.545 Opening ALSA audio device 'default'.
2010-09-23 06:27:51.599 mixer unable to find control Master 1
2010-09-23 06:27:51.713 VDPAU: Created 2 output surfaces.
2010-09-23 06:27:51.713 VDPAU: Version 1
2010-09-23 06:27:51.713 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:27:51.713 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:27:51.801 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:27:51.803 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:27:51.891 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:27:51.891 Realtime priority would require SUID as root.
2010-09-23 06:27:51.895 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:28:56.107 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 06:28:56.107 Using runtime prefix = /usr
2010-09-23 06:28:56.107 Using configuration directory = /home/john/.mythtv
2010-09-23 06:28:56.813 Empty LocalHostName.
2010-09-23 06:28:56.813 Using localhost value of jpc-desktop
2010-09-23 06:28:56.824 New DB connection, total: 1
2010-09-23 06:28:56.831 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:28:56.832 Closing DB connection named 'DBManager0'
2010-09-23 06:28:56.847 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:28:56.848 DPMS is active.
2010-09-23 06:28:56.850 Primary screen: 1.
2010-09-23 06:28:56.851 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:28:56.852 Using screen 1, 1366x768 at 0,0
2010-09-23 06:28:56.915 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:28:56.931 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:28:56.966 AudioPulseUtil: Suspend Success
2010-09-23 06:28:56.966 Enabled verbose msgs:  important general
2010-09-23 06:28:56.973 Primary screen: 1.
2010-09-23 06:28:56.973 Using screen 1, 1366x768 at 0,0
2010-09-23 06:28:56.974 Using theme base resolution of 1280x720
2010-09-23 06:28:56.978 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:28:56.978 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:28:57.024 Using Frameless Window
2010-09-23 06:28:57.024 Using Full Screen Window
2010-09-23 06:28:57.167 Using the Qt painter
2010-09-23 06:28:57.289 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:28:57.309 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:28:57.313 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:28:57.314 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:28:57.319 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:28:57.663 Registering Internal as a media playback plugin.
2010-09-23 06:28:57.676 Cannot load language en_us for module mytharchive
2010-09-23 06:28:57.678 Cannot load language en_us for module mythbrowser
2010-09-23 06:28:57.680 Registering WebBrowser as a media playback plugin.
2010-09-23 06:28:57.680 Cannot load language en_us for module mythbrowser
2010-09-23 06:28:57.695 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:28:57.695 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:28:57.695 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:28:57.697 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:28:57.697 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:28:57.697 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:28:57.697 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:28:57.697 Cannot load language en_us for module mythgallery
2010-09-23 06:28:57.701 Cannot load language en_us for module mythgame
2010-09-23 06:28:57.703 Cannot load language en_us for module mythmovies
2010-09-23 06:28:57.716 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:28:57.751 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:28:57.758 Cannot load language en_us for module mythmusic
2010-09-23 06:28:57.764 Cannot load language en_us for module mythnews
2010-09-23 06:28:57.776 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:28:57.806 Cannot load language en_us for module mythvideo
2010-09-23 06:28:57.815 Cannot load language en_us for module mythweather
2010-09-23 06:28:57.817 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:28:57.819 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:28:57.822 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:28:57.822 Searching CD statistically - file by file!
2010-09-23 06:28:57.884 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:28:57.885 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:28:58.138 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:28:58.139 Using protocol version 23056
2010-09-23 06:28:59.771 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:29:00.432 New DB connection, total: 2
2010-09-23 06:29:00.433 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:29:00.434 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:29:06.138 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:29:06.280 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.280 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.281 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.281 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.282 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.284 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.285 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.286 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.287 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.287 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.287 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.287 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.287 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.288 [mpeg2video @ 0xb668a960]mpeg_decode_postinit() failure
2010-09-23 06:29:06.342 AFD: Opened codec 0x913b950, id(MPEG2VIDEO) type(Video)
2010-09-23 06:29:06.342 AFD: codec AC3 has 6 channels
2010-09-23 06:29:06.343 AFD: Opened codec 0x935e7a0, id(AC3) type(Audio)
2010-09-23 06:29:06.343 AFD: codec AC3 has 2 channels
2010-09-23 06:29:06.344 AFD: Opened codec 0x935ed20, id(AC3) type(Audio)
2010-09-23 06:29:06.416 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:29:06.416 Opening ALSA audio device 'default'.
2010-09-23 06:29:06.471 mixer unable to find control Master 1
2010-09-23 06:29:06.632 VDPAU: Created 2 output surfaces.
2010-09-23 06:29:06.632 VDPAU: Version 1
2010-09-23 06:29:06.632 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:29:06.632 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:29:06.705 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:29:06.707 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:29:06.798 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:29:06.799 Realtime priority would require SUID as root.
2010-09-23 06:29:06.800 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:30:50.776 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 06:30:50.776 Using runtime prefix = /usr
2010-09-23 06:30:50.776 Using configuration directory = /home/john/.mythtv
2010-09-23 06:30:51.257 Empty LocalHostName.
2010-09-23 06:30:51.257 Using localhost value of jpc-desktop
2010-09-23 06:30:51.260 New DB connection, total: 1
2010-09-23 06:30:51.262 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:30:51.262 Closing DB connection named 'DBManager0'
2010-09-23 06:30:51.275 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:30:51.276 DPMS is active.
2010-09-23 06:30:51.276 Primary screen: 1.
2010-09-23 06:30:51.276 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:30:51.277 Using screen 1, 1366x768 at 0,0
2010-09-23 06:30:51.348 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:30:51.355 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:30:51.373 AudioPulseUtil: Suspend Success
2010-09-23 06:30:51.373 Enabled verbose msgs:  important general
2010-09-23 06:30:51.389 Primary screen: 1.
2010-09-23 06:30:51.389 Using screen 1, 1366x768 at 0,0
2010-09-23 06:30:51.399 Using theme base resolution of 1280x720
2010-09-23 06:30:51.416 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:30:51.416 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:30:51.448 Using Frameless Window
2010-09-23 06:30:51.448 Using Full Screen Window
2010-09-23 06:30:51.574 Using the Qt painter
2010-09-23 06:30:51.803 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:30:51.930 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:30:51.956 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:30:51.956 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:30:51.959 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:30:54.752 Registering Internal as a media playback plugin.
2010-09-23 06:30:54.797 Cannot load language en_us for module mytharchive
2010-09-23 06:30:54.807 Cannot load language en_us for module mythbrowser
2010-09-23 06:30:54.808 Registering WebBrowser as a media playback plugin.
2010-09-23 06:30:54.808 Cannot load language en_us for module mythbrowser
2010-09-23 06:30:54.838 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:30:54.838 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:30:54.838 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:30:54.838 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:30:54.839 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:30:54.839 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:30:54.839 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:30:54.839 Cannot load language en_us for module mythgallery
2010-09-23 06:30:54.857 Cannot load language en_us for module mythgame
2010-09-23 06:30:54.868 Cannot load language en_us for module mythmovies
2010-09-23 06:30:55.114 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:30:55.129 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:30:55.130 Cannot load language en_us for module mythmusic
2010-09-23 06:30:55.142 Cannot load language en_us for module mythnews
2010-09-23 06:30:55.218 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:30:55.227 Cannot load language en_us for module mythvideo
2010-09-23 06:30:55.239 Cannot load language en_us for module mythweather
2010-09-23 06:30:55.240 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:30:55.240 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:30:55.245 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:30:55.245 Searching CD statistically - file by file!
2010-09-23 06:30:55.322 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:30:55.323 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:30:55.853 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:30:55.854 Using protocol version 23056
2010-09-23 06:30:57.542 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:30:58.197 New DB connection, total: 2
2010-09-23 06:30:58.197 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:30:58.197 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:30:59.663 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:31:00.384 AFD: Opened codec 0x9d9fc80, id(H264) type(Video)
2010-09-23 06:31:00.384 AFD: codec AAC has 2 channels
2010-09-23 06:31:00.384 AFD: Opened codec 0x9da0030, id(AAC) type(Audio)
2010-09-23 06:31:00.437 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:31:00.437 Opening ALSA audio device 'default'.
2010-09-23 06:31:00.486 mixer unable to find control Master 1
2010-09-23 06:31:01.101 VDPAU: Created 2 output surfaces.
2010-09-23 06:31:01.101 VDPAU: Version 1
2010-09-23 06:31:01.101 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:31:01.101 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:31:01.173 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:31:01.173 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:31:01.647 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:31:01.647 Realtime priority would require SUID as root.
2010-09-23 06:31:01.648 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:31:05.783 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 06:31:05.783 Using runtime prefix = /usr
2010-09-23 06:31:05.783 Using configuration directory = /home/john/.mythtv
2010-09-23 06:31:06.716 Empty LocalHostName.
2010-09-23 06:31:06.716 Using localhost value of jpc-desktop
2010-09-23 06:31:06.720 New DB connection, total: 1
2010-09-23 06:31:06.722 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:31:06.722 Closing DB connection named 'DBManager0'
2010-09-23 06:31:06.727 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:31:06.727 DPMS is active.
2010-09-23 06:31:06.728 Primary screen: 1.
2010-09-23 06:31:06.728 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:31:06.729 Using screen 1, 1366x768 at 0,0
2010-09-23 06:31:06.770 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:31:06.777 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:31:06.790 AudioPulseUtil: Suspend Success
2010-09-23 06:31:06.790 Enabled verbose msgs:  important general
2010-09-23 06:31:06.792 Primary screen: 1.
2010-09-23 06:31:06.792 Using screen 1, 1366x768 at 0,0
2010-09-23 06:31:06.792 Using theme base resolution of 1280x720
2010-09-23 06:31:06.794 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:31:06.794 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:31:06.816 Using Frameless Window
2010-09-23 06:31:06.816 Using Full Screen Window
2010-09-23 06:31:06.933 Using the Qt painter
2010-09-23 06:31:07.045 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:31:07.049 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:31:07.054 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:31:07.054 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:31:07.057 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:31:07.261 Registering Internal as a media playback plugin.
2010-09-23 06:31:07.269 Cannot load language en_us for module mytharchive
2010-09-23 06:31:07.270 Cannot load language en_us for module mythbrowser
2010-09-23 06:31:07.271 Registering WebBrowser as a media playback plugin.
2010-09-23 06:31:07.271 Cannot load language en_us for module mythbrowser
2010-09-23 06:31:07.281 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:31:07.281 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:31:07.281 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:31:07.282 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:31:07.282 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:31:07.282 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:31:07.283 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:31:07.283 Cannot load language en_us for module mythgallery
2010-09-23 06:31:07.285 Cannot load language en_us for module mythgame
2010-09-23 06:31:07.286 Cannot load language en_us for module mythmovies
2010-09-23 06:31:07.295 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:31:07.308 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:31:07.310 Cannot load language en_us for module mythmusic
2010-09-23 06:31:07.312 Cannot load language en_us for module mythnews
2010-09-23 06:31:07.315 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:31:07.323 Cannot load language en_us for module mythvideo
2010-09-23 06:31:07.326 Cannot load language en_us for module mythweather
2010-09-23 06:31:07.326 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:31:07.327 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:31:07.331 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:31:07.331 Searching CD statistically - file by file!
2010-09-23 06:31:07.382 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:31:07.383 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:31:07.617 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:31:07.618 Using protocol version 23056
2010-09-23 06:31:09.667 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 06:31:10.423 New DB connection, total: 2
2010-09-23 06:31:10.423 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:31:10.424 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 06:31:21.536 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 06:31:21.713 AFD: Opened codec 0x9f96710, id(H264) type(Video)
2010-09-23 06:31:21.714 AFD: codec AAC has 2 channels
2010-09-23 06:31:21.714 AFD: Opened codec 0xa02a1b0, id(AAC) type(Audio)
2010-09-23 06:31:21.782 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 06:31:21.783 Opening ALSA audio device 'default'.
2010-09-23 06:31:21.846 mixer unable to find control Master 1
2010-09-23 06:31:22.023 VDPAU: Created 2 output surfaces.
2010-09-23 06:31:22.023 VDPAU: Version 1
2010-09-23 06:31:22.024 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:31:22.024 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:31:22.096 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 06:31:22.097 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:31:22.187 Realtime priority would require SUID as root.
2010-09-23 06:31:22.188 TV: Changing from None to WatchingPreRecorded
2010-09-23 06:31:22.189 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 06:35:43.122 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 06:35:43.123 Using runtime prefix = /usr
2010-09-23 06:35:43.123 Using configuration directory = /home/john/.mythtv
2010-09-23 06:35:43.587 Empty LocalHostName.
2010-09-23 06:35:43.587 Using localhost value of jpc-desktop
2010-09-23 06:35:43.600 New DB connection, total: 1
2010-09-23 06:35:43.602 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:35:43.602 Closing DB connection named 'DBManager0'
2010-09-23 06:35:43.614 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 06:35:43.615 DPMS is active.
2010-09-23 06:35:43.616 Primary screen: 1.
2010-09-23 06:35:43.617 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:35:43.618 Using screen 1, 1366x768 at 0,0
2010-09-23 06:35:43.690 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 06:35:43.713 MythUI Image Cache size set to 20971520 bytes
2010-09-23 06:35:43.747 AudioPulseUtil: Suspend Success
2010-09-23 06:35:43.748 Enabled verbose msgs:  important general
2010-09-23 06:35:43.754 Primary screen: 1.
2010-09-23 06:35:43.755 Using screen 1, 1366x768 at 0,0
2010-09-23 06:35:43.756 Using theme base resolution of 1280x720
2010-09-23 06:35:43.763 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 06:35:43.763 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 06:35:43.814 Using Frameless Window
2010-09-23 06:35:43.814 Using Full Screen Window
2010-09-23 06:35:43.952 Using the Qt painter
2010-09-23 06:35:44.080 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 06:35:44.084 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 06:35:44.089 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 06:35:44.089 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 06:35:44.102 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 06:35:44.501 Registering Internal as a media playback plugin.
2010-09-23 06:35:44.532 Cannot load language en_us for module mytharchive
2010-09-23 06:35:44.536 Cannot load language en_us for module mythbrowser
2010-09-23 06:35:44.540 Registering WebBrowser as a media playback plugin.
2010-09-23 06:35:44.540 Cannot load language en_us for module mythbrowser
2010-09-23 06:35:44.576 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:35:44.576 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:35:44.577 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:35:44.579 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:35:44.580 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:35:44.580 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 06:35:44.581 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 06:35:44.582 Cannot load language en_us for module mythgallery
2010-09-23 06:35:44.586 Cannot load language en_us for module mythgame
2010-09-23 06:35:44.588 Cannot load language en_us for module mythmovies
2010-09-23 06:35:44.597 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 06:35:44.632 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 06:35:44.639 Cannot load language en_us for module mythmusic
2010-09-23 06:35:44.646 Cannot load language en_us for module mythnews
2010-09-23 06:35:44.657 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 06:35:44.688 Cannot load language en_us for module mythvideo
2010-09-23 06:35:44.697 Cannot load language en_us for module mythweather
2010-09-23 06:35:44.700 NetworkControl: Listening for remote connections on port 6546
2010-09-23 06:35:44.701 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 06:35:44.759 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 06:35:44.759 Searching CD statistically - file by file!
2010-09-23 06:35:44.787 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 06:35:44.788 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 06:35:45.045 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:35:45.046 Using protocol version 23056
2010-09-23 06:35:47.068 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-09-23 06:35:48.366 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-09-23 06:36:33.004 Received a remote 'Clear Cache' request
2010-09-23 06:36:36.123 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-09-23 06:36:37.957 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2010-09-23 06:36:43.421 Received a remote 'Clear Cache' request
2010-09-23 06:36:47.812 Using Idle Timer. 121 minutes
2010-09-23 06:36:47.833 TV: Attempting to change from None to WatchingLiveTV
2010-09-23 06:36:47.834 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 06:36:47.835 Using protocol version 23056
2010-09-23 06:36:47.850 Spawning LiveTV Recorder -- begin
2010-09-23 06:36:48.117 Spawning LiveTV Recorder -- end
2010-09-23 06:36:48.121 ProgramInfo(): Updated pathname '':'' -> '1021_20100923063647.mpg'
2010-09-23 06:36:48.126 We have a playbackURL(/media/mythtv/livetv/1021_20100923063647.mpg) & cardtype(DUMMY)
2010-09-23 06:36:48.126 We have a RingBuffer
2010-09-23 06:36:48.204 NVP(0): Disabling Audio, params(-1,2,44100)
2010-09-23 06:36:48.257 ProgramInfo(): Updated pathname '':'' -> '1021_20100923063647.mpg'
2010-09-23 06:36:48.313 ProgramInfo(): Updated pathname '':'' -> '1021_20100923063647.mpg'
2010-09-23 06:36:48.323 VDPAU: Created 2 output surfaces.
2010-09-23 06:36:48.323 VDPAU: Version 1
2010-09-23 06:36:48.323 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 06:36:48.323 VDPAU: Created VDPAU render device 1366x768
2010-09-23 06:36:48.338 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 06:36:48.369 ProgramInfo(): Updated pathname '':'' -> '1021_20100923063647.mpg'
2010-09-23 06:36:48.424 ProgramInfo(): Updated pathname '':'' -> '1021_20100923063647.mpg'
2010-09-23 06:36:48.428 New DB connection, total: 2
2010-09-23 06:36:48.428 TV: Changing from None to WatchingLiveTV
2010-09-23 06:36:48.428 TV: State is LiveTV & mctx == ctx
2010-09-23 06:36:48.429 New DB connection, total: 3
2010-09-23 06:36:48.429 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:36:48.430 Realtime priority would require SUID as root.
2010-09-23 06:36:48.431 Connected to database 'mythconverg' at host: localhost
2010-09-23 06:36:48.432 TV: UpdateOSDInput done
2010-09-23 06:36:48.432 TV: UpdateLCD done
2010-09-23 06:36:48.432 TV: ITVRestart done
2010-09-23 06:36:48.432 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 07:04:29.631 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 07:04:29.632 Using runtime prefix = /usr
2010-09-23 07:04:29.632 Using configuration directory = /home/john/.mythtv
2010-09-23 07:04:30.633 Empty LocalHostName.
2010-09-23 07:04:30.633 Using localhost value of jpc-desktop
2010-09-23 07:04:30.645 New DB connection, total: 1
2010-09-23 07:04:30.652 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:04:30.653 Closing DB connection named 'DBManager0'
2010-09-23 07:04:30.669 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 07:04:30.671 DPMS is active.
2010-09-23 07:04:30.672 Primary screen: 1.
2010-09-23 07:04:30.673 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:04:30.675 Using screen 1, 1366x768 at 0,0
2010-09-23 07:04:30.737 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 07:04:30.746 MythUI Image Cache size set to 20971520 bytes
2010-09-23 07:04:30.770 AudioPulseUtil: Suspend Success
2010-09-23 07:04:30.771 Enabled verbose msgs:  important general
2010-09-23 07:04:30.776 Primary screen: 1.
2010-09-23 07:04:30.776 Using screen 1, 1366x768 at 0,0
2010-09-23 07:04:30.777 Using theme base resolution of 1280x720
2010-09-23 07:04:30.784 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 07:04:30.784 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 07:04:30.822 Using Frameless Window
2010-09-23 07:04:30.822 Using Full Screen Window
2010-09-23 07:04:30.980 Using the Qt painter
2010-09-23 07:04:31.104 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 07:04:31.111 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 07:04:31.115 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 07:04:31.115 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 07:04:31.130 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 07:04:31.479 Registering Internal as a media playback plugin.
2010-09-23 07:04:31.509 Cannot load language en_us for module mytharchive
2010-09-23 07:04:31.513 Cannot load language en_us for module mythbrowser
2010-09-23 07:04:31.517 Registering WebBrowser as a media playback plugin.
2010-09-23 07:04:31.517 Cannot load language en_us for module mythbrowser
2010-09-23 07:04:31.565 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:04:31.565 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:04:31.565 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:04:31.566 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:04:31.566 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:04:31.566 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:04:31.566 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 07:04:31.566 Cannot load language en_us for module mythgallery
2010-09-23 07:04:31.570 Cannot load language en_us for module mythgame
2010-09-23 07:04:31.572 Cannot load language en_us for module mythmovies
2010-09-23 07:04:31.581 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 07:04:31.618 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 07:04:31.625 Cannot load language en_us for module mythmusic
2010-09-23 07:04:31.632 Cannot load language en_us for module mythnews
2010-09-23 07:04:31.643 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 07:04:31.673 Cannot load language en_us for module mythvideo
2010-09-23 07:04:31.683 Cannot load language en_us for module mythweather
2010-09-23 07:04:31.685 NetworkControl: Listening for remote connections on port 6546
2010-09-23 07:04:31.687 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 07:04:31.745 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 07:04:31.745 Searching CD statistically - file by file!
2010-09-23 07:04:31.752 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 07:04:31.753 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 07:04:32.041 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 07:04:32.042 Using protocol version 23056
2010-09-23 07:04:33.811 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2010-09-23 07:04:36.132 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 07:04:37.385 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-09-23 07:04:37.597 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@jpc-desktop/media/mythtv/videos/)
2010-09-23 07:04:37.607 New DB connection, total: 2
2010-09-23 07:04:37.607 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:04:39.748 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-09-23 07:04:40.898 TV: Attempting to change from None to WatchingVideo
2010-09-23 07:04:41.516 AFD: Opened codec 0xa7205b50, id(H264) type(Video)
2010-09-23 07:04:41.516 AFD: codec AAC has 2 channels
2010-09-23 07:04:41.516 AFD: Opened codec 0xa8498f50, id(AAC) type(Audio)
2010-09-23 07:04:41.517 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2010-09-23 07:04:41.592 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 07:04:41.593 Opening ALSA audio device 'default'.
2010-09-23 07:04:41.648 mixer unable to find control Master 1
2010-09-23 07:04:42.135 VDPAU: Created 2 output surfaces.
2010-09-23 07:04:42.135 VDPAU: Version 1
2010-09-23 07:04:42.135 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 07:04:42.135 VDPAU: Created VDPAU render device 1366x768
2010-09-23 07:04:42.148 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 07:04:42.150 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 07:04:42.234 TV: Changing from None to WatchingVideo
2010-09-23 07:04:42.235 New DB connection, total: 3
2010-09-23 07:04:42.235 Realtime priority would require SUID as root.
2010-09-23 07:04:42.235 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:04:42.239 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 07:24:30.661 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 07:24:30.661 Using runtime prefix = /usr
2010-09-23 07:24:30.661 Using configuration directory = /home/john/.mythtv
2010-09-23 07:24:31.545 Empty LocalHostName.
2010-09-23 07:24:31.545 Using localhost value of jpc-desktop
2010-09-23 07:24:31.556 New DB connection, total: 1
2010-09-23 07:24:31.563 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:24:31.564 Closing DB connection named 'DBManager0'
2010-09-23 07:24:31.581 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 07:24:31.582 DPMS is active.
2010-09-23 07:24:31.584 Primary screen: 1.
2010-09-23 07:24:31.584 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:24:31.586 Using screen 1, 1366x768 at 0,0
2010-09-23 07:24:31.644 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 07:24:31.662 MythUI Image Cache size set to 20971520 bytes
2010-09-23 07:24:31.699 AudioPulseUtil: Suspend Success
2010-09-23 07:24:31.700 Enabled verbose msgs:  important general
2010-09-23 07:24:31.705 Primary screen: 1.
2010-09-23 07:24:31.705 Using screen 1, 1366x768 at 0,0
2010-09-23 07:24:31.706 Using theme base resolution of 1280x720
2010-09-23 07:24:31.712 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 07:24:31.713 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 07:24:31.763 Using Frameless Window
2010-09-23 07:24:31.763 Using Full Screen Window
2010-09-23 07:24:31.908 Using the Qt painter
2010-09-23 07:24:32.050 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 07:24:32.057 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 07:24:32.062 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 07:24:32.062 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 07:24:32.067 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 07:24:32.441 Registering Internal as a media playback plugin.
2010-09-23 07:24:32.472 Cannot load language en_us for module mytharchive
2010-09-23 07:24:32.476 Cannot load language en_us for module mythbrowser
2010-09-23 07:24:32.479 Registering WebBrowser as a media playback plugin.
2010-09-23 07:24:32.480 Cannot load language en_us for module mythbrowser
2010-09-23 07:24:32.516 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:24:32.516 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:24:32.517 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:24:32.519 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:24:32.519 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:24:32.520 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:24:32.520 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 07:24:32.520 Cannot load language en_us for module mythgallery
2010-09-23 07:24:32.523 Cannot load language en_us for module mythgame
2010-09-23 07:24:32.525 Cannot load language en_us for module mythmovies
2010-09-23 07:24:32.534 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 07:24:32.570 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 07:24:32.577 Cannot load language en_us for module mythmusic
2010-09-23 07:24:32.584 Cannot load language en_us for module mythnews
2010-09-23 07:24:32.596 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 07:24:32.629 Cannot load language en_us for module mythvideo
2010-09-23 07:24:32.638 Cannot load language en_us for module mythweather
2010-09-23 07:24:32.641 NetworkControl: Listening for remote connections on port 6546
2010-09-23 07:24:32.642 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 07:24:32.700 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 07:24:32.700 Searching CD statistically - file by file!
2010-09-23 07:24:32.727 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 07:24:32.729 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 07:24:32.985 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 07:24:32.986 Using protocol version 23056
2010-09-23 07:24:34.297 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 07:24:34.822 New DB connection, total: 2
2010-09-23 07:24:34.822 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:24:34.824 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 07:24:39.844 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 07:24:40.030 AFD: Opened codec 0x93a5bd0, id(MPEG2VIDEO) type(Video)
2010-09-23 07:24:40.030 AFD: codec AC3 has 6 channels
2010-09-23 07:24:40.031 AFD: Opened codec 0x93a2cb0, id(AC3) type(Audio)
2010-09-23 07:24:40.031 AFD: codec AC3 has 2 channels
2010-09-23 07:24:40.032 AFD: Opened codec 0x9416910, id(AC3) type(Audio)
2010-09-23 07:24:40.104 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 07:24:40.105 Opening ALSA audio device 'default'.
2010-09-23 07:24:40.160 mixer unable to find control Master 1
2010-09-23 07:24:40.808 VDPAU: Created 2 output surfaces.
2010-09-23 07:24:40.808 VDPAU: Version 1
2010-09-23 07:24:40.808 VDPAU: Information NVIDIA VDPAU Driver Shared Library  256.44  Thu Jul 29 01:59:12 PDT 2010
2010-09-23 07:24:40.808 VDPAU: Created VDPAU render device 1366x768
2010-09-23 07:24:40.843 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-09-23 07:24:40.844 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 07:24:40.927 Realtime priority would require SUID as root.
2010-09-23 07:24:40.927 TV: Changing from None to WatchingPreRecorded
2010-09-23 07:24:40.932 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 07:28:02.436 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 07:28:02.436 Using runtime prefix = /usr
2010-09-23 07:28:02.437 Using configuration directory = /home/john/.mythtv
Starting mythfrontend.real..
2010-09-23 07:28:02.783 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 07:28:02.783 Using runtime prefix = /usr
2010-09-23 07:28:02.783 Using configuration directory = /home/john/.mythtv
2010-09-23 07:28:02.784 MediaRenderer::HttpServer Create Error
2010-09-23 07:28:02.785 Empty LocalHostName.
2010-09-23 07:28:02.785 Using localhost value of jpc-desktop
2010-09-23 07:28:02.788 New DB connection, total: 1
2010-09-23 07:28:02.790 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:28:02.791 Closing DB connection named 'DBManager0'
2010-09-23 07:28:02.802 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 07:28:02.803 DPMS is active.
2010-09-23 07:28:02.804 Primary screen: 1.
2010-09-23 07:28:02.804 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:28:02.805 Using screen 1, 1366x768 at 0,0
2010-09-23 07:28:02.853 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 07:28:02.876 MythUI Image Cache size set to 20971520 bytes
2010-09-23 07:28:02.910 AudioPulseUtil: Suspend Success
2010-09-23 07:28:02.910 Enabled verbose msgs:  important general
2010-09-23 07:28:02.916 Primary screen: 1.
2010-09-23 07:28:02.917 Using screen 1, 1366x768 at 0,0
2010-09-23 07:28:02.917 Using theme base resolution of 1280x720
2010-09-23 07:28:02.922 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 07:28:02.922 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 07:28:02.950 Using Frameless Window
2010-09-23 07:28:02.950 Using Full Screen Window
2010-09-23 07:28:03.111 Using the Qt painter
2010-09-23 07:28:03.140 Empty LocalHostName.
2010-09-23 07:28:03.141 Using localhost value of jpc-desktop
2010-09-23 07:28:03.152 New DB connection, total: 1
2010-09-23 07:28:03.159 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:28:03.160 Closing DB connection named 'DBManager0'
2010-09-23 07:28:03.177 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 07:28:03.178 DPMS is active.
2010-09-23 07:28:03.180 Primary screen: 1.
2010-09-23 07:28:03.181 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:28:03.182 Using screen 1, 1366x768 at 0,0
2010-09-23 07:28:03.243 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 07:28:03.248 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 07:28:03.252 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 07:28:03.256 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 07:28:03.262 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 07:28:03.267 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 07:28:03.267 MythUI Image Cache size set to 20971520 bytes
2010-09-23 07:28:03.282 AudioPulseUtil: Suspend Success
2010-09-23 07:28:03.283 Enabled verbose msgs:  important general
2010-09-23 07:28:03.286 Primary screen: 1.
2010-09-23 07:28:03.286 Using screen 1, 1366x768 at 0,0
2010-09-23 07:28:03.287 Using theme base resolution of 1280x720
2010-09-23 07:28:03.290 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 07:28:03.290 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 07:28:03.312 Using Frameless Window
2010-09-23 07:28:03.312 Using Full Screen Window
2010-09-23 07:28:03.449 Using the Qt painter
2010-09-23 07:28:03.579 Registering Internal as a media playback plugin.
2010-09-23 07:28:03.585 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 07:28:03.589 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 07:28:03.594 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 07:28:03.594 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 07:28:03.598 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 07:28:03.600 Cannot load language en_us for module mytharchive
2010-09-23 07:28:03.602 Cannot load language en_us for module mythbrowser
2010-09-23 07:28:03.604 Registering WebBrowser as a media playback plugin.
2010-09-23 07:28:03.604 Cannot load language en_us for module mythbrowser
2010-09-23 07:28:03.619 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.619 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.619 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.620 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.620 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.621 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.621 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 07:28:03.621 Cannot load language en_us for module mythgallery
2010-09-23 07:28:03.624 Cannot load language en_us for module mythgame
2010-09-23 07:28:03.626 Cannot load language en_us for module mythmovies
2010-09-23 07:28:03.637 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 07:28:03.680 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 07:28:03.687 Cannot load language en_us for module mythmusic
2010-09-23 07:28:03.695 Cannot load language en_us for module mythnews
2010-09-23 07:28:03.706 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 07:28:03.738 Cannot load language en_us for module mythvideo
2010-09-23 07:28:03.748 Cannot load language en_us for module mythweather
2010-09-23 07:28:03.750 NetworkControl: Listening for remote connections on port 6546
2010-09-23 07:28:03.752 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 07:28:03.810 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 07:28:03.811 Searching CD statistically - file by file!
2010-09-23 07:28:03.824 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 07:28:03.825 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 07:28:03.903 Registering Internal as a media playback plugin.
2010-09-23 07:28:03.912 Cannot load language en_us for module mytharchive
2010-09-23 07:28:03.913 Cannot load language en_us for module mythbrowser
2010-09-23 07:28:03.914 Registering WebBrowser as a media playback plugin.
2010-09-23 07:28:03.914 Cannot load language en_us for module mythbrowser
2010-09-23 07:28:03.923 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.923 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.923 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.924 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.924 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.924 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:28:03.924 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 07:28:03.925 Cannot load language en_us for module mythgallery
2010-09-23 07:28:03.927 Cannot load language en_us for module mythgame
2010-09-23 07:28:03.928 Cannot load language en_us for module mythmovies
2010-09-23 07:28:03.937 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 07:28:03.949 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 07:28:03.950 Cannot load language en_us for module mythmusic
2010-09-23 07:28:03.953 Cannot load language en_us for module mythnews
2010-09-23 07:28:03.956 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 07:28:03.963 Cannot load language en_us for module mythvideo
2010-09-23 07:28:03.966 Cannot load language en_us for module mythweather
2010-09-23 07:28:03.966 NetworkControl failed to bind to port 6546.
2010-09-23 07:28:03.967 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 07:28:03.975 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 07:28:03.975 Searching CD statistically - file by file!
2010-09-23 07:28:04.028 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 07:28:04.037 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 07:28:04.134 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 07:28:04.134 Using protocol version 23056
2010-09-23 07:28:04.279 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 07:28:04.279 Using protocol version 23056
2010-09-23 07:28:06.804 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-09-23 07:28:08.007 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-09-23 07:28:11.403 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2010-09-23 07:28:15.780 Received a remote 'Clear Cache' request
2010-09-23 07:28:15.780 Received a remote 'Clear Cache' request
2010-09-23 07:28:19.683 Received a remote 'Clear Cache' request
2010-09-23 07:28:19.683 Received a remote 'Clear Cache' request
2010-09-23 07:28:32.747 Received a remote 'Clear Cache' request
2010-09-23 07:28:32.747 Received a remote 'Clear Cache' request
2010-09-23 07:28:36.915 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 07:28:37.328 New DB connection, total: 2
2010-09-23 07:28:37.329 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:28:37.330 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 07:28:38.580 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 07:28:38.757 AFD: Opened codec 0xa65e92b0, id(H264) type(Video)
2010-09-23 07:28:38.757 AFD: codec AAC has 2 channels
2010-09-23 07:28:38.757 AFD: Opened codec 0xa67e5ad0, id(AAC) type(Audio)
2010-09-23 07:28:38.828 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 07:28:38.829 Opening ALSA audio device 'default'.
2010-09-23 07:28:38.892 mixer unable to find control Master 1
2010-09-23 07:28:38.946 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-09-23 07:28:39.080 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 07:28:39.589 Realtime priority would require SUID as root.
2010-09-23 07:28:39.591 TV: Changing from None to WatchingPreRecorded
2010-09-23 07:28:39.614 OpenGLVideoSync()
2010-09-23 07:28:40.935 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 07:28:41.876 New DB connection, total: 2
2010-09-23 07:28:41.877 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:28:41.878 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 07:28:46.828 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 07:28:46.986 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.987 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.987 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.988 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.988 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.989 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.990 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.991 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.991 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.991 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.991 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.991 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.991 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:46.992 [mpeg2video @ 0xb663e960]mpeg_decode_postinit() failure
2010-09-23 07:28:47.039 AFD: Opened codec 0x93ad4d0, id(MPEG2VIDEO) type(Video)
2010-09-23 07:28:47.040 AFD: codec AC3 has 6 channels
2010-09-23 07:28:47.041 AFD: Opened codec 0x93adc20, id(AC3) type(Audio)
2010-09-23 07:28:47.041 AFD: codec AC3 has 2 channels
2010-09-23 07:28:47.042 AFD: Opened codec 0x93a6640, id(AC3) type(Audio)
2010-09-23 07:28:47.120 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 07:28:47.121 Opening ALSA audio device 'default'.
2010-09-23 07:28:47.175 mixer unable to find control Master 1
2010-09-23 07:28:47.354 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-09-23 07:28:47.460 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 07:28:47.546 Realtime priority would require SUID as root.
2010-09-23 07:28:47.548 TV: Changing from None to WatchingPreRecorded
2010-09-23 07:28:47.554 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 07:33:55.241 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 07:33:55.241 Using runtime prefix = /usr
2010-09-23 07:33:55.241 Using configuration directory = /home/john/.mythtv
2010-09-23 07:33:55.792 Empty LocalHostName.
2010-09-23 07:33:55.792 Using localhost value of jpc-desktop
2010-09-23 07:33:55.819 New DB connection, total: 1
2010-09-23 07:33:55.827 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:33:55.828 Closing DB connection named 'DBManager0'
2010-09-23 07:33:55.845 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 07:33:55.846 DPMS is active.
2010-09-23 07:33:55.848 Primary screen: 1.
2010-09-23 07:33:55.849 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:33:55.850 Using screen 1, 1366x768 at 0,0
2010-09-23 07:33:55.919 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 07:33:55.933 MythUI Image Cache size set to 20971520 bytes
2010-09-23 07:33:55.997 AudioPulseUtil: Suspend Success
2010-09-23 07:33:55.997 Enabled verbose msgs:  important general
2010-09-23 07:33:56.001 Primary screen: 1.
2010-09-23 07:33:56.001 Using screen 1, 1366x768 at 0,0
2010-09-23 07:33:56.002 Using theme base resolution of 1280x720
2010-09-23 07:33:56.009 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 07:33:56.009 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 07:33:56.048 Using Frameless Window
2010-09-23 07:33:56.048 Using Full Screen Window
2010-09-23 07:33:56.191 Using the Qt painter
2010-09-23 07:33:56.312 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 07:33:56.328 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 07:33:56.335 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 07:33:56.335 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 07:33:56.338 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 07:33:56.681 Registering Internal as a media playback plugin.
2010-09-23 07:33:56.711 Cannot load language en_us for module mytharchive
2010-09-23 07:33:56.715 Cannot load language en_us for module mythbrowser
2010-09-23 07:33:56.719 Registering WebBrowser as a media playback plugin.
2010-09-23 07:33:56.719 Cannot load language en_us for module mythbrowser
2010-09-23 07:33:56.755 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:33:56.755 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:33:56.756 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:33:56.758 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:33:56.759 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:33:56.759 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:33:56.760 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 07:33:56.760 Cannot load language en_us for module mythgallery
2010-09-23 07:33:56.763 Cannot load language en_us for module mythgame
2010-09-23 07:33:56.765 Cannot load language en_us for module mythmovies
2010-09-23 07:33:56.774 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 07:33:56.794 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 07:33:56.796 Cannot load language en_us for module mythmusic
2010-09-23 07:33:56.799 Cannot load language en_us for module mythnews
2010-09-23 07:33:56.804 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 07:33:56.827 Cannot load language en_us for module mythvideo
2010-09-23 07:33:56.837 Cannot load language en_us for module mythweather
2010-09-23 07:33:56.840 NetworkControl: Listening for remote connections on port 6546
2010-09-23 07:33:56.842 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 07:33:56.899 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 07:33:56.899 Searching CD statistically - file by file!
2010-09-23 07:33:56.906 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 07:33:56.907 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 07:33:57.184 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 07:33:57.185 Using protocol version 23056
2010-09-23 07:33:58.671 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 07:33:59.552 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-09-23 07:33:59.719 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@jpc-desktop/media/mythtv/videos/)
2010-09-23 07:33:59.727 New DB connection, total: 2
2010-09-23 07:33:59.728 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:34:01.559 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-09-23 07:34:02.396 TV: Attempting to change from None to WatchingVideo
2010-09-23 07:34:02.983 AFD: Opened codec 0x8d0d720, id(H264) type(Video)
2010-09-23 07:34:02.983 AFD: codec AAC has 2 channels
2010-09-23 07:34:02.983 AFD: Opened codec 0x8d0dda0, id(AAC) type(Audio)
2010-09-23 07:34:02.983 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2010-09-23 07:34:03.056 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 07:34:03.057 Opening ALSA audio device 'default'.
2010-09-23 07:34:03.112 mixer unable to find control Master 1
2010-09-23 07:34:03.158 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-09-23 07:34:03.183 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 07:34:03.362 New DB connection, total: 3
2010-09-23 07:34:03.362 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:34:03.362 Realtime priority would require SUID as root.
2010-09-23 07:34:03.363 TV: Changing from None to WatchingVideo
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 480
YadifDeint: Using existing thread.
2010-09-23 07:34:03.401 ScreenSaverX11Private: DPMS Deactivated 1
2010-09-23 07:34:03.402 OpenGLVideoSync()
Starting mythfrontend.real..
2010-09-23 07:47:58.991 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2010-09-23 07:47:58.992 Using runtime prefix = /usr
2010-09-23 07:47:58.992 Using configuration directory = /home/john/.mythtv
2010-09-23 07:47:59.676 Empty LocalHostName.
2010-09-23 07:47:59.676 Using localhost value of jpc-desktop
2010-09-23 07:47:59.681 New DB connection, total: 1
2010-09-23 07:47:59.683 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:47:59.684 Closing DB connection named 'DBManager0'
2010-09-23 07:47:59.693 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-23 07:47:59.694 DPMS is active.
2010-09-23 07:47:59.695 Primary screen: 1.
2010-09-23 07:47:59.695 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:47:59.696 Using screen 1, 1366x768 at 0,0
2010-09-23 07:47:59.749 Desktop video mode: 1366x768 59.641 Hz
2010-09-23 07:47:59.766 MythUI Image Cache size set to 20971520 bytes
2010-09-23 07:47:59.795 AudioPulseUtil: Suspend Success
2010-09-23 07:47:59.795 Enabled verbose msgs:  important general
2010-09-23 07:47:59.802 Primary screen: 1.
2010-09-23 07:47:59.802 Using screen 1, 1366x768 at 0,0
2010-09-23 07:47:59.803 Using theme base resolution of 1280x720
2010-09-23 07:47:59.811 LIRC: Successfully initialized '/dev/lircd' using '/home/john/.mythtv/lircrc' config
2010-09-23 07:47:59.811 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-09-23 07:47:59.848 Using Frameless Window
2010-09-23 07:47:59.849 Using Full Screen Window
2010-09-23 07:47:59.990 Using the Qt painter
2010-09-23 07:48:00.113 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-23 07:48:00.118 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-23 07:48:00.124 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-23 07:48:00.124 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-23 07:48:00.128 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-23 07:48:00.407 Registering Internal as a media playback plugin.
2010-09-23 07:48:00.451 Cannot load language en_us for module mytharchive
2010-09-23 07:48:00.455 Cannot load language en_us for module mythbrowser
2010-09-23 07:48:00.457 Registering WebBrowser as a media playback plugin.
2010-09-23 07:48:00.457 Cannot load language en_us for module mythbrowser
2010-09-23 07:48:00.477 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:48:00.477 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:48:00.478 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:48:00.479 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:48:00.479 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:48:00.479 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-23 07:48:00.479 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-23 07:48:00.480 Cannot load language en_us for module mythgallery
2010-09-23 07:48:00.484 Cannot load language en_us for module mythgame
2010-09-23 07:48:00.487 Cannot load language en_us for module mythmovies
2010-09-23 07:48:00.500 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-23 07:48:00.541 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-23 07:48:00.548 Cannot load language en_us for module mythmusic
2010-09-23 07:48:00.555 Cannot load language en_us for module mythnews
2010-09-23 07:48:00.566 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-23 07:48:00.609 Cannot load language en_us for module mythvideo
2010-09-23 07:48:00.619 Cannot load language en_us for module mythweather
2010-09-23 07:48:00.621 NetworkControl: Listening for remote connections on port 6546
2010-09-23 07:48:00.623 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-23 07:48:00.681 CD/DVD '/media/20100921-lucid' contained none of
            /VIDEO_TS, /.TOC.plist, /vcd or /svcd
2010-09-23 07:48:00.681 Searching CD statistically - file by file!
2010-09-23 07:48:00.685 Loading menu theme from /home/john/.mythtv/mainmenu.xml
2010-09-23 07:48:00.687 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-23 07:48:00.961 MythContext: Connecting to backend server: 192.168.0.244:6543 (try 1 of 1)
2010-09-23 07:48:00.962 Using protocol version 23056
2010-09-23 07:48:02.402 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-09-23 07:48:02.913 New DB connection, total: 2
2010-09-23 07:48:02.914 Connected to database 'mythconverg' at host: localhost
2010-09-23 07:48:02.917 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-09-23 07:48:09.891 TV: Attempting to change from None to WatchingPreRecorded
2010-09-23 07:48:10.026 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.026 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.027 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.027 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.028 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.028 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.029 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.029 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.030 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.030 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.031 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.031 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.032 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.032 [mpeg2video @ 0xb664d960]mpeg_decode_postinit() failure
2010-09-23 07:48:10.074 AFD: Opened codec 0x92ab010, id(MPEG2VIDEO) type(Video)
2010-09-23 07:48:10.074 AFD: codec AC3 has 6 channels
2010-09-23 07:48:10.075 AFD: Opened codec 0x9118d90, id(AC3) type(Audio)
2010-09-23 07:48:10.076 AFD: codec AC3 has 2 channels
2010-09-23 07:48:10.076 AFD: Opened codec 0x9119490, id(AC3) type(Audio)
2010-09-23 07:48:10.144 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-23 07:48:10.145 Opening ALSA audio device 'default'.
2010-09-23 07:48:10.200 mixer unable to find control Master 1
2010-09-23 07:48:10.317 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-09-23 07:48:10.428 OSD Theme Dimensions W: 1280 H: 720
2010-09-23 07:48:10.526 TV: Changing from None to WatchingPreRecorded
2010-09-23 07:48:10.527 Realtime priority would require SUID as root.
2010-09-23 07:48:10.529 OpenGLVideoSync()

```

---

### Post by mathog on 2010-09-23
> **LowSky said:**
> 
anyone know what is going wrong?


Not specifically.  

"Segmentation fault" tells you that some program tried to access memory it did not have access to.  Generally it is the result of a programming error, such as running off the end of an array or corrupting a memory pointer.  End users can't do much about these other than trying to configure the piece of software so it doesn't bumble into the bad piece of code.

---

### Post by LowSky on 2010-09-24
Well instead of hunting down the problem. I decided to just back up the database, backup my home directory, and then reinstalled Ubuntu (switching to AMD64 verison in the process).

I'm thinking the error was caused by a mythbuntu ppa update that may not have run correctly, but I have no idea. A 4 hour reinstall (installing tuner drivers, running mythfilldatabase, and installing all the other system programs) seemed a better idea than trying to hunt down code lines that code take even longer.

---

