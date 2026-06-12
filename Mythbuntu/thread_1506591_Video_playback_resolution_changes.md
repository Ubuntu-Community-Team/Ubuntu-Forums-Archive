---
title: "Video playback resolution changes"
date: 2010-06-10
forum: Mythbuntu
---

### Post by phroman on 2010-06-10
Hi all, when watching a backuped dvd of a tv series with 4 episodes on the disk, at the root menu the image scales too big for the tv screen. And when I try to navigate around the main menu, it doesn't highlight where the cursor is/should be, it is changing to each position because I can click and it plays but I can't actually see it highlighting my selection.  I checked it with VLC and all is fine, its just in mythtv frontend, mythvideo.

I restarted the frontend, went to play this video and exited, here's my frontend log.  There's various errors having to do with video in there but I don't know what any of them mean or if they're relevant.  

```
Starting mythfrontend.real..
2010-06-10 11:06:22.463 mythfrontend version: branches/release-0-23-fixes [25065] www.mythtv.org
2010-06-10 11:06:22.463 Using runtime prefix = /usr
2010-06-10 11:06:22.463 Using configuration directory = /home/joe/.mythtv
2010-06-10 11:06:23.152 Empty LocalHostName.
2010-06-10 11:06:23.153 Using localhost value of mythserver1
2010-06-10 11:06:23.158 New DB connection, total: 1
2010-06-10 11:06:23.159 Connected to database 'mythconverg' at host: localhost
2010-06-10 11:06:23.160 Closing DB connection named 'DBManager0'
2010-06-10 11:06:23.167 ScreenSaverX11Private: XScreenSaver support enabled
2010-06-10 11:06:23.168 DPMS is disabled.
2010-06-10 11:06:23.168 Primary screen: 0.
2010-06-10 11:06:23.169 Connected to database 'mythconverg' at host: localhost
2010-06-10 11:06:23.169 Using screen 0, 1920x1080 at 0,0
2010-06-10 11:06:23.175 Desktop video mode: 1920x1080 60.0024 Hz
2010-06-10 11:06:23.183 MythUI Image Cache size set to 20971520 bytes
2010-06-10 11:06:23.193 Enabled verbose msgs:  important general
2010-06-10 11:06:23.195 Primary screen: 0.
2010-06-10 11:06:23.196 Using screen 0, 1920x1080 at 0,0
2010-06-10 11:06:23.196 Using theme base resolution of 1280x720
2010-06-10 11:06:23.199 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2010-06-10 11:06:23.199 JoystickMenuThread Error: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2010-06-10 11:06:23.219 Using Frameless Window
2010-06-10 11:06:23.219 Using Full Screen Window
2010-06-10 11:06:23.355 Using the Qt painter
2010-06-10 11:06:23.422 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-06-10 11:06:23.431 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-06-10 11:06:23.437 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-06-10 11:06:23.437 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-06-10 11:06:23.449 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-10 11:06:23.699 Registering Internal as a media playback plugin.
2010-06-10 11:06:23.714 Cannot load language en_us for module mytharchive
2010-06-10 11:06:23.731 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-10 11:06:23.731 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-10 11:06:23.731 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-10 11:06:23.732 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-06-10 11:06:23.732 Cannot load language en_us for module mythgallery
2010-06-10 11:06:23.734 Cannot load language en_us for module mythmovies
2010-06-10 11:06:23.746 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-06-10 11:06:23.765 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-06-10 11:06:23.768 Cannot load language en_us for module mythmusic
2010-06-10 11:06:23.773 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-06-10 11:06:23.788 Cannot load language en_us for module mythvideo
2010-06-10 11:06:23.794 Starting update of NDFD-18_Hour
2010-06-10 11:06:23.794 NDFD-18_Hour recently updated, skipping.
2010-06-10 11:06:23.794 Starting update of NDFD-6_day
2010-06-10 11:06:23.794 NDFD-6_day recently updated, skipping.
2010-06-10 11:06:23.795 Starting update of NWS-XML
2010-06-10 11:06:23.795 NWS-XML recently updated, skipping.
2010-06-10 11:06:23.795 Cannot load language en_us for module mythweather
2010-06-10 11:06:23.796 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-06-10 11:06:23.836 Loading menu theme from /usr/share/mythtv/themes/customized defaultmenu//mainmenu.xml
2010-06-10 11:06:23.836 Found mainmenu.xml for theme 'Mythbuntu'
2010-06-10 11:06:24.474 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-10 11:06:24.475 Using protocol version 56
2010-06-10 11:06:29.720 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-06-10 11:06:29.889 MythVideo::ScanVideoDirectory Scanning (/disk2/movies1)
2010-06-10 11:06:29.892 New DB connection, total: 2
2010-06-10 11:06:29.892 Connected to database 'mythconverg' at host: localhost
2010-06-10 11:06:32.242 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000150
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00019bcf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001fa74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001ba46e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001ba472
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0027ff92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0027ff96
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0034a409
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0034a40d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00353997
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0035399b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00353ac4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00353ac8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003de6d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003de6d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003e08d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003e08d8
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: BATTLESTAR_GALACTICA
libdvdnav: DVD Serial Number: 335274db
libdvdnav: DVD Title (Alternative): S2_D1_R0
libdvdnav: Unable to find map file '/home/joe/.dvdnav/BATTLESTAR_GALACTICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2010-06-10 11:06:33.053 Opened DVD device at /disk2/movies1/BSG S2 D1.iso
2010-06-10 11:06:33.053 There are 16 titles on the disk
2010-06-10 11:06:33.053 Title 0 has 0 parts.
2010-06-10 11:06:33.053 Title 1 has 5 parts.
2010-06-10 11:06:33.053 Title 2 has 5 parts.
2010-06-10 11:06:33.053 Title 3 has 9 parts.
2010-06-10 11:06:33.053 Title 4 has 5 parts.
2010-06-10 11:06:33.053 Title 5 has 5 parts.
2010-06-10 11:06:33.053 Title 6 has 5 parts.
2010-06-10 11:06:33.053 Title 7 has 5 parts.
2010-06-10 11:06:33.053 Title 8 has 2 parts.
2010-06-10 11:06:33.053 Title 9 has 2 parts.
2010-06-10 11:06:33.053 Title 10 has 7 parts.
2010-06-10 11:06:33.053 Title 11 has 6 parts.
2010-06-10 11:06:33.054 Title 12 has 2 parts.
2010-06-10 11:06:33.054 Title 13 has 3 parts.
2010-06-10 11:06:33.054 Title 14 has 2 parts.
2010-06-10 11:06:33.054 Title 15 has 2 parts.
2010-06-10 11:06:33.129 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000150
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00019bcf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001fa74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001ba46e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001ba472
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0027ff92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0027ff96
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0034a409
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0034a40d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00353997
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0035399b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00353ac4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00353ac8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003de6d1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003de6d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003e08d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003e08d8
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: BATTLESTAR_GALACTICA
libdvdnav: DVD Serial Number: 335274db
libdvdnav: DVD Title (Alternative): S2_D1_R0
libdvdnav: Unable to find map file '/home/joe/.dvdnav/BATTLESTAR_GALACTICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2010-06-10 11:06:33.130 Opened DVD device at /disk2/movies1/BSG S2 D1.iso
2010-06-10 11:06:33.130 There are 16 titles on the disk
2010-06-10 11:06:33.130 Title 0 has 0 parts.
2010-06-10 11:06:33.131 Title 1 has 5 parts.
2010-06-10 11:06:33.131 Title 2 has 5 parts.
2010-06-10 11:06:33.131 Title 3 has 9 parts.
2010-06-10 11:06:33.131 Title 4 has 5 parts.
2010-06-10 11:06:33.131 Title 5 has 5 parts.
2010-06-10 11:06:33.131 Title 6 has 5 parts.
2010-06-10 11:06:33.131 Title 7 has 5 parts.
2010-06-10 11:06:33.131 Title 8 has 2 parts.
2010-06-10 11:06:33.131 Title 9 has 2 parts.
2010-06-10 11:06:33.131 Title 10 has 7 parts.
2010-06-10 11:06:33.131 Title 11 has 6 parts.
2010-06-10 11:06:33.131 Title 12 has 2 parts.
2010-06-10 11:06:33.131 Title 13 has 3 parts.
2010-06-10 11:06:33.131 Title 14 has 2 parts.
2010-06-10 11:06:33.131 Title 15 has 2 parts.
2010-06-10 11:06:33.223 AFD: Opened codec 0x8e13df0, id(MPEG2VIDEO) type(Video)
2010-06-10 11:06:33.224 NVP(0): Disabling Audio, params(-1,-1,-1)
2010-06-10 11:06:33.236 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-06-10 11:06:33.258 OSD Theme Dimensions W: 640 H: 480
2010-06-10 11:06:33.291 TV: Changing from None to WatchingDVD
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2010-06-10 11:06:33.295 Video timing method: USleep with busy wait
2010-06-10 11:06:33.334 AFD: Warning, video codec 0x8e13df0 id(MPEG2VIDEO) type (Video) already open.
2010-06-10 11:06:33.366 AFD: codec AC3 has 0 channels
2010-06-10 11:06:33.367 AFD: Opened codec 0xa3d58a20, id(AC3) type(Audio)
2010-06-10 11:06:33.376 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-06-10 11:06:33.376 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-06-10 11:06:33.407 mixer unable to find control Master 1
2010-06-10 11:06:33.407 NVP(0): Enabling Audio
2010-06-10 11:06:33.410 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-06-10 11:06:33.411 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-06-10 11:06:33.442 mixer unable to find control Master 1
2010-06-10 11:06:55.757 NVP(0): Disabling Audio, params(-1,-1,-1)
2010-06-10 11:07:02.822 AFD: Warning, video codec 0x8e13df0 id(MPEG2VIDEO) type (Video) already open.
2010-06-10 11:07:02.839 AFD: codec AC3 has 0 channels
2010-06-10 11:07:02.840 AFD: Opened codec 0x9547e80, id(AC3) type(Audio)
2010-06-10 11:07:02.842 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 1)
2010-06-10 11:07:02.842 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-06-10 11:07:02.874 mixer unable to find control Master 1
2010-06-10 11:07:02.874 NVP(0): Enabling Audio
2010-06-10 11:09:12.739 NVP(0): Disabling Audio, params(-1,-1,-1)
2010-06-10 11:09:27.720 AFD: Warning, video codec 0x8e13df0 id(MPEG2VIDEO) type (Video) already open.
2010-06-10 11:09:27.725 AFD: Opened codec 0x9895d30, id(DVD_SUBTITLE) type(Subtitle)
2010-06-10 11:09:27.726 [mpeg2video @ 0x4c6940]ac-tex damaged at 26 0
2010-06-10 11:09:27.726 [mpeg2video @ 0x4c6940]Warning MVs not available
2010-06-10 11:09:27.728 [mpeg2video @ 0x4c6940]ac-tex damaged at 26 0
2010-06-10 11:09:27.728 [mpeg2video @ 0x4c6940]Warning MVs not available
2010-06-10 11:09:27.733 AFD: Warning, video codec 0x8e13df0 id(MPEG2VIDEO) type (Video) already open.
2010-06-10 11:09:27.734 AFD: Opened codec 0x965ada0, id(DVD_SUBTITLE) type(Subtitle)
2010-06-10 11:09:27.752 AFD: Warning, video codec 0x8e13df0 id(MPEG2VIDEO) type (Video) already open.
2010-06-10 11:09:27.752 AFD: codec AC3 has 0 channels
2010-06-10 11:09:27.752 AFD: Opened codec 0x94ddcc0, id(AC3) type(Audio)
2010-06-10 11:09:27.755 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 1)
2010-06-10 11:09:27.755 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-06-10 11:09:27.786 mixer unable to find control Master 1
2010-06-10 11:09:27.786 NVP(0): Enabling Audio
2010-06-10 11:15:04.876 TV: Attempting to change from WatchingDVD to None
2010-06-10 11:15:04.876 TV: Changing from WatchingDVD to None
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000dfbf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000e52d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00014faf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002a711e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002cd9a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002e1a7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00395f53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00398150
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: ASDF
libdvdnav: DVD Serial Number: 37597EC1
libdvdnav: DVD Title (Alternative): ASDF
libdvdnav: Unable to find map file '/home/joe/.dvdnav/ASDF.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2010-06-10 11:15:05.946 Opened DVD device at /disk2/movies1/Battlestar Galactica Razor.iso
2010-06-10 11:15:05.946 There are 11 titles on the disk
2010-06-10 11:15:05.946 Title 0 has 0 parts.
2010-06-10 11:15:05.946 Title 1 has 21 parts.
2010-06-10 11:15:05.946 Title 2 has 21 parts.
2010-06-10 11:15:05.946 Title 3 has 2 parts.
2010-06-10 11:15:05.946 Title 4 has 2 parts.
2010-06-10 11:15:05.946 Title 5 has 3 parts.
2010-06-10 11:15:05.946 Title 6 has 2 parts.
2010-06-10 11:15:05.946 Title 7 has 2 parts.
2010-06-10 11:15:05.946 Title 8 has 2 parts.
2010-06-10 11:15:05.946 Title 9 has 8 parts.
2010-06-10 11:15:05.946 Title 10 has 2 parts.
2010-06-10 11:15:06.012 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000dfbf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000e52d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00014faf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002a711e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002cd9a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002e1a7a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00395f53
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00398150
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: ASDF
libdvdnav: DVD Serial Number: 37597EC1
libdvdnav: DVD Title (Alternative): ASDF
libdvdnav: Unable to find map file '/home/joe/.dvdnav/ASDF.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2010-06-10 11:15:06.013 Opened DVD device at /disk2/movies1/Battlestar Galactica Razor.iso
2010-06-10 11:15:06.013 There are 11 titles on the disk
2010-06-10 11:15:06.013 Title 0 has 0 parts.
2010-06-10 11:15:06.013 Title 1 has 21 parts.
2010-06-10 11:15:06.013 Title 2 has 21 parts.
2010-06-10 11:15:06.013 Title 3 has 2 parts.
2010-06-10 11:15:06.013 Title 4 has 2 parts.
2010-06-10 11:15:06.013 Title 5 has 3 parts.
2010-06-10 11:15:06.013 Title 6 has 2 parts.
2010-06-10 11:15:06.013 Title 7 has 2 parts.
2010-06-10 11:15:06.013 Title 8 has 2 parts.
2010-06-10 11:15:06.013 Title 9 has 8 parts.
2010-06-10 11:15:06.013 Title 10 has 2 parts.
2010-06-10 11:15:06.084 AFD: Opened codec 0xa3cfe3a0, id(MPEG2VIDEO) type(Video)
2010-06-10 11:15:06.084 NVP(1): Disabling Audio, params(-1,-1,-1)
2010-06-10 11:15:06.088 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-06-10 11:15:06.105 OSD Theme Dimensions W: 640 H: 480
2010-06-10 11:15:06.130 TV: Changing from None to WatchingDVD
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2010-06-10 11:15:06.133 Video timing method: USleep with busy wait
2010-06-10 11:15:09.785 TV: Attempting to change from WatchingDVD to None
2010-06-10 11:15:09.786 TV: Changing from WatchingDVD to None
2010-06-10 11:15:13.404 Deleting UPnP client...
```


Any ideas?  Its a small damper on the GAF and any help is very appreciated, thank you.

---

