---
title: "exit error code 136"
date: 2011-06-13
forum: Mythbuntu
---

### Post by AxelBlade on 2011-06-13
Hello everybody, I've just installed mythbuntu, when I try to play music from the cd or use the weather plugin , the front crashes and give me the following error " the front end closed unexpectedly (exit code 136)"
what is the problem.

Thanks in advance.

---

### Post by tgm4883 on 2011-06-13
> **AxelBlade said:**
> Hello everybody, I've just installed mythbuntu, when I try to play music from the cd or use the weather plugin , the front crashes and give me the following error " the front end closed unexpectedly (exit code 136)"
what is the problem.

Thanks in advance.

Exit code 136 means jack to me. You will need to post your mythfrontend log from /var/log/mythtv/

---

### Post by AxelBlade on 2011-06-18
> **tgm4883 said:**
> Exit code 136 means jack to me. You will need to post your mythfrontend log from /var/log/mythtv/

below you can find the log from mythfrontend
Starting mythfrontend.real..
2011-06-12 22:39:28.726 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-12 22:39:28.726 Using runtime prefix = /usr
2011-06-12 22:39:28.726 Using configuration directory = /home/crhome/.mythtv
2011-06-12 22:39:28.726 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-12 22:39:29.267 Empty LocalHostName.
2011-06-12 22:39:29.267 Using localhost value of crhome-htpc
2011-06-12 22:39:29.270 New DB connection, total: 1
2011-06-12 22:39:29.272 Connected to database 'mythconverg' at host: localhost
2011-06-12 22:39:29.275 Closing DB connection named 'DBManager0'
2011-06-12 22:39:29.276 Connected to database 'mythconverg' at host: localhost
2011-06-12 22:39:29.276 Current locale EN_US
2011-06-12 22:39:29.276 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-12 22:39:29.481 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-12 22:39:29.481 DPMS is active.
2011-06-12 22:39:29.510 Desktop video mode: 1360x768 60.015 Hz
2011-06-12 22:39:30.082 Enabled verbose msgs:  important general
2011-06-12 22:39:30.096 Loading en_us translation for module mythfrontend
2011-06-12 22:39:30.097 MythUIHelper, Warning: No theme dir: '/usr/share/mythtv/themes/Mythbuntu'
2011-06-12 22:39:30.111 Could not find theme: Mythbuntu - Switching to Terra
2011-06-12 22:39:30.157 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-12 22:39:30.157 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-12 22:39:30.211 Using Frameless Window
2011-06-12 22:39:30.211 Using Full Screen Window
2011-06-12 22:39:30.218 Using the Qt painter
2011-06-12 22:39:30.729 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-12 22:39:31.354 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-12 22:39:31.354 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-12 22:39:31.387 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-12 22:39:31.387 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-12 22:39:31.491 Writing settings file /home/crhome/.mythtv/mysql.txt
2011-06-12 22:39:31.491 Closing DB connection named 'DBManager0'
2011-06-12 22:39:31.491 Connected to database 'mythconverg' at host: localhost
2011-06-12 22:39:31.567 Registering Internal as a media playback plugin.
2011-06-12 22:39:31.589 Loading en_us translation for module mythweather
2011-06-12 22:39:31.593 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-12 22:39:31.593 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-12 22:39:31.593 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-12 22:39:31.709 Found mainmenu.xml for theme 'Terra'
2011-06-12 22:39:32.065 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-12 22:39:32.072 Using protocol version 63
2011-06-12 22:40:17.764 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-12 22:40:17.764 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-12 22:40:17.765 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-12 22:40:17.765 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-12 22:40:37.169 Received a remote 'Clear Cache' request
2011-06-12 22:40:38.463 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-12 22:40:38.463 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-12 22:40:38.464 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-12 22:40:38.464 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-12 22:40:53.733 Received a remote 'Clear Cache' request
2011-06-12 22:40:53.795 Using Frameless Window
2011-06-12 22:40:53.795 Using Full Screen Window
2011-06-12 22:40:53.808 Using the Qt painter
2011-06-12 22:40:54.007 Found mainmenu.xml for theme 'Terra'
2011-06-12 22:41:06.732 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-12 22:41:06.732 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-12 22:41:06.733 Received a remote 'Clear Cache' request
2011-06-12 22:41:06.733 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-12 22:41:06.733 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-12 22:41:12.181 Using Frameless Window
2011-06-12 22:41:12.181 Using Full Screen Window
2011-06-12 22:41:12.191 Using the Qt painter
2011-06-12 22:41:12.389 Found mainmenu.xml for theme 'Terra'
2011-06-12 22:41:32.685 Received a remote 'Clear Cache' request
2011-06-12 22:41:32.685 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-12 22:41:32.685 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-12 22:41:32.686 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-12 22:41:32.686 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-12 22:41:43.918 Using Frameless Window
2011-06-12 22:41:43.918 Using Full Screen Window
2011-06-12 22:41:43.925 Using the Qt painter
2011-06-12 22:41:44.091 Found mainmenu.xml for theme 'Terra'
2011-06-12 22:41:47.103 PlaybackBox Error: SortedList is Empty
2011-06-12 22:41:47.202 PlaybackBox Error: SortedList is Empty
2011-06-12 22:41:56.362 Deleting UPnP client...
Starting mythfrontend.real..
2011-06-13 07:32:28.737 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 07:32:28.737 Using runtime prefix = /usr
2011-06-13 07:32:28.738 Using configuration directory = /home/crhome/.mythtv
2011-06-13 07:32:28.757 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 07:32:29.300 Empty LocalHostName.
2011-06-13 07:32:29.300 Using localhost value of crhome-htpc
2011-06-13 07:32:29.304 New DB connection, total: 1
2011-06-13 07:32:29.305 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:32:29.309 Closing DB connection named 'DBManager0'
2011-06-13 07:32:29.309 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:32:29.310 Current locale EN_US
2011-06-13 07:32:29.310 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 07:32:29.514 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 07:32:29.515 DPMS is active.
2011-06-13 07:32:29.557 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 07:32:30.132 Enabled verbose msgs:  important general
2011-06-13 07:32:30.160 Loading en_us translation for module mythfrontend
2011-06-13 07:32:30.190 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 07:32:30.190 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 07:32:30.241 Using Frameless Window
2011-06-13 07:32:30.241 Using Full Screen Window
2011-06-13 07:32:30.382 Using the Qt painter
2011-06-13 07:32:30.933 New DB connection, total: 2
2011-06-13 07:32:30.933 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:32:30.934 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 07:32:31.577 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 07:32:31.577 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 07:32:31.607 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 07:32:31.607 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 07:32:31.747 Registering Internal as a media playback plugin.
2011-06-13 07:32:31.771 Loading en_us translation for module mythweather
2011-06-13 07:32:31.775 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:32:31.775 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:32:31.775 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:32:32.824 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 07:32:32.861 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 07:32:32.871 Using protocol version 63
2011-06-13 07:32:52.302 PlaybackBox Error: SortedList is Empty
2011-06-13 07:32:52.403 PlaybackBox Error: SortedList is Empty
2011-06-13 07:34:43.975 Received a remote 'Clear Cache' request
2011-06-13 07:34:52.259 Received a remote 'Clear Cache' request
2011-06-13 07:35:28.066 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 07:35:28.066 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 07:35:28.067 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 07:35:28.067 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 07:35:57.148 Received a remote 'Clear Cache' request
2011-06-13 07:36:23.152 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2011-06-13 07:54:33.519 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 07:54:33.519 Using runtime prefix = /usr
2011-06-13 07:54:33.519 Using configuration directory = /home/crhome/.mythtv
2011-06-13 07:54:33.520 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 07:54:34.206 Empty LocalHostName.
2011-06-13 07:54:34.206 Using localhost value of crhome-htpc
2011-06-13 07:54:34.212 New DB connection, total: 1
2011-06-13 07:54:34.215 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:54:34.221 Closing DB connection named 'DBManager0'
2011-06-13 07:54:34.221 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:54:34.222 Current locale EN_US
2011-06-13 07:54:34.222 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 07:54:34.431 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 07:54:34.432 DPMS is active.
2011-06-13 07:54:34.447 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 07:54:35.035 Enabled verbose msgs:  important general
2011-06-13 07:54:35.036 Loading en_us translation for module mythfrontend
2011-06-13 07:54:35.041 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 07:54:35.041 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 07:54:35.065 Using Frameless Window
2011-06-13 07:54:35.065 Using Full Screen Window
2011-06-13 07:54:35.117 Using the Qt painter
2011-06-13 07:54:35.250 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 07:54:35.262 New DB connection, total: 2
2011-06-13 07:54:35.262 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:54:35.308 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 07:54:35.308 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 07:54:35.309 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 07:54:35.309 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 07:54:35.407 Registering Internal as a media playback plugin.
2011-06-13 07:54:35.423 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:54:35.423 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:54:35.423 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:54:35.424 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 07:54:35.424 Loading en_us translation for module mythgallery
2011-06-13 07:54:35.457 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 07:54:35.466 Loading en_us translation for module mythvideo
2011-06-13 07:54:35.469 Loading en_us translation for module mythweather
2011-06-13 07:54:35.641 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 07:54:35.676 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 07:54:35.677 Using protocol version 63
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DEVIL
libdvdnav: DVD Serial Number: 3D9BBCA8C2644357
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/crhome/.dvdnav/DEVIL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2011-06-13 07:54:49.932 Opened DVD device at /dev/dvd
2011-06-13 07:54:49.932 There are 6 titles on the disk
2011-06-13 07:54:49.932 DVDRB: Title 1 has 21 parts.
2011-06-13 07:54:49.932 DVDRB: Title 2 has 2 parts.
2011-06-13 07:54:49.932 DVDRB: Title 3 has 7 parts.
2011-06-13 07:54:49.932 DVDRB: Title 4 has 2 parts.
2011-06-13 07:54:49.932 DVDRB: Title 5 has 2 parts.
2011-06-13 07:54:49.932 DVDRB: Title 6 has 2 parts.
2011-06-13 07:54:50.096 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DEVIL
libdvdnav: DVD Serial Number: 3D9BBCA8C2644357
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/crhome/.dvdnav/DEVIL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2011-06-13 07:54:50.118 Opened DVD device at /dev/dvd
2011-06-13 07:54:50.118 There are 6 titles on the disk
2011-06-13 07:54:50.118 DVDRB: Title 1 has 21 parts.
2011-06-13 07:54:50.118 DVDRB: Title 2 has 2 parts.
2011-06-13 07:54:50.118 DVDRB: Title 3 has 7 parts.
2011-06-13 07:54:50.118 DVDRB: Title 4 has 2 parts.
2011-06-13 07:54:50.118 DVDRB: Title 5 has 2 parts.
2011-06-13 07:54:50.118 DVDRB: Title 6 has 2 parts.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000014a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000006ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0021c54a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0021c562
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
2011-06-13 07:54:50.368 DVDRB: Resetting DVD device.
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2011-06-13 07:54:50.372 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-13 07:54:50.372 AFD: Opened codec 0x2ba0cd0, id(MPEG2VIDEO) type(Video)
2011-06-13 07:54:50.372 AFD: codec AC3 has 6 channels
2011-06-13 07:54:50.372 AFD: Opened codec 0x2bad030, id(AC3) type(Audio)
2011-06-13 07:54:50.392 AO: Opening audio device 'default' ch 2(6) sr 48000 sf 32 bit floating point reenc 0
2011-06-13 07:54:50.393 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-06-13 07:54:50.416 ALSA, Error: no playback control PCM found on mixer device default
2011-06-13 07:54:50.416 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-06-13 07:54:50.416 AudioPlayer: Enabling Audio
2011-06-13 07:54:50.429 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-06-13 07:54:50.448 OSD: Base theme size: 1280x720
2011-06-13 07:54:50.448 OSD: Scaling factors: 0.5625x0.666667
2011-06-13 07:54:50.494 OSD: Base theme size: 1280x720
2011-06-13 07:54:50.494 OSD: Scaling factors: 0.5625x0.666667
2011-06-13 07:54:50.532 Player(0): Video timing method: DRM
2011-06-13 07:54:50.557 TV: Changing from None to WatchingDVD
2011-06-13 07:54:50.572 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 07:54:50.573 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 07:54:50.573 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 07:54:50.574 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 07:54:50.574 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 07:54:50.592 VideoOutput: Created YV12 OSD.
2011-06-13 07:54:51.048 ScreenSaverX11Private: DPMS Reactivated 1
2011-06-13 07:54:51.586 AudioPlayer: Disabling Audio, params(0,-1,-1)
2011-06-13 07:54:51.627 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch -1 fmt 0 @ -1Hz
2011-06-13 07:54:51.638 AFD: Opened codec 0x3020030, id(DVD_SUBTITLE) type(Subtitle)
2011-06-13 07:54:51.640 AFD: Opened codec 0x3023860, id(DVD_SUBTITLE) type(Subtitle)
2011-06-13 07:54:51.647 AFD: codec AC3 has 0 channels
2011-06-13 07:54:51.647 AFD: Opened codec 0x2bad030, id(AC3) type(Audio)
2011-06-13 07:54:51.694 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-06-13 07:54:51.695 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-06-13 07:54:51.704 ALSA, Error: no playback control PCM found on mixer device default
2011-06-13 07:54:51.704 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-06-13 07:54:51.704 AudioPlayer: Enabling Audio
2011-06-13 07:55:01.346 TV: Attempting to change from WatchingDVD to None
2011-06-13 07:55:01.362 TV: Changing from WatchingDVD to None
Restarting mythfrontend.real...
2011-06-13 07:55:57.267 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 07:55:57.267 Using runtime prefix = /usr
2011-06-13 07:55:57.267 Using configuration directory = /home/crhome/.mythtv
2011-06-13 07:55:57.268 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 07:55:57.845 Empty LocalHostName.
2011-06-13 07:55:57.845 Using localhost value of crhome-htpc
2011-06-13 07:55:57.851 New DB connection, total: 1
2011-06-13 07:55:57.854 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:55:57.859 Closing DB connection named 'DBManager0'
2011-06-13 07:55:57.860 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:55:57.861 Current locale EN_US
2011-06-13 07:55:57.861 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 07:55:58.069 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 07:55:58.070 DPMS is active.
2011-06-13 07:55:58.084 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 07:55:58.671 Enabled verbose msgs:  important general
2011-06-13 07:55:58.673 Loading en_us translation for module mythfrontend
2011-06-13 07:55:58.676 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 07:55:58.676 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 07:55:58.697 Using Frameless Window
2011-06-13 07:55:58.697 Using Full Screen Window
2011-06-13 07:55:58.762 Using the Qt painter
2011-06-13 07:55:58.895 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 07:55:58.900 New DB connection, total: 2
2011-06-13 07:55:58.904 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:55:58.963 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 07:55:58.963 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 07:55:58.964 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 07:55:58.964 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 07:55:59.064 Registering Internal as a media playback plugin.
2011-06-13 07:55:59.078 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:55:59.078 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:55:59.078 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:55:59.078 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 07:55:59.078 Loading en_us translation for module mythgallery
2011-06-13 07:55:59.082 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 07:55:59.089 Loading en_us translation for module mythvideo
2011-06-13 07:55:59.092 Loading en_us translation for module mythweather
2011-06-13 07:55:59.253 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 07:55:59.283 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 07:55:59.284 Using protocol version 63
2011-06-13 07:56:28.558 No Active Screens are defined. Nothing Saved.
Restarting mythfrontend.real...
2011-06-13 07:56:31.066 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 07:56:31.066 Using runtime prefix = /usr
2011-06-13 07:56:31.066 Using configuration directory = /home/crhome/.mythtv
2011-06-13 07:56:31.066 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 07:56:32.072 Empty LocalHostName.
2011-06-13 07:56:32.072 Using localhost value of crhome-htpc
2011-06-13 07:56:32.076 New DB connection, total: 1
2011-06-13 07:56:32.078 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:56:32.081 Closing DB connection named 'DBManager0'
2011-06-13 07:56:32.081 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:56:32.082 Current locale EN_US
2011-06-13 07:56:32.082 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 07:56:32.286 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 07:56:32.287 DPMS is active.
2011-06-13 07:56:32.302 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 07:56:32.880 Enabled verbose msgs:  important general
2011-06-13 07:56:32.881 Loading en_us translation for module mythfrontend
2011-06-13 07:56:32.884 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 07:56:32.884 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 07:56:32.905 Using Frameless Window
2011-06-13 07:56:32.905 Using Full Screen Window
2011-06-13 07:56:32.965 Using the Qt painter
2011-06-13 07:56:33.102 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 07:56:33.105 New DB connection, total: 2
2011-06-13 07:56:33.106 Connected to database 'mythconverg' at host: localhost
2011-06-13 07:56:33.158 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 07:56:33.158 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 07:56:33.159 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 07:56:33.159 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 07:56:33.251 Registering Internal as a media playback plugin.
2011-06-13 07:56:33.263 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:56:33.263 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:56:33.263 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 07:56:33.264 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 07:56:33.264 Loading en_us translation for module mythgallery
2011-06-13 07:56:33.268 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 07:56:33.274 Loading en_us translation for module mythvideo
2011-06-13 07:56:33.277 Loading en_us translation for module mythweather
2011-06-13 07:56:33.438 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 07:56:33.469 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 07:56:33.469 Using protocol version 63
2011-06-13 07:56:48.916 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2011-06-13 22:28:30.636 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 22:28:30.637 Using runtime prefix = /usr
2011-06-13 22:28:30.637 Using configuration directory = /home/crhome/.mythtv
2011-06-13 22:28:30.638 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 22:28:31.428 Empty LocalHostName.
2011-06-13 22:28:31.428 Using localhost value of crhome-htpc
2011-06-13 22:28:31.434 New DB connection, total: 1
2011-06-13 22:28:31.436 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:28:31.442 Closing DB connection named 'DBManager0'
2011-06-13 22:28:31.443 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:28:31.444 Current locale EN_US
2011-06-13 22:28:31.444 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 22:28:31.650 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 22:28:31.651 DPMS is active.
2011-06-13 22:28:31.691 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 22:28:32.272 Enabled verbose msgs:  important general
2011-06-13 22:28:32.294 Loading en_us translation for module mythfrontend
2011-06-13 22:28:32.350 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 22:28:32.350 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 22:28:32.407 Using Frameless Window
2011-06-13 22:28:32.407 Using Full Screen Window
2011-06-13 22:28:32.541 Using the Qt painter
2011-06-13 22:28:33.059 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 22:28:33.072 New DB connection, total: 2
2011-06-13 22:28:33.073 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:28:33.653 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 22:28:33.653 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 22:28:33.702 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 22:28:33.702 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 22:28:33.864 Registering Internal as a media playback plugin.
2011-06-13 22:28:33.867 Registering WebBrowser as a media playback plugin.
2011-06-13 22:28:33.868 Loading en_us translation for module mythbrowser
2011-06-13 22:28:33.902 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:28:33.902 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:28:33.903 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:28:33.903 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 22:28:33.915 Loading en_us translation for module mythgallery
2011-06-13 22:28:34.029 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 22:28:34.062 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 22:28:34.067 Loading en_us translation for module mythmusic
2011-06-13 22:28:34.132 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 22:28:34.151 Loading en_us translation for module mythvideo
2011-06-13 22:28:34.180 Loading en_us translation for module mythweather
2011-06-13 22:28:34.415 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 22:28:34.457 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 22:28:34.462 Using protocol version 63
2011-06-13 22:30:52.956 VirtualKeyboard, Warning: Cannot find layout for 'en'
2011-06-13 22:30:52.988 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
2011-06-13 22:32:39.967 Received a remote 'Clear Cache' request
2011-06-13 22:33:19.392 Received a remote 'Clear Cache' request
2011-06-13 22:33:19.393 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 22:33:19.393 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 22:33:19.394 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 22:33:19.394 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 22:35:11.934 New DB connection, total: 3
2011-06-13 22:35:11.934 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:35:11.944 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 22:36:42.601 No Active Screens are defined. Nothing Saved.
Restarting mythfrontend.real...
2011-06-13 22:36:46.897 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 22:36:46.897 Using runtime prefix = /usr
2011-06-13 22:36:46.897 Using configuration directory = /home/crhome/.mythtv
2011-06-13 22:36:46.898 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 22:36:47.507 Empty LocalHostName.
2011-06-13 22:36:47.507 Using localhost value of crhome-htpc
2011-06-13 22:36:47.513 New DB connection, total: 1
2011-06-13 22:36:47.516 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:36:47.522 Closing DB connection named 'DBManager0'
2011-06-13 22:36:47.522 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:36:47.524 Current locale EN_US
2011-06-13 22:36:47.524 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 22:36:47.732 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 22:36:47.734 DPMS is active.
2011-06-13 22:36:47.749 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 22:36:48.362 Enabled verbose msgs:  important general
2011-06-13 22:36:48.364 Loading en_us translation for module mythfrontend
2011-06-13 22:36:48.368 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 22:36:48.368 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 22:36:48.389 Using Frameless Window
2011-06-13 22:36:48.389 Using Full Screen Window
2011-06-13 22:36:48.446 Using the Qt painter
2011-06-13 22:36:48.585 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 22:36:48.593 New DB connection, total: 2
2011-06-13 22:36:48.601 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:36:48.651 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 22:36:48.651 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 22:36:48.651 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 22:36:48.651 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 22:36:48.896 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:36:48.901 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:36:48.993 Pulse: PulseAudio resume OK
2011-06-13 22:36:48.994 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 22:36:49.081 Registering Internal as a media playback plugin.
2011-06-13 22:36:49.086 Registering WebBrowser as a media playback plugin.
2011-06-13 22:36:49.086 Loading en_us translation for module mythbrowser
2011-06-13 22:36:49.109 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:36:49.109 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:36:49.109 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:36:49.110 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 22:36:49.110 Loading en_us translation for module mythgallery
2011-06-13 22:36:49.125 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 22:36:49.143 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 22:36:49.146 Loading en_us translation for module mythmusic
2011-06-13 22:36:49.151 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 22:36:49.159 Loading en_us translation for module mythvideo
2011-06-13 22:36:49.162 Loading en_us translation for module mythweather
2011-06-13 22:36:49.163 NetworkControl: Listening for remote connections on port 6546
2011-06-13 22:36:49.342 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 22:36:49.390 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 22:36:49.391 Using protocol version 63
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
2011-06-13 22:36:55.238 Failed to mount /dev/sr0.
2011-06-13 22:37:01.053 NetworkControl: New connection established.
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DEVIL
libdvdnav: DVD Serial Number: 3D9BBCA8C2644357
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/crhome/.dvdnav/DEVIL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2011-06-13 22:37:21.446 Opened DVD device at /dev/dvd
2011-06-13 22:37:21.446 There are 6 titles on the disk
2011-06-13 22:37:21.446 DVDRB: Title 1 has 21 parts.
2011-06-13 22:37:21.446 DVDRB: Title 2 has 2 parts.
2011-06-13 22:37:21.446 DVDRB: Title 3 has 7 parts.
2011-06-13 22:37:21.446 DVDRB: Title 4 has 2 parts.
2011-06-13 22:37:21.446 DVDRB: Title 5 has 2 parts.
2011-06-13 22:37:21.446 DVDRB: Title 6 has 2 parts.
2011-06-13 22:37:21.547 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DEVIL
libdvdnav: DVD Serial Number: 3D9BBCA8C2644357
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/crhome/.dvdnav/DEVIL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2011-06-13 22:37:21.888 Opened DVD device at /dev/dvd
2011-06-13 22:37:21.888 There are 6 titles on the disk
2011-06-13 22:37:21.888 DVDRB: Title 1 has 21 parts.
2011-06-13 22:37:21.888 DVDRB: Title 2 has 2 parts.
2011-06-13 22:37:21.888 DVDRB: Title 3 has 7 parts.
2011-06-13 22:37:21.888 DVDRB: Title 4 has 2 parts.
2011-06-13 22:37:21.888 DVDRB: Title 5 has 2 parts.
2011-06-13 22:37:21.888 DVDRB: Title 6 has 2 parts.
2011-06-13 22:37:22.120 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:37:22.124 ALSA, Error: snd_pcm_open("default0"): No such file or directory

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000014a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000006ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0021c54a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0021c562
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
2011-06-13 22:37:22.269 DVDRB: Resetting DVD device.
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2011-06-13 22:37:22.276 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-06-13 22:37:22.276 AFD: Opened codec 0x7f94387b42b0, id(MPEG2VIDEO) type(Video)
2011-06-13 22:37:22.277 AFD: codec AC3 has 6 channels
2011-06-13 22:37:22.277 AFD: Opened codec 0x7f94388072a0, id(AC3) type(Audio)
2011-06-13 22:37:22.420 Pulse: PulseAudio resume OK
2011-06-13 22:37:22.520 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:37:22.522 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:37:22.523 AO: Opening audio device 'default0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:37:22.523 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:37:22.523 AudioOutput Error: Aborting reconfigure
2011-06-13 22:37:22.523 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-06-13 22:37:22.543 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-06-13 22:37:22.568 OSD: Base theme size: 1280x720
2011-06-13 22:37:22.568 OSD: Scaling factors: 0.5625x0.666667
2011-06-13 22:37:22.612 OSD: Base theme size: 1280x720
2011-06-13 22:37:22.612 OSD: Scaling factors: 0.5625x0.666667
2011-06-13 22:37:22.643 Player(0): Video timing method: DRM
2011-06-13 22:37:22.675 TV: Changing from None to WatchingDVD
2011-06-13 22:37:22.683 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 22:37:22.684 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 22:37:22.684 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 22:37:22.684 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 22:37:22.684 ScreenSaverX11Private: DPMS Deactivated 1
2011-06-13 22:37:22.703 VideoOutput: Created YV12 OSD.
2011-06-13 22:37:23.658 ScreenSaverX11Private: DPMS Reactivated 1
2011-06-13 22:37:23.659 AudioPlayer: Disabling Audio, params(0,-1,-1)
2011-06-13 22:37:23.822 Pulse: PulseAudio resume OK
2011-06-13 22:37:23.922 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:37:23.927 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:37:23.927 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch -1 fmt 0 @ -1Hz
2011-06-13 22:37:23.929 AFD: Opened codec 0x2c41240, id(DVD_SUBTITLE) type(Subtitle)
2011-06-13 22:37:23.931 AFD: Opened codec 0x2c6f070, id(DVD_SUBTITLE) type(Subtitle)
2011-06-13 22:37:23.939 AFD: codec AC3 has 0 channels
2011-06-13 22:37:23.940 AFD: Opened codec 0x7f9438c8f510, id(AC3) type(Audio)
2011-06-13 22:37:24.122 Pulse: PulseAudio resume OK
2011-06-13 22:37:24.222 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:37:24.225 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:37:24.225 AO: Opening audio device 'default0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:37:24.225 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:37:24.225 AudioOutput Error: Aborting reconfigure
2011-06-13 22:37:24.225 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-06-13 22:38:10.599 OSD: Base theme size: 1280x720
2011-06-13 22:38:10.600 OSD: Scaling factors: 0.5625x0.666667
2011-06-13 22:38:13.702 TV: OSDDialogEvent: result -1 text  action 0
2011-06-13 22:38:17.797 TV: Attempting to change from WatchingDVD to None
2011-06-13 22:38:17.819 MythPainter: 9 images not yet de-allocated.
2011-06-13 22:38:17.969 Pulse: PulseAudio resume OK
2011-06-13 22:38:17.969 TV: Changing from WatchingDVD to None
2011-06-13 22:41:43.723 New DB connection, total: 3
2011-06-13 22:41:43.723 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:41:43.733 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 22:41:43.803 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:41:44.357 CD status has changed.
2011-06-13 22:42:01.735 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:42:04.706 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:43:27.648 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:44:00.131 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:45:00.615 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:45:15.653 Track, Warning: Track Number of 0 is invalid!
2011-06-13 22:45:15.653 Track, Error: putYourselfOnTheListView() failed to create a widget
2011-06-13 22:45:23.728 Playlist, Error: Song with ID of 0 in playlist, this shouldn't happen.
2011-06-13 22:45:23.728 Playlist, Error: Song with ID of 0 in playlist, this shouldn't happen.
2011-06-13 22:45:27.950 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:45:28.180 Playlist, Error: Song with ID of 0 in playlist, this shouldn't happen.
2011-06-13 22:45:28.180 Playlist, Error: Song with ID of 0 in playlist, this shouldn't happen.
2011-06-13 22:45:28.408 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:45:28.413 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:45:28.413 AO: Resampling from 44 kHz to 48 kHz with quality medium
2011-06-13 22:45:28.427 AO: Opening audio device 'default0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:45:28.427 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:45:28.428 AudioOutput Error: Aborting reconfigure
Restarting mythfrontend.real...
2011-06-13 22:45:41.985 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 22:45:41.985 Using runtime prefix = /usr
2011-06-13 22:45:41.985 Using configuration directory = /home/crhome/.mythtv
2011-06-13 22:45:41.986 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 22:45:42.510 Empty LocalHostName.
2011-06-13 22:45:42.510 Using localhost value of crhome-htpc
2011-06-13 22:45:42.516 New DB connection, total: 1
2011-06-13 22:45:42.519 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:45:42.524 Closing DB connection named 'DBManager0'
2011-06-13 22:45:42.524 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:45:42.526 Current locale EN_US
2011-06-13 22:45:42.526 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 22:45:42.735 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 22:45:42.736 DPMS is active.
2011-06-13 22:45:42.751 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 22:45:43.353 Enabled verbose msgs:  important general
2011-06-13 22:45:43.354 Loading en_us translation for module mythfrontend
2011-06-13 22:45:43.357 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 22:45:43.358 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 22:45:43.378 Using Frameless Window
2011-06-13 22:45:43.378 Using Full Screen Window
2011-06-13 22:45:43.441 Using the Qt painter
2011-06-13 22:45:43.569 New DB connection, total: 2
2011-06-13 22:45:43.569 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:45:43.571 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 22:45:43.638 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 22:45:43.638 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 22:45:43.639 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 22:45:43.639 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 22:45:43.898 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:45:43.904 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:45:43.996 Pulse: PulseAudio resume OK
2011-06-13 22:45:43.997 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 22:45:44.084 Registering Internal as a media playback plugin.
2011-06-13 22:45:44.089 Registering WebBrowser as a media playback plugin.
2011-06-13 22:45:44.089 Loading en_us translation for module mythbrowser
2011-06-13 22:45:44.112 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:45:44.112 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:45:44.112 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:45:44.113 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 22:45:44.113 Loading en_us translation for module mythgallery
2011-06-13 22:45:44.127 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 22:45:44.145 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 22:45:44.148 Loading en_us translation for module mythmusic
2011-06-13 22:45:44.152 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 22:45:44.160 Loading en_us translation for module mythvideo
2011-06-13 22:45:44.164 Loading en_us translation for module mythweather
2011-06-13 22:45:44.165 NetworkControl: Listening for remote connections on port 6546
2011-06-13 22:45:44.331 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 22:45:44.363 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 22:45:44.364 Using protocol version 63
2011-06-13 22:46:01.101 NetworkControl: New connection established.
2011-06-13 22:46:05.019 New DB connection, total: 3
2011-06-13 22:46:05.020 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:46:05.028 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 22:46:05.099 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:46:05.624 CD status has changed.
2011-06-13 22:46:15.621 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:46:15.628 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:46:15.628 AO: Resampling from 44 kHz to 48 kHz with quality medium
2011-06-13 22:46:15.628 AO: Opening audio device 'default0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:46:15.628 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:46:15.628 AudioOutput Error: Aborting reconfigure
Restarting mythfrontend.real...
2011-06-13 22:46:21.931 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 22:46:21.931 Using runtime prefix = /usr
2011-06-13 22:46:21.931 Using configuration directory = /home/crhome/.mythtv
2011-06-13 22:46:21.932 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 22:46:22.441 Empty LocalHostName.
2011-06-13 22:46:22.441 Using localhost value of crhome-htpc
2011-06-13 22:46:22.447 New DB connection, total: 1
2011-06-13 22:46:22.449 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:46:22.455 Closing DB connection named 'DBManager0'
2011-06-13 22:46:22.455 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:46:22.456 Current locale EN_US
2011-06-13 22:46:22.456 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 22:46:22.663 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 22:46:22.664 DPMS is active.
2011-06-13 22:46:22.678 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 22:46:23.272 Enabled verbose msgs:  important general
2011-06-13 22:46:23.273 Loading en_us translation for module mythfrontend
2011-06-13 22:46:23.276 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 22:46:23.277 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 22:46:23.297 Using Frameless Window
2011-06-13 22:46:23.297 Using Full Screen Window
2011-06-13 22:46:23.358 Using the Qt painter
2011-06-13 22:46:23.487 New DB connection, total: 2
2011-06-13 22:46:23.488 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 22:46:23.499 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:46:23.548 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 22:46:23.548 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 22:46:23.549 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 22:46:23.549 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 22:46:23.829 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:46:23.834 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:46:23.927 Pulse: PulseAudio resume OK
2011-06-13 22:46:23.927 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 22:46:24.007 Registering Internal as a media playback plugin.
2011-06-13 22:46:24.012 Registering WebBrowser as a media playback plugin.
2011-06-13 22:46:24.012 Loading en_us translation for module mythbrowser
2011-06-13 22:46:24.031 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:46:24.031 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:46:24.031 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:46:24.032 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 22:46:24.032 Loading en_us translation for module mythgallery
2011-06-13 22:46:24.047 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 22:46:24.061 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 22:46:24.063 Loading en_us translation for module mythmusic
2011-06-13 22:46:24.067 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 22:46:24.073 Loading en_us translation for module mythvideo
2011-06-13 22:46:24.076 Loading en_us translation for module mythweather
2011-06-13 22:46:24.077 NetworkControl: Listening for remote connections on port 6546
2011-06-13 22:46:24.239 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 22:46:24.270 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 22:46:24.271 Using protocol version 63
2011-06-13 22:46:39.322 NetworkControl: New connection established.
2011-06-13 22:46:57.867 New DB connection, total: 3
2011-06-13 22:46:57.867 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:46:57.873 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 22:46:57.944 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 22:46:58.469 CD status has changed.
2011-06-13 22:47:08.462 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:47:08.468 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:47:08.468 AO: Resampling from 44 kHz to 48 kHz with quality medium
2011-06-13 22:47:08.468 AO: Opening audio device 'default0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:47:08.468 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:47:08.468 AudioOutput Error: Aborting reconfigure
Restarting mythfrontend.real...
2011-06-13 22:47:15.125 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 22:47:15.125 Using runtime prefix = /usr
2011-06-13 22:47:15.125 Using configuration directory = /home/crhome/.mythtv
2011-06-13 22:47:15.125 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 22:47:15.756 Empty LocalHostName.
2011-06-13 22:47:15.756 Using localhost value of crhome-htpc
2011-06-13 22:47:15.762 New DB connection, total: 1
2011-06-13 22:47:15.765 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:47:15.770 Closing DB connection named 'DBManager0'
2011-06-13 22:47:15.771 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:47:15.771 Current locale EN_US
2011-06-13 22:47:15.772 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 22:47:15.978 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 22:47:15.979 DPMS is active.
2011-06-13 22:47:15.993 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 22:47:16.562 Enabled verbose msgs:  important general
2011-06-13 22:47:16.563 Loading en_us translation for module mythfrontend
2011-06-13 22:47:16.567 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 22:47:16.567 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 22:47:16.587 Using Frameless Window
2011-06-13 22:47:16.587 Using Full Screen Window
2011-06-13 22:47:16.650 Using the Qt painter
2011-06-13 22:47:16.778 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 22:47:16.782 New DB connection, total: 2
2011-06-13 22:47:16.782 Connected to database 'mythconverg' at host: localhost
2011-06-13 22:47:16.833 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 22:47:16.833 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 22:47:16.834 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 22:47:16.834 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 22:47:17.142 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 22:47:17.147 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 22:47:17.240 Pulse: PulseAudio resume OK
2011-06-13 22:47:17.240 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 22:47:17.320 Registering Internal as a media playback plugin.
2011-06-13 22:47:17.324 Registering WebBrowser as a media playback plugin.
2011-06-13 22:47:17.324 Loading en_us translation for module mythbrowser
2011-06-13 22:47:17.344 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:47:17.344 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:47:17.344 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 22:47:17.345 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 22:47:17.345 Loading en_us translation for module mythgallery
2011-06-13 22:47:17.358 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 22:47:17.372 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 22:47:17.374 Loading en_us translation for module mythmusic
2011-06-13 22:47:17.378 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 22:47:17.384 Loading en_us translation for module mythvideo
2011-06-13 22:47:17.387 Loading en_us translation for module mythweather
2011-06-13 22:47:17.388 NetworkControl: Listening for remote connections on port 6546
2011-06-13 22:47:17.554 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 22:47:17.586 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 22:47:17.586 Using protocol version 63
2011-06-13 22:47:30.969 NetworkControl: New connection established.
2011-06-13 22:48:37.188 BookmarkManager: Something is wrong. Asked to edit a non existent bookmark!
2011-06-13 22:48:42.929 BookmarkManager: Something is wrong. Asked to edit a non existent bookmark!
2011-06-13 22:51:40.616 Received a remote 'Clear Cache' request
2011-06-13 22:51:46.662 Received a remote 'Clear Cache' request
2011-06-13 22:51:56.784 NetworkControl: Client Socket disconnected
2011-06-13 22:51:56.801 Pulse: Cleaning up PulseHandler
2011-06-13 22:51:56.801 Deleting UPnP client...
Starting mythfrontend.real..
2011-06-13 23:03:58.585 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 23:03:58.585 Using runtime prefix = /usr
2011-06-13 23:03:58.585 Using configuration directory = /home/crhome/.mythtv
2011-06-13 23:03:58.585 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 23:03:59.094 Empty LocalHostName.
2011-06-13 23:03:59.094 Using localhost value of crhome-htpc
2011-06-13 23:03:59.100 New DB connection, total: 1
2011-06-13 23:03:59.103 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:03:59.106 Closing DB connection named 'DBManager0'
2011-06-13 23:03:59.107 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:03:59.107 Current locale EN_US
2011-06-13 23:03:59.107 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 23:03:59.313 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 23:03:59.314 DPMS is active.
2011-06-13 23:03:59.330 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 23:03:59.913 Enabled verbose msgs:  important general
2011-06-13 23:03:59.914 Loading en_us translation for module mythfrontend
2011-06-13 23:03:59.919 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 23:03:59.919 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 23:03:59.941 Using Frameless Window
2011-06-13 23:03:59.941 Using Full Screen Window
2011-06-13 23:03:59.999 Using the Qt painter
2011-06-13 23:04:00.133 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 23:04:00.199 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 23:04:00.199 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 23:04:00.199 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 23:04:00.199 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 23:04:00.478 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:04:00.484 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:04:00.576 Pulse: PulseAudio resume OK
2011-06-13 23:04:00.576 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 23:04:00.665 Registering Internal as a media playback plugin.
2011-06-13 23:04:00.670 Registering WebBrowser as a media playback plugin.
2011-06-13 23:04:00.670 Loading en_us translation for module mythbrowser
2011-06-13 23:04:00.693 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:04:00.693 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:04:00.693 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:04:00.694 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 23:04:00.694 Loading en_us translation for module mythgallery
2011-06-13 23:04:00.708 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 23:04:00.725 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 23:04:00.728 Loading en_us translation for module mythmusic
2011-06-13 23:04:00.733 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 23:04:00.746 Loading en_us translation for module mythvideo
2011-06-13 23:04:00.752 Loading en_us translation for module mythweather
2011-06-13 23:04:00.753 NetworkControl: Listening for remote connections on port 6546
2011-06-13 23:04:00.930 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 23:04:00.963 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 23:04:00.963 Using protocol version 63
2011-06-13 23:04:06.484 New DB connection, total: 2
2011-06-13 23:04:06.484 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:04:06.491 New DB connection, total: 3
2011-06-13 23:04:06.492 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:04:06.501 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 23:04:06.570 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 23:04:07.085 CD status has changed.
2011-06-13 23:04:17.089 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:04:17.094 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:04:17.094 AO: Resampling from 44 kHz to 48 kHz with quality medium
2011-06-13 23:04:17.095 AO: Opening audio device 'default0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:04:17.095 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:04:17.095 AudioOutput Error: Aborting reconfigure
Restarting mythfrontend.real...
2011-06-13 23:04:24.286 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 23:04:24.286 Using runtime prefix = /usr
2011-06-13 23:04:24.286 Using configuration directory = /home/crhome/.mythtv
2011-06-13 23:04:24.287 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 23:04:24.692 Empty LocalHostName.
2011-06-13 23:04:24.692 Using localhost value of crhome-htpc
2011-06-13 23:04:24.698 New DB connection, total: 1
2011-06-13 23:04:24.701 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:04:24.706 Closing DB connection named 'DBManager0'
2011-06-13 23:04:24.707 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:04:24.708 Current locale EN_US
2011-06-13 23:04:24.708 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 23:04:24.915 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 23:04:24.919 DPMS is active.
2011-06-13 23:04:24.934 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 23:04:25.513 Enabled verbose msgs:  important general
2011-06-13 23:04:25.514 Loading en_us translation for module mythfrontend
2011-06-13 23:04:25.518 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 23:04:25.518 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 23:04:25.539 Using Frameless Window
2011-06-13 23:04:25.539 Using Full Screen Window
2011-06-13 23:04:25.592 Using the Qt painter
2011-06-13 23:04:25.745 New DB connection, total: 2
2011-06-13 23:04:25.746 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:04:25.746 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 23:04:25.801 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 23:04:25.802 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 23:04:25.802 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 23:04:25.802 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 23:04:26.079 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:04:26.085 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:04:26.177 Pulse: PulseAudio resume OK
2011-06-13 23:04:26.177 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 23:04:26.260 Registering Internal as a media playback plugin.
2011-06-13 23:04:26.265 Registering WebBrowser as a media playback plugin.
2011-06-13 23:04:26.265 Loading en_us translation for module mythbrowser
2011-06-13 23:04:26.285 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:04:26.285 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:04:26.286 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:04:26.286 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 23:04:26.287 Loading en_us translation for module mythgallery
2011-06-13 23:04:26.299 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 23:04:26.313 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 23:04:26.315 Loading en_us translation for module mythmusic
2011-06-13 23:04:26.320 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 23:04:26.327 Loading en_us translation for module mythvideo
2011-06-13 23:04:26.330 Loading en_us translation for module mythweather
2011-06-13 23:04:26.330 NetworkControl: Listening for remote connections on port 6546
2011-06-13 23:04:26.498 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 23:04:26.532 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 23:04:26.532 Using protocol version 63
2011-06-13 23:04:39.012 Pulse: Cleaning up PulseHandler
2011-06-13 23:04:39.013 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2011-06-13 23:22:43.011 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 23:22:43.011 Using runtime prefix = /usr
2011-06-13 23:22:43.011 Using configuration directory = /home/crhome/.mythtv
2011-06-13 23:22:43.012 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 23:22:43.582 Empty LocalHostName.
2011-06-13 23:22:43.582 Using localhost value of crhome-htpc
2011-06-13 23:22:43.588 New DB connection, total: 1
2011-06-13 23:22:43.591 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:22:43.597 Closing DB connection named 'DBManager0'
2011-06-13 23:22:43.597 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:22:43.598 Current locale EN_US
2011-06-13 23:22:43.598 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 23:22:43.805 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 23:22:43.806 DPMS is active.
2011-06-13 23:22:43.820 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 23:22:44.393 Enabled verbose msgs:  important general
2011-06-13 23:22:44.394 Loading en_us translation for module mythfrontend
2011-06-13 23:22:44.398 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 23:22:44.398 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 23:22:44.418 Using Frameless Window
2011-06-13 23:22:44.418 Using Full Screen Window
2011-06-13 23:22:44.480 Using the Qt painter
2011-06-13 23:22:44.615 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 23:22:44.621 New DB connection, total: 2
2011-06-13 23:22:44.625 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:22:44.672 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 23:22:44.672 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 23:22:44.672 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 23:22:44.672 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 23:22:44.969 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:22:44.974 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:22:45.067 Pulse: PulseAudio resume OK
2011-06-13 23:22:45.067 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 23:22:45.147 Registering Internal as a media playback plugin.
2011-06-13 23:22:45.152 Registering WebBrowser as a media playback plugin.
2011-06-13 23:22:45.152 Loading en_us translation for module mythbrowser
2011-06-13 23:22:45.171 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:22:45.171 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:22:45.172 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:22:45.172 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 23:22:45.173 Loading en_us translation for module mythgallery
2011-06-13 23:22:45.187 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 23:22:45.201 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 23:22:45.203 Loading en_us translation for module mythmusic
2011-06-13 23:22:45.207 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 23:22:45.213 Loading en_us translation for module mythvideo
2011-06-13 23:22:45.216 Loading en_us translation for module mythweather
2011-06-13 23:22:45.217 NetworkControl: Listening for remote connections on port 6546
2011-06-13 23:22:45.385 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 23:22:45.417 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 23:22:45.417 Using protocol version 63
2011-06-13 23:22:50.452 New DB connection, total: 3
2011-06-13 23:22:50.453 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:22:50.459 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 23:22:50.529 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 23:22:51.042 CD status has changed.
2011-06-13 23:23:00.979 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:23:00.984 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:23:00.984 AO: Resampling from 44 kHz to 48 kHz with quality medium
2011-06-13 23:23:00.985 AO: Opening audio device 'default0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:23:00.985 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:23:00.985 AudioOutput Error: Aborting reconfigure
Restarting mythfrontend.real...
2011-06-13 23:23:08.344 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 23:23:08.344 Using runtime prefix = /usr
2011-06-13 23:23:08.344 Using configuration directory = /home/crhome/.mythtv
2011-06-13 23:23:08.345 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 23:23:08.905 Empty LocalHostName.
2011-06-13 23:23:08.905 Using localhost value of crhome-htpc
2011-06-13 23:23:08.911 New DB connection, total: 1
2011-06-13 23:23:08.914 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:23:08.919 Closing DB connection named 'DBManager0'
2011-06-13 23:23:08.920 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:23:08.921 Current locale EN_US
2011-06-13 23:23:08.921 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 23:23:09.128 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 23:23:09.129 DPMS is active.
2011-06-13 23:23:09.143 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 23:23:09.712 Enabled verbose msgs:  important general
2011-06-13 23:23:09.713 Loading en_us translation for module mythfrontend
2011-06-13 23:23:09.717 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 23:23:09.717 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 23:23:09.737 Using Frameless Window
2011-06-13 23:23:09.738 Using Full Screen Window
2011-06-13 23:23:09.794 Using the Qt painter
2011-06-13 23:23:09.934 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 23:23:09.986 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 23:23:09.986 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 23:23:09.986 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 23:23:09.986 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 23:23:10.196 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:23:10.201 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:23:10.294 Pulse: PulseAudio resume OK
2011-06-13 23:23:10.294 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 23:23:10.371 Registering Internal as a media playback plugin.
2011-06-13 23:23:10.376 Registering WebBrowser as a media playback plugin.
2011-06-13 23:23:10.376 Loading en_us translation for module mythbrowser
2011-06-13 23:23:10.395 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:23:10.395 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:23:10.395 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:23:10.396 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 23:23:10.396 Loading en_us translation for module mythgallery
2011-06-13 23:23:10.409 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 23:23:10.422 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 23:23:10.424 Loading en_us translation for module mythmusic
2011-06-13 23:23:10.428 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 23:23:10.434 Loading en_us translation for module mythvideo
2011-06-13 23:23:10.437 Loading en_us translation for module mythweather
2011-06-13 23:23:10.438 NetworkControl: Listening for remote connections on port 6546
2011-06-13 23:23:10.603 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 23:23:10.634 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 23:23:10.635 Using protocol version 63
2011-06-13 23:23:23.618 Pulse: Cleaning up PulseHandler
2011-06-13 23:23:23.618 Deleting UPnP client...
Starting mythfrontend.real..
2011-06-13 23:25:28.653 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-13 23:25:28.653 Using runtime prefix = /usr
2011-06-13 23:25:28.653 Using configuration directory = /home/crhome/.mythtv
2011-06-13 23:25:28.654 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-13 23:25:29.170 Empty LocalHostName.
2011-06-13 23:25:29.170 Using localhost value of crhome-htpc
2011-06-13 23:25:29.175 New DB connection, total: 1
2011-06-13 23:25:29.178 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:25:29.183 Closing DB connection named 'DBManager0'
2011-06-13 23:25:29.183 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:25:29.184 Current locale EN_US
2011-06-13 23:25:29.184 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-13 23:25:29.390 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-13 23:25:29.391 DPMS is active.
2011-06-13 23:25:29.406 Desktop video mode: 1360x768 60.015 Hz
2011-06-13 23:25:29.982 Enabled verbose msgs:  important general
2011-06-13 23:25:29.984 Loading en_us translation for module mythfrontend
2011-06-13 23:25:29.987 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-13 23:25:29.987 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-13 23:25:30.007 Using Frameless Window
2011-06-13 23:25:30.008 Using Full Screen Window
2011-06-13 23:25:30.069 Using the Qt painter
2011-06-13 23:25:30.205 New DB connection, total: 2
2011-06-13 23:25:30.205 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:25:30.205 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-13 23:25:30.264 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-13 23:25:30.264 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-13 23:25:30.265 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-13 23:25:30.265 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-13 23:25:30.554 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:25:30.558 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:25:30.651 Pulse: PulseAudio resume OK
2011-06-13 23:25:30.652 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 23:25:30.731 Registering Internal as a media playback plugin.
2011-06-13 23:25:30.736 Registering WebBrowser as a media playback plugin.
2011-06-13 23:25:30.736 Loading en_us translation for module mythbrowser
2011-06-13 23:25:30.755 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:25:30.756 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:25:30.756 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-13 23:25:30.756 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-13 23:25:30.757 Loading en_us translation for module mythgallery
2011-06-13 23:25:30.769 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-13 23:25:30.783 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-13 23:25:30.785 Loading en_us translation for module mythmusic
2011-06-13 23:25:30.789 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-13 23:25:30.796 Loading en_us translation for module mythvideo
2011-06-13 23:25:30.799 Loading en_us translation for module mythweather
2011-06-13 23:25:30.799 NetworkControl: Listening for remote connections on port 6546
2011-06-13 23:25:30.964 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-13 23:25:30.998 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-13 23:25:30.998 Using protocol version 63
2011-06-13 23:25:43.310 New DB connection, total: 3
2011-06-13 23:25:43.310 Connected to database 'mythconverg' at host: localhost
2011-06-13 23:25:43.316 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2011-06-13 23:25:56.297 VirtualKeyboard, Warning: Cannot find layout for 'en'
2011-06-13 23:25:56.301 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
2011-06-13 23:26:01.400 VirtualKeyboard, Warning: Cannot find layout for 'en'
2011-06-13 23:26:01.404 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
2011-06-13 23:26:55.118 Pulse: PulseAudio suspend OK
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM default0
2011-06-13 23:26:55.124 ALSA, Error: snd_pcm_open("default0"): No such file or directory
2011-06-13 23:26:55.218 Pulse: PulseAudio resume OK
2011-06-13 23:26:55.219 Audio device ALSA:default0 isn't usable Check audio configuration
2011-06-13 23:27:20.550 VirtualKeyboard, Warning: Cannot find layout for 'en'
2011-06-13 23:27:20.554 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
2011-06-13 23:28:56.998 Received a remote 'Clear Cache' request
2011-06-13 23:29:09.291 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default-wide/music-ui.xml'
2011-06-13 23:29:09.864 CD status has changed.
2011-06-13 23:29:19.685 AO: Opening audio device 'default' ch 2(2) sr 44100 sf signed 16 bit reenc 0
2011-06-13 23:29:19.686 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-06-13 23:29:19.715 ALSA, Error: no playback control PCM found on mixer device default
2011-06-13 23:29:19.715 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-06-13 23:30:49.555 Could not find widget to detach
2011-06-13 23:30:49.557 Could not find widget to detach
2011-06-13 23:30:49.561 Could not find widget to detach
2011-06-13 23:30:49.561 Pulse: Cleaning up PulseHandler
2011-06-13 23:30:49.561 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2011-06-18 09:15:55.078 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-18 09:15:55.078 Using runtime prefix = /usr
2011-06-18 09:15:55.078 Using configuration directory = /home/crhome/.mythtv
2011-06-18 09:15:55.096 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-18 09:15:56.053 Empty LocalHostName.
2011-06-18 09:15:56.054 Using localhost value of crhome-htpc
2011-06-18 09:15:56.060 New DB connection, total: 1
2011-06-18 09:15:56.062 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:15:56.068 Closing DB connection named 'DBManager0'
2011-06-18 09:15:56.068 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:15:56.069 Current locale EN_US
2011-06-18 09:15:56.069 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-18 09:15:56.276 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-18 09:15:56.277 DPMS is active.
2011-06-18 09:15:56.293 Desktop video mode: 1360x768 60.015 Hz
2011-06-18 09:15:56.885 Enabled verbose msgs:  important general
2011-06-18 09:15:56.896 Loading en_us translation for module mythfrontend
2011-06-18 09:15:56.951 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-18 09:15:56.951 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-18 09:15:56.999 Using Frameless Window
2011-06-18 09:15:56.999 Using Full Screen Window
2011-06-18 09:15:57.134 Using the Qt painter
2011-06-18 09:15:57.601 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-18 09:15:57.626 New DB connection, total: 2
2011-06-18 09:15:57.626 New DB connection, total: 3
2011-06-18 09:15:57.626 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:15:57.626 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:15:58.137 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-18 09:15:58.137 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-18 09:15:58.186 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-18 09:15:58.186 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-18 09:15:58.374 Registering Internal as a media playback plugin.
2011-06-18 09:15:58.393 Registering WebBrowser as a media playback plugin.
2011-06-18 09:15:58.405 Loading en_us translation for module mythbrowser
2011-06-18 09:15:58.437 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-18 09:15:58.437 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-18 09:15:58.437 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-18 09:15:58.438 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-18 09:15:58.450 Loading en_us translation for module mythgallery
2011-06-18 09:15:58.708 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-18 09:15:58.743 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-18 09:15:58.761 Loading en_us translation for module mythmusic
2011-06-18 09:15:58.833 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-18 09:15:58.851 Loading en_us translation for module mythvideo
2011-06-18 09:15:58.889 Loading en_us translation for module mythweather
2011-06-18 09:15:58.890 NetworkControl: Listening for remote connections on port 6546
2011-06-18 09:15:59.141 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-18 09:15:59.183 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-18 09:15:59.188 Using protocol version 63
Restarting mythfrontend.real...
2011-06-18 09:16:43.261 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-06-18 09:16:43.261 Using runtime prefix = /usr
2011-06-18 09:16:43.261 Using configuration directory = /home/crhome/.mythtv
2011-06-18 09:16:43.262 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-06-18 09:16:43.964 Empty LocalHostName.
2011-06-18 09:16:43.964 Using localhost value of crhome-htpc
2011-06-18 09:16:43.970 New DB connection, total: 1
2011-06-18 09:16:43.973 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:16:43.979 Closing DB connection named 'DBManager0'
2011-06-18 09:16:43.979 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:16:43.980 Current locale EN_US
2011-06-18 09:16:43.980 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-06-18 09:16:44.187 ScreenSaverX11Private: Gnome screen saver support enabled
2011-06-18 09:16:44.188 DPMS is active.
2011-06-18 09:16:44.202 Desktop video mode: 1360x768 60.015 Hz
2011-06-18 09:16:44.793 Enabled verbose msgs:  important general
2011-06-18 09:16:44.794 Loading en_us translation for module mythfrontend
2011-06-18 09:16:44.797 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-06-18 09:16:44.797 JoystickMenuThread: Joystick disabled - Failed to read /home/crhome/.mythtv/joystickmenurc
2011-06-18 09:16:44.818 Using Frameless Window
2011-06-18 09:16:44.818 Using Full Screen Window
2011-06-18 09:16:44.878 Using the Qt painter
2011-06-18 09:16:45.013 Current MythTV Schema Version (DBSchemaVer): 1264
2011-06-18 09:16:45.017 New DB connection, total: 2
2011-06-18 09:16:45.021 Connected to database 'mythconverg' at host: localhost
2011-06-18 09:16:45.067 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-06-18 09:16:45.067 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-06-18 09:16:45.068 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-06-18 09:16:45.068 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-06-18 09:16:45.160 Registering Internal as a media playback plugin.
2011-06-18 09:16:45.162 Registering WebBrowser as a media playback plugin.
2011-06-18 09:16:45.162 Loading en_us translation for module mythbrowser
2011-06-18 09:16:45.174 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-18 09:16:45.174 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-18 09:16:45.174 MediaMonitorUnix::AddDevice() - empty device path.
2011-06-18 09:16:45.174 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-06-18 09:16:45.174 Loading en_us translation for module mythgallery
2011-06-18 09:16:45.184 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-06-18 09:16:45.198 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-06-18 09:16:45.200 Loading en_us translation for module mythmusic
2011-06-18 09:16:45.204 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-06-18 09:16:45.211 Loading en_us translation for module mythvideo
2011-06-18 09:16:45.213 Loading en_us translation for module mythweather
2011-06-18 09:16:45.214 NetworkControl: Listening for remote connections on port 6546
2011-06-18 09:16:45.384 Found mainmenu.xml for theme 'MythCenter-wide'
2011-06-18 09:16:45.418 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-18 09:16:45.418 Using protocol version 63
2011-06-18 09:16:53.884 Deleting UPnP client...

---

### Post by nickrout on 2011-06-18
At what point in that log does it crash?

---

