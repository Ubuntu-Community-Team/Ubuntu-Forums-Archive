---
title: "Live tv not working"
date: 2011-04-25
forum: Mythbuntu
---

### Post by phroman on 2011-04-25
Mythfrontend version: fixes/0.24 (v0.24-248-g8c6ee70)

Hello everyone, my live TV isn't working right now, there are errors in both my frontend and backend logs.  The backend log shows permissions being denied when trying to use my serial port for external tuning, which I believe is the live TV issue.  I can still watch my recordings, just no live tv.  Here's my backend log:

```
2011-04-18 23:24:55.822 mythbackend version: fixes/0.24 [v0.24-248-g8c6ee70] www.mythtv.org
2011-04-18 23:24:56.222 Using runtime prefix = /usr
2011-04-18 23:24:56.428 Using configuration directory = /home/mythtv/.mythtv
2011-04-18 23:24:56.505 Empty LocalHostName.
2011-04-18 23:24:56.588 Using localhost value of mythserver
2011-04-18 23:24:56.699 Testing network connectivity to '192.168.1.22'
2011-04-18 23:24:56.873 New DB connection, total: 1
2011-04-18 23:24:57.017 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 23:24:57.177 Closing DB connection named 'DBManager0'
2011-04-18 23:24:57.231 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 23:24:57.672 Current locale en_US
2011-04-18 23:24:57.741 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-04-18 23:24:57.971 Current MythTV Schema Version (DBSchemaVer): 1264
2011-04-18 23:24:58.045 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-18 23:24:58.114 Enabling Upnpmedia rebuild thread.
2011-04-18 23:24:59.372 MythBackend: Starting up as the master server.
2011-04-18 23:24:59.600 New DB connection, total: 2
2011-04-18 23:24:59.662 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 23:25:00.217 New DB connection, total: 3
2011-04-18 23:25:00.382 Connected to database 'mythconverg' at host: 192.168.1.22
sh: /dev/ttyS0: Permission denied
2011-04-18 23:25:01.179 New DB scheduler connection
2011-04-18 23:25:01.341 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 23:25:01.510 Main::Registering HttpStatus Extension
2011-04-18 23:25:01.650 Enabled verbose msgs:  important general
2011-04-18 23:25:01.825 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-04-18 23:25:02.670 MainServer::ANN Monitor
2011-04-18 23:25:02.703 adding: mythserver as a client (events: 0)
2011-04-18 23:25:02.745 MainServer::ANN Monitor
2011-04-18 23:25:02.787 adding: mythserver as a client (events: 1)
2011-04-18 23:25:04.511 Reschedule requested for id -1.
2011-04-18 23:25:04.730 MainServer::ANN Monitor
2011-04-18 23:25:04.839 adding: mythserver as a client (events: 0)
2011-04-18 23:25:06.575 Scheduled 560 items in 2.1 = 0.28 match + 1.78 place
2011-04-18 23:25:06.634 Seem to be woken up by USER
2011-04-18 23:25:08.227 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-04-18 23:25:08.279 UPnpMedia: BuildMediaMap Done. Found 1 objects
2011-04-18 23:25:08.320 UPnpMedia: BuildMediaMap VIDEO scan starting in :/disk2/movies1:
2011-04-18 23:25:08.728 UPnpMedia: BuildMediaMap Done. Found 415 objects

```

The only changes I've made to this system recently were setting a static ip and configuring it to accept a remote frontend.  I don't understand how the permissions of /dev/ttyS0 could change.  I made it read/writeable for everyone just to test it but that didn't work either.  

The frontend log shows all kinds of errors too, server timeouts, backend time zone settings, all sorts of things I've never had before.  An important one looks to be the one about playback url & card buffer and ringbuffer, which I think can also lead to breaking viewing tv.  

Here's my frontend log:

```
Starting mythfrontend.real..
2011-04-18 22:33:42.940 mythfrontend version: fixes/0.24 [v0.24-248-g8c6ee70] www.mythtv.org
2011-04-18 22:33:42.940 Using runtime prefix = /usr
2011-04-18 22:33:42.940 Using configuration directory = /home/joe/.mythtv
2011-04-18 22:33:42.941 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-18 22:33:43.717 Empty LocalHostName.
2011-04-18 22:33:43.717 Using localhost value of mythserver
2011-04-18 22:33:43.717 Testing network connectivity to '192.168.1.22'
2011-04-18 22:33:43.839 New DB connection, total: 1
2011-04-18 22:33:43.840 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:33:43.844 Closing DB connection named 'DBManager0'
2011-04-18 22:33:43.850 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:33:43.851 Current locale en_US
2011-04-18 22:33:43.851 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-04-18 22:33:44.030 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-18 22:33:44.031 DPMS is disabled.
2011-04-18 22:33:44.039 Desktop video mode: 1920x1080 60.000 Hz
2011-04-18 22:33:44.053 Enabled verbose msgs:  important general
2011-04-18 22:33:44.055 Loading en_us translation for module mythfrontend
2011-04-18 22:33:44.066 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2011-04-18 22:33:44.066 JoystickMenuThread: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2011-04-18 22:33:44.207 Using Frameless Window
2011-04-18 22:33:44.210 Using Full Screen Window
2011-04-18 22:33:44.366 Using the Qt painter
2011-04-18 22:33:44.693 Current MythTV Schema Version (DBSchemaVer): 1264
2011-04-18 22:33:44.699 New DB connection, total: 2
2011-04-18 22:33:44.699 New DB connection, total: 3
2011-04-18 22:33:44.709 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:33:44.715 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:33:46.693 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-04-18 22:33:46.693 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-04-18 22:33:46.695 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-04-18 22:33:46.702 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-04-18 22:33:46.972 Registering Internal as a media playback plugin.
2011-04-18 22:33:46.990 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:33:46.991 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:33:46.991 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:33:46.991 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-18 22:33:46.991 Loading en_us translation for module mythgallery
2011-04-18 22:33:47.011 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-18 22:33:47.033 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-18 22:33:47.036 Loading en_us translation for module mythmusic
2011-04-18 22:33:47.043 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-04-18 22:33:47.053 Loading en_us translation for module mythvideo
2011-04-18 22:33:47.080 Starting update of yrno-XML
2011-04-18 22:33:47.087 yrno-XML recently updated, skipping.
2011-04-18 22:33:47.087 No cachefile for yrno-XML, forcing update.
2011-04-18 22:33:47.089 Starting update of BBC-Current-XML
2011-04-18 22:33:47.090 BBC-Current-XML recently updated, skipping.
2011-04-18 22:33:47.090 Loading en_us translation for module mythweather
2011-04-18 22:33:47.253 Found mainmenu.xml for theme 'Mythbuntu'
2011-04-18 22:33:47.432 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:33:47.432 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-04-18 22:33:47.432 Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
2011-04-18 22:33:49.112 'nice /usr/share/mythtv/mythweather/scripts/no_yrno/yrnoxml.pl -u ENG -d /home/joe/.mythtv/MythWeather/yrno-XML United_States/California/Los_Angeles' has exited
2011-04-18 22:34:01.390 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:34:01.390 Using protocol version 63
2011-04-18 22:34:01.577 TV: Attempting to change from None to WatchingLiveTV
2011-04-18 22:34:01.577 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:34:01.577 Using protocol version 63
2011-04-18 22:34:01.664 Spawning LiveTV Recorder -- begin
2011-04-18 22:34:02.287 Spawning LiveTV Recorder -- end
2011-04-18 22:34:02.290 We have a playbackURL(/var/lib/mythtv/livetv/1241_20110418223402.mpg) & cardtype(DUMMY)
2011-04-18 22:34:02.290 We have a RingBuffer
2011-04-18 22:34:02.465 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-04-18 22:34:02.490 OSD: Base theme size: 1280x720
2011-04-18 22:34:02.490 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:34:02.580 OSD: Base theme size: 1280x720
2011-04-18 22:34:02.580 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:34:02.583 Player(0): Video timing method: USleep with busy wait
2011-04-18 22:34:02.583 TV: Changing from None to WatchingLiveTV
2011-04-18 22:34:02.583 TV: State is LiveTV & mctx == ctx
2011-04-18 22:34:02.586 TV: UpdateOSDInput done
2011-04-18 22:34:02.586 TV: UpdateLCD done
2011-04-18 22:34:02.586 TV: ITVRestart done
2011-04-18 22:34:02.721 VideoOutput: Created YV12 OSD.
2011-04-18 22:34:09.860 OSD: Base theme size: 1280x720
2011-04-18 22:34:09.860 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:34:09.880 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-04-18 22:34:09.880 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-04-18 22:34:10.623 TV: OSDDialogEvent: result 0 text Exit Live TV action DIALOG_VIDEOEXIT_JUSTEXIT_0
2011-04-18 22:34:10.666 TV: Attempting to change from WatchingLiveTV to None
2011-04-18 22:34:10.709 TV: Changing from WatchingLiveTV to None
2011-04-18 22:34:14.583 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
Starting mythfrontend.real..
2011-04-18 22:37:08.658 mythfrontend version: fixes/0.24 [v0.24-248-g8c6ee70] www.mythtv.org
2011-04-18 22:37:08.658 Using runtime prefix = /usr
2011-04-18 22:37:08.659 Using configuration directory = /home/joe/.mythtv
2011-04-18 22:37:08.659 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-18 22:37:09.574 Empty LocalHostName.
2011-04-18 22:37:09.575 Using localhost value of mythserver
2011-04-18 22:37:09.575 Testing network connectivity to '192.168.1.22'
2011-04-18 22:37:09.686 New DB connection, total: 1
2011-04-18 22:37:09.688 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:37:09.693 Closing DB connection named 'DBManager0'
2011-04-18 22:37:09.694 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:37:09.695 Current locale en_US
2011-04-18 22:37:09.695 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-04-18 22:37:09.877 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-18 22:37:09.877 DPMS is disabled.
2011-04-18 22:37:09.887 Desktop video mode: 1920x1080 60.000 Hz
2011-04-18 22:37:09.901 Enabled verbose msgs:  important general
2011-04-18 22:37:09.903 Loading en_us translation for module mythfrontend
2011-04-18 22:37:09.908 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2011-04-18 22:37:09.908 JoystickMenuThread: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2011-04-18 22:37:09.936 Using Frameless Window
2011-04-18 22:37:09.936 Using Full Screen Window
2011-04-18 22:37:10.076 Using the Qt painter
2011-04-18 22:37:10.174 New DB connection, total: 2
2011-04-18 22:37:10.175 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:37:10.175 Current MythTV Schema Version (DBSchemaVer): 1264
2011-04-18 22:37:10.235 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-04-18 22:37:10.235 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-04-18 22:37:10.237 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-04-18 22:37:10.237 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-04-18 22:37:10.485 Registering Internal as a media playback plugin.
2011-04-18 22:37:10.510 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:37:10.511 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:37:10.511 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:37:10.511 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-18 22:37:10.512 Loading en_us translation for module mythgallery
2011-04-18 22:37:10.534 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-18 22:37:10.556 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-18 22:37:10.560 Loading en_us translation for module mythmusic
2011-04-18 22:37:10.570 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-04-18 22:37:10.584 Loading en_us translation for module mythvideo
2011-04-18 22:37:10.592 Starting update of yrno-XML
2011-04-18 22:37:10.593 yrno-XML recently updated, skipping.
2011-04-18 22:37:10.593 No cachefile for yrno-XML, forcing update.
2011-04-18 22:37:10.596 Starting update of BBC-Current-XML
2011-04-18 22:37:10.600 Loading en_us translation for module mythweather
2011-04-18 22:37:10.738 Found mainmenu.xml for theme 'Mythbuntu'
2011-04-18 22:37:10.900 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:37:10.907 Using protocol version 63
2011-04-18 22:37:11.429 'nice /usr/share/mythtv/mythweather/scripts/no_yrno/yrnoxml.pl -u ENG -d /home/joe/.mythtv/MythWeather/yrno-XML United_States/California/Los_Angeles' has exited
2011-04-18 22:37:11.746 'nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl -u ENG -d /home/joe/.mythtv/MythWeather/BBC-Current-XML 3439' has exited
2011-04-18 22:37:13.846 TV: Attempting to change from None to WatchingLiveTV
2011-04-18 22:37:13.846 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:37:13.846 Using protocol version 63
2011-04-18 22:37:13.946 Spawning LiveTV Recorder -- begin
2011-04-18 22:37:14.275 Spawning LiveTV Recorder -- end
2011-04-18 22:37:14.279 We have a playbackURL(/var/lib/mythtv/livetv/1241_20110418223714.mpg) & cardtype(DUMMY)
2011-04-18 22:37:14.279 We have a RingBuffer
2011-04-18 22:37:14.406 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-04-18 22:37:14.434 OSD: Base theme size: 1280x720
2011-04-18 22:37:14.434 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:37:14.462 OSD: Base theme size: 1280x720
2011-04-18 22:37:14.462 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:37:14.465 Player(0): Video timing method: USleep with busy wait
2011-04-18 22:37:14.465 TV: Changing from None to WatchingLiveTV
2011-04-18 22:37:14.465 TV: State is LiveTV & mctx == ctx
2011-04-18 22:37:14.468 TV: UpdateOSDInput done
2011-04-18 22:37:14.468 TV: UpdateLCD done
2011-04-18 22:37:14.468 TV: ITVRestart done
2011-04-18 22:37:14.550 VideoOutput: Created YV12 OSD.
2011-04-18 22:37:23.679 OSD: Base theme size: 1280x720
2011-04-18 22:37:23.679 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:37:23.688 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-04-18 22:37:23.688 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-04-18 22:37:24.169 TV: OSDDialogEvent: result -1 text  action DIALOG_VIDEOEXIT_KEEPWATCHING_0
2011-04-18 22:37:25.568 OSD: Base theme size: 1280x720
2011-04-18 22:37:25.568 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:37:25.573 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-04-18 22:37:25.573 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-04-18 22:37:26.295 TV: OSDDialogEvent: result 0 text Exit Live TV action DIALOG_VIDEOEXIT_JUSTEXIT_0
2011-04-18 22:37:26.338 TV: Attempting to change from WatchingLiveTV to None
2011-04-18 22:37:26.392 TV: Changing from WatchingLiveTV to None
2011-04-18 22:37:29.135 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2011-04-18 22:40:22.245 mythfrontend version: fixes/0.24 [v0.24-248-g8c6ee70] www.mythtv.org
2011-04-18 22:40:22.245 Using runtime prefix = /usr
2011-04-18 22:40:22.245 Using configuration directory = /home/joe/.mythtv
2011-04-18 22:40:22.246 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-18 22:40:22.910 Empty LocalHostName.
2011-04-18 22:40:22.910 Using localhost value of mythserver
2011-04-18 22:40:22.911 Testing network connectivity to '192.168.1.22'
2011-04-18 22:40:23.022 New DB connection, total: 1
2011-04-18 22:40:23.024 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:40:23.029 Closing DB connection named 'DBManager0'
2011-04-18 22:40:23.030 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:40:23.031 Current locale en_US
2011-04-18 22:40:23.031 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-04-18 22:40:23.213 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-18 22:40:23.213 DPMS is disabled.
2011-04-18 22:40:23.223 Desktop video mode: 1920x1080 60.000 Hz
2011-04-18 22:40:23.233 Enabled verbose msgs:  important general
2011-04-18 22:40:23.235 Loading en_us translation for module mythfrontend
2011-04-18 22:40:23.240 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2011-04-18 22:40:23.240 JoystickMenuThread: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2011-04-18 22:40:23.268 Using Frameless Window
2011-04-18 22:40:23.268 Using Full Screen Window
2011-04-18 22:40:23.413 Using the Qt painter
2011-04-18 22:40:23.510 New DB connection, total: 2
2011-04-18 22:40:23.510 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:40:23.511 Current MythTV Schema Version (DBSchemaVer): 1264
2011-04-18 22:40:23.569 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-04-18 22:40:23.569 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-04-18 22:40:23.572 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-04-18 22:40:23.572 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-04-18 22:40:23.821 Registering Internal as a media playback plugin.
2011-04-18 22:40:23.846 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:40:23.847 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:40:23.847 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:40:23.847 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-18 22:40:23.848 Loading en_us translation for module mythgallery
2011-04-18 22:40:23.873 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-18 22:40:23.895 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-18 22:40:23.899 Loading en_us translation for module mythmusic
2011-04-18 22:40:23.910 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-04-18 22:40:23.923 Loading en_us translation for module mythvideo
2011-04-18 22:40:23.932 Starting update of yrno-XML
2011-04-18 22:40:23.932 yrno-XML recently updated, skipping.
2011-04-18 22:40:23.932 No cachefile for yrno-XML, forcing update.
2011-04-18 22:40:23.936 Starting update of BBC-Current-XML
2011-04-18 22:40:23.936 BBC-Current-XML recently updated, skipping.
2011-04-18 22:40:23.936 Loading en_us translation for module mythweather
2011-04-18 22:40:24.076 Found mainmenu.xml for theme 'Mythbuntu'
2011-04-18 22:40:24.227 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:40:24.230 Using protocol version 63
2011-04-18 22:40:24.630 'nice /usr/share/mythtv/mythweather/scripts/no_yrno/yrnoxml.pl -u ENG -d /home/joe/.mythtv/MythWeather/yrno-XML United_States/California/Los_Angeles' has exited
2011-04-18 22:40:26.353 TV: Attempting to change from None to WatchingLiveTV
2011-04-18 22:40:26.353 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:40:26.354 Using protocol version 63
2011-04-18 22:40:26.440 Spawning LiveTV Recorder -- begin
2011-04-18 22:40:26.753 Spawning LiveTV Recorder -- end
2011-04-18 22:40:26.757 We have a playbackURL(/var/lib/mythtv/livetv/1241_20110418224026.mpg) & cardtype(DUMMY)
2011-04-18 22:40:26.757 We have a RingBuffer
2011-04-18 22:40:26.940 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-04-18 22:40:26.966 OSD: Base theme size: 1280x720
2011-04-18 22:40:26.966 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:40:26.995 OSD: Base theme size: 1280x720
2011-04-18 22:40:26.995 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:40:26.998 Player(0): Video timing method: USleep with busy wait
2011-04-18 22:40:26.998 TV: Changing from None to WatchingLiveTV
2011-04-18 22:40:26.998 TV: State is LiveTV & mctx == ctx
2011-04-18 22:40:27.001 TV: UpdateOSDInput done
2011-04-18 22:40:27.001 TV: UpdateLCD done
2011-04-18 22:40:27.001 TV: ITVRestart done
2011-04-18 22:40:27.075 VideoOutput: Created YV12 OSD.
2011-04-18 22:40:34.231 OSD: Base theme size: 1280x720
2011-04-18 22:40:34.231 OSD: Scaling factors: 0.5625x0.8
2011-04-18 22:40:34.239 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-04-18 22:40:34.240 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-04-18 22:40:35.143 TV: OSDDialogEvent: result 0 text Exit Live TV action DIALOG_VIDEOEXIT_JUSTEXIT_0
2011-04-18 22:40:35.188 TV: Attempting to change from WatchingLiveTV to None
2011-04-18 22:40:35.239 TV: Changing from WatchingLiveTV to None
2011-04-18 22:40:37.994 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2011-04-18 22:47:27.808 mythfrontend version: fixes/0.24 [v0.24-248-g8c6ee70] www.mythtv.org
2011-04-18 22:47:27.809 Using runtime prefix = /usr
2011-04-18 22:47:27.809 Using configuration directory = /home/joe/.mythtv
2011-04-18 22:47:27.809 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-18 22:47:28.256 Empty LocalHostName.
2011-04-18 22:47:28.256 Using localhost value of mythserver
2011-04-18 22:47:28.256 Testing network connectivity to '192.168.1.22'
2011-04-18 22:47:28.386 New DB connection, total: 1
2011-04-18 22:47:28.391 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:47:28.395 Closing DB connection named 'DBManager0'
2011-04-18 22:47:28.396 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:47:28.396 Current locale en_US
2011-04-18 22:47:28.396 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-04-18 22:47:28.567 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-18 22:47:28.583 DPMS is disabled.
2011-04-18 22:47:28.593 Desktop video mode: 1920x1080 60.000 Hz
2011-04-18 22:47:28.620 Enabled verbose msgs:  important general
2011-04-18 22:47:28.622 Loading en_us translation for module mythfrontend
2011-04-18 22:47:28.639 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2011-04-18 22:47:28.639 JoystickMenuThread: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2011-04-18 22:47:28.699 Using Frameless Window
2011-04-18 22:47:28.700 Using Full Screen Window
2011-04-18 22:47:28.910 Using the Qt painter
2011-04-18 22:47:29.121 New DB connection, total: 2
2011-04-18 22:47:29.121 Connected to database 'mythconverg' at host: 192.168.1.22
2011-04-18 22:47:29.122 Current MythTV Schema Version (DBSchemaVer): 1264
2011-04-18 22:47:33.315 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-04-18 22:47:33.315 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-04-18 22:47:33.331 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-04-18 22:47:33.331 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-04-18 22:47:33.612 Registering Internal as a media playback plugin.
2011-04-18 22:47:33.633 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:47:33.633 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:47:33.634 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-18 22:47:33.634 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-18 22:47:33.634 Loading en_us translation for module mythgallery
2011-04-18 22:47:33.655 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-18 22:47:33.680 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-18 22:47:33.683 Loading en_us translation for module mythmusic
2011-04-18 22:47:33.691 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-04-18 22:47:33.702 Loading en_us translation for module mythvideo
2011-04-18 22:47:33.719 Starting update of yrno-XML
2011-04-18 22:47:33.719 yrno-XML recently updated, skipping.
2011-04-18 22:47:33.719 No cachefile for yrno-XML, forcing update.
2011-04-18 22:47:33.721 Starting update of BBC-Current-XML
2011-04-18 22:47:33.722 BBC-Current-XML recently updated, skipping.
2011-04-18 22:47:33.722 Loading en_us translation for module mythweather
2011-04-18 22:47:33.853 Found mainmenu.xml for theme 'Mythbuntu'
2011-04-18 22:47:34.049 MythCoreContext: Connecting to backend server: 192.168.1.22:6543 (try 1 of 1)
2011-04-18 22:47:34.050 Using protocol version 63
2011-04-18 22:47:34.369 'nice /usr/share/mythtv/mythweather/scripts/no_yrno/yrnoxml.pl -u ENG -d /home/joe/.mythtv/MythWeather/yrno-XML United_States/California/Los_Angeles' has exited
2011-04-18 22:48:18.185 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
```


 
I'm stuck here, so thank you very much for any guidance.

---

### Post by azmyth on 2011-04-26
Changing permissions on dev links is tricky as they either don't work or they don't stick. I've gone through this with modems and printers. The best thing to do is set a udev rule and then you won't have to worry about it. If you don't want to do that, then you should add user(s) to the dialout group to have permission to use the ttyS0.

---

### Post by phroman on 2011-04-26
Did a fresh install, didn't really have any media to save to wasn't a big deal.  I downloaded an updated channel change script, and edited my channel change script line in the backend, everything is working now.  Thanks.

---

