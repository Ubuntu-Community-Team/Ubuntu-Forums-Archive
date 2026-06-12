---
title: "HVR 1600 Analog Displaying Static"
date: 2010-12-27
forum: Mythbuntu
---

### Post by defo1 on 2010-12-27
Hi all,

I'm having an issue with my mythbuntu 10.04 install (Mythtv version 0.23.0+fixes24158-0ubuntu2).  I tried to set up the analog side of my hvr 1600 as follows:  

I made a new IVTV MPEG2 capture card as /dev/video0 (default input is Tuner 1).  Then I made a new video source named Analog with my SchedulesDirect info/lineup. 

When I try set the input Tuner 1 of /dev/video0 to the video source called Analog and scan for channels, nothing is found.  Fetching channels from listing appears to work, as after doing that, I can choose a starting channel from a list of ~80 channels.  However, once I exit the backend setup and try to watch tv on the frontend, every channel just shows [static like this]("http://i.imgur.com/GAvV5.png"). 

Here's my mythfrontend.log-
```
Starting mythfrontend.real..
2010-12-27 21:23:12.225 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-12-27 21:23:12.225 Using runtime prefix = /usr
2010-12-27 21:23:12.226 Using configuration directory = /home/myth/.mythtv
2010-12-27 21:23:13.040 Empty LocalHostName.
2010-12-27 21:23:13.040 Using localhost value of mythbox
2010-12-27 21:23:13.048 New DB connection, total: 1
2010-12-27 21:23:13.052 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:13.053 Closing DB connection named 'DBManager0'
2010-12-27 21:23:13.069 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-27 21:23:13.071 DPMS is disabled.
2010-12-27 21:23:13.072 Primary screen: 0.
2010-12-27 21:23:13.073 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:13.075 Using screen 0, 800x600 at 0,0
2010-12-27 21:23:13.092 Desktop video mode: 800x600 60.3173 Hz
2010-12-27 21:23:13.111 MythUI Image Cache size set to 20971520 bytes
2010-12-27 21:23:13.138 AudioPulseUtil: Suspend Success
2010-12-27 21:23:13.139 Enabled verbose msgs:  important general
2010-12-27 21:23:13.146 Primary screen: 0.
2010-12-27 21:23:13.147 Using screen 0, 800x600 at 0,0
2010-12-27 21:23:13.148 Using theme base resolution of 800x600
2010-12-27 21:23:13.155 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-27 21:23:13.155 JoystickMenuThread Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2010-12-27 21:23:13.196 Using Frameless Window
2010-12-27 21:23:13.196 Using Full Screen Window
2010-12-27 21:23:13.246 Using the OpenGL painter
2010-12-27 21:23:13.517 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Arial'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 985
            Name: 'small'    Type: 'font'
2010-12-27 21:23:13.533 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 991
            Name: 'medium'    Type: 'font'
2010-12-27 21:23:13.547 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 997
            Name: 'large'    Type: 'font'
2010-12-27 21:23:13.554 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1003
            Name: 'clock'    Type: 'font'
2010-12-27 21:23:13.556 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-27 21:23:13.568 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-27 21:23:13.574 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-27 21:23:14.231 Registering Internal as a media playback plugin.
2010-12-27 21:23:14.259 Cannot load language en_us for module mytharchive
2010-12-27 21:23:14.262 Cannot load language en_us for module mythbrowser
2010-12-27 21:23:14.266 Registering WebBrowser as a media playback plugin.
2010-12-27 21:23:14.266 Cannot load language en_us for module mythbrowser
2010-12-27 21:23:14.300 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-27 21:23:14.300 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-27 21:23:14.301 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-27 21:23:14.302 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-27 21:23:14.302 Cannot load language en_us for module mythgallery
2010-12-27 21:23:14.310 Cannot load language en_us for module mythgame
2010-12-27 21:23:14.313 Cannot load language en_us for module mythmovies
2010-12-27 21:23:14.335 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-27 21:23:14.387 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-27 21:23:14.395 Cannot load language en_us for module mythmusic
2010-12-27 21:23:14.405 Cannot load language en_us for module mythnetvision
2010-12-27 21:23:14.411 Cannot load language en_us for module mythnews
2010-12-27 21:23:14.420 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-27 21:23:14.452 Cannot load language en_us for module mythvideo
2010-12-27 21:23:14.459 Cannot load language en_us for module mythweather
2010-12-27 21:23:14.462 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-27 21:23:14.672 Loading menu theme from /home/myth/.mythtv/mainmenu.xml
2010-12-27 21:23:14.676 Found mainmenu.xml for theme 'MythCenter'
2010-12-27 21:23:14.740 Using NV NPOT texture extension
2010-12-27 21:23:14.787 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-27 21:23:14.789 Using protocol version 56
2010-12-27 21:23:15.906 TV: Attempting to change from None to WatchingLiveTV
2010-12-27 21:23:15.906 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-27 21:23:15.907 Using protocol version 56
2010-12-27 21:23:15.908 Spawning LiveTV Recorder -- begin
2010-12-27 21:23:16.003 Spawning LiveTV Recorder -- end
2010-12-27 21:23:16.006 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:16.011 We have a playbackURL(/recordings/Live TV/1005_20101227212315.mpg) & cardtype(MPEG)
2010-12-27 21:23:16.646 We have a RingBuffer
2010-12-27 21:23:17.461 AFD: Opened codec 0xac87cf60, id(MPEG2VIDEO) type(Video)
2010-12-27 21:23:17.462 AFD: codec MP2 has 2 channels
2010-12-27 21:23:17.462 AFD: Opened codec 0xac87d9a0, id(MP2) type(Audio)
2010-12-27 21:23:17.599 AO: Using resampler. From: 32000 to 48000
2010-12-27 21:23:17.599 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-27 21:23:17.599 Opening ALSA audio device 'default'.
2010-12-27 21:23:17.619 AO: Using resampler. From: 32000 to 48000
2010-12-27 21:23:17.619 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-27 21:23:17.619 Opening ALSA audio device 'default'.
2010-12-27 21:23:17.643 AO: Using resampler. From: 32000 to 48000
2010-12-27 21:23:17.643 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-27 21:23:17.644 Opening ALSA audio device 'default'.
2010-12-27 21:23:17.673 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-12-27 21:23:17.698 New DB connection, total: 2
2010-12-27 21:23:17.699 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:17.700 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:17.704 OSD Theme Dimensions W: 1280 H: 720
2010-12-27 21:23:17.757 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:17.814 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:17.859 TV: Changing from None to WatchingLiveTV
2010-12-27 21:23:17.861 Realtime priority would require SUID as root.
2010-12-27 21:23:17.860 TV: State is LiveTV & mctx == ctx
2010-12-27 21:23:17.862 TV: UpdateOSDInput done
2010-12-27 21:23:17.862 TV: UpdateLCD done
2010-12-27 21:23:17.863 TV: ITVRestart done
2010-12-27 21:23:17.869 Video timing method: USleep with busy wait
2010-12-27 21:23:17.871 [mpeg2video @ 0x3f68960]warning: first frame is no keyframe
2010-12-27 21:23:17.879 [mpeg2video @ 0x3f68960]warning: first frame is no keyframe
2010-12-27 21:23:24.395 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:24.401 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.674 [mp2 @ 0x3f68960]incomplete frame
2010-12-27 21:23:26.675 AFD Error: Unknown audio decoding error
2010-12-27 21:23:26.922 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:26.931 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:27.490 WriteAudio: buffer underrun
2010-12-27 21:23:31.197 TV: Attempting to change from WatchingLiveTV to None
2010-12-27 21:23:31.871 TV: Changing from WatchingLiveTV to None
2010-12-27 21:23:35.662 AudioPulseUtil: Resume Success
2010-12-27 21:23:35.662 Deleting UPnP client...

```And mythbackend.log-

```
2010-12-27 21:23:14.790 MainServer::ANN Monitor
2010-12-27 21:23:14.791 adding: mythbox as a client (events: 0)
2010-12-27 21:23:14.792 MainServer::ANN Monitor
2010-12-27 21:23:14.792 adding: mythbox as a client (events: 1)
2010-12-27 21:23:15.907 MainServer::ANN Playback
2010-12-27 21:23:15.907 adding: mythbox as a client (events: 0)
2010-12-27 21:23:15.910 TVRec(1): Changing from None to WatchingLiveTV
2010-12-27 21:23:15.913 TVRec(1): HW Tuner: 1->1
2010-12-27 21:23:15.996 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:16.003 

Not ivtv or pvrusb2 or hdpvr driver


2010-12-27 21:23:16.008 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-12-27 21:23:16.040 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:16.060 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:17.624 RecBase(1:/dev/video0): GetKeyframePositions(16,9223372036854775807,#1) out of 3
2010-12-27 21:23:17.755 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:17.812 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:17.867 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.160 TVRec(1): HW Tuner: 1->1
2010-12-27 21:23:24.319 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.321 Finished recording Charlie and the Chocolate Factory: channel 1005
2010-12-27 21:23:24.323 scheduler: Finished recording: Charlie and the Chocolate Factory: channel 1005
2010-12-27 21:23:24.339 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.341 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.343 Finished recording Charlie and the Chocolate Factory: channel 1005
2010-12-27 21:23:24.362 TVRec(1): RingBufferChanged()
2010-12-27 21:23:24.365 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.368 Finished recording Charlie and the Chocolate Factory: channel 1005
2010-12-27 21:23:24.368 ProgramInfo(1005_20101227212315.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2010-12-27 21:23:24.369 ProgramInfo(1005_20101227212315.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2010-12-27 21:23:24.391 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-12-27 21:23:24.398 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.403 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:24.449 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:24.452 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:24.510 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-12-27 21:23:24.511 Using runtime prefix = /usr
2010-12-27 21:23:24.512 Using configuration directory = /home/mythtv/.mythtv
2010-12-27 21:23:24.513 Empty LocalHostName.
2010-12-27 21:23:24.513 Using localhost value of mythbox
2010-12-27 21:23:24.523 New DB connection, total: 1
2010-12-27 21:23:24.527 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:24.527 Closing DB connection named 'DBManager0'
2010-12-27 21:23:24.528 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:24.533 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-27 21:23:24.535 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:23:26.681 TVRec(1): HW Tuner: 1->1
2010-12-27 21:23:26.817 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.820 Finished recording NECN Tonight: channel 1006
2010-12-27 21:23:26.822 scheduler: Last message repeated 2 times: Finished recording: Charlie and the Chocolate Factory: channel 1005
2010-12-27 21:23:26.825 scheduler: Finished recording: NECN Tonight: channel 1006
2010-12-27 21:23:26.840 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.842 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.846 Finished recording NECN Tonight: channel 1006
2010-12-27 21:23:26.905 TVRec(1): RingBufferChanged()
2010-12-27 21:23:26.908 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.911 Finished recording NECN Tonight: channel 1006
2010-12-27 21:23:26.912 ProgramInfo(1006_20101227212324.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2010-12-27 21:23:26.912 ProgramInfo(1006_20101227212324.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2010-12-27 21:23:26.924 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-12-27 21:23:26.930 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:26.935 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.955 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:26.976 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:26.979 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:27.014 AFD: Opened codec 0x951d450, id(MPEG2VIDEO) type(Video)
2010-12-27 21:23:27.015 AFD: codec MP2 has 2 channels
2010-12-27 21:23:27.015 AFD: Opened codec 0x9522550, id(MP2) type(Audio)
2010-12-27 21:23:27.028 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-12-27 21:23:27.029 Using runtime prefix = /usr
2010-12-27 21:23:27.030 Using configuration directory = /home/mythtv/.mythtv
2010-12-27 21:23:27.034 Empty LocalHostName.
2010-12-27 21:23:27.034 Using localhost value of mythbox
2010-12-27 21:23:27.055 New DB connection, total: 1
2010-12-27 21:23:27.065 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:27.066 Closing DB connection named 'DBManager0'
2010-12-27 21:23:27.078 [mpeg2video @ 0x1a18960]warning: first frame is no keyframe
2010-12-27 21:23:27.102 Connected to database 'mythconverg' at host: localhost
2010-12-27 21:23:27.108 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-27 21:23:27.111 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:23:27.158 Preview: Grabbed preview '/recordings/Live TV/1005_20101227212315.mpg' 480x480@64s
2010-12-27 21:23:27.281 ~MythContext waiting for threads to exit.
2010-12-27 21:23:27.289 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.289 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.290 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.303 [mp2 @ 0x1cb2960]Header missing
2010-12-27 21:23:27.304 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.308 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.308 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.308 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.309 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:27.309 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.723 AFD: Opened codec 0x8f2d950, id(MPEG2VIDEO) type(Video)
2010-12-27 21:23:29.724 AFD: codec MP2 has 2 channels
2010-12-27 21:23:29.724 AFD: Opened codec 0x8f3baf0, id(MP2) type(Audio)
2010-12-27 21:23:29.800 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.809 AFD Error: Unknown decoding error
2010-12-27 21:23:29.810 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.810 AFD Error: Unknown decoding error
2010-12-27 21:23:29.815 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.815 AFD Error: Unknown decoding error
2010-12-27 21:23:29.815 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.815 AFD Error: Unknown decoding error
2010-12-27 21:23:29.816 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.816 AFD Error: Unknown decoding error
2010-12-27 21:23:29.816 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.817 AFD Error: Unknown decoding error
2010-12-27 21:23:29.817 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.817 AFD Error: Unknown decoding error
2010-12-27 21:23:29.817 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.818 AFD Error: Unknown decoding error
2010-12-27 21:23:29.818 [mpeg2video @ 0x1cb2960]mpeg_decode_postinit() failure
2010-12-27 21:23:29.818 AFD Error: Unknown decoding error
2010-12-27 21:23:29.913 Preview: Grabbed preview '/recordings/Live TV/1006_20101227212324.mpg' 480x480@64s
2010-12-27 21:23:30.063 ~MythContext waiting for threads to exit.
2010-12-27 21:23:31.219 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:31.220 TVRec(1): Changing from WatchingLiveTV to None
2010-12-27 21:23:31.221 ProgramInfo(1007_20101227212326.mpg), Error: Unknown type, recording width was 0
2010-12-27 21:23:31.860 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:31.863 Finished recording Chuck "Chuck Versus the Aisle of Terror": channel 1007
2010-12-27 21:23:31.865 scheduler: Last message repeated 2 times: Finished recording: NECN Tonight: channel 1006
2010-12-27 21:23:31.868 scheduler: Finished recording: Chuck "Chuck Versus the Aisle of Terror": channel 1007
2010-12-27 21:23:31.920 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:23:31.994 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:24:45.473 Expiring 4 MBytes for 1005 @ Mon Dec 27 20:00:00 2010 => Charlie and the Chocolate Factory
2010-12-27 21:24:45.475 autoexpire: Expiring Program: Expiring 4 MBytes for 1005 @ Mon Dec 27 20:00:00 2010 => Charlie and the Chocolate Factory
2010-12-27 21:24:45.475 Expiring 1 MBytes for 1006 @ Mon Dec 27 21:00:00 2010 => NECN Tonight
2010-12-27 21:24:45.477 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:24:45.477 autoexpire: Expiring Program: Expiring 1 MBytes for 1006 @ Mon Dec 27 21:00:00 2010 => NECN Tonight
2010-12-27 21:24:45.482 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:24:45.532 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:24:45.534 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:24:48.482 ProgramInfo(): Updated pathname '':'' -> '1005_20101227212315.mpg'
2010-12-27 21:24:52.492 ProgramInfo(): Updated pathname '':'' -> '1006_20101227212324.mpg'
2010-12-27 21:26:45.483 Expiring 2 MBytes for 1007 @ Mon Dec 27 21:00:00 2010 => Chuck "Chuck Versus the Aisle of Terror"
2010-12-27 21:26:45.485 autoexpire: Expiring Program: Expiring 2 MBytes for 1007 @ Mon Dec 27 21:00:00 2010 => Chuck "Chuck Versus the Aisle of Terror"
2010-12-27 21:26:45.488 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:26:45.542 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'
2010-12-27 21:26:48.493 ProgramInfo(): Updated pathname '':'' -> '1007_20101227212326.mpg'

```Any ideas on how to fix this?

---

### Post by zepfan on 2010-12-27
Stupid question, but do you have cable plugged into both ports?

---

### Post by defo1 on 2010-12-27
I have cable plugged into the 'TV' port on the card.  I'm assuming that's the analog half, as the other port is labeled 'ATSC'.

---

### Post by defo1 on 2010-12-28
Nobody has any ideas?

---

### Post by thatguruguy on 2010-12-28
Who is your cable carrier?

---

### Post by defo1 on 2010-12-29
Comcast.

---

### Post by thatguruguy on 2010-12-29
> **defo1 said:**
> Comcast.

Well, there's your problem. 

Your tuner is working fine. Comcast is transitioning to full digital. In most markets, they are no longer transmitting any analog signals.  The reason you're seeing static is that there is no analog signal to decode.

---

### Post by defo1 on 2010-12-29
I don't think that's the case. I have my cable split into two wires, one going directly into an old tube TV, and one into the hvr 1600.  My tube TV can get ~22 channels, which leads me to believe it's not all digital, yet.

But, I'll try setting up the digital half of the card to see if that makes a difference.

---

### Post by klc5555 on 2010-12-29
> **defo1 said:**
> I don't think that's the case. I have my cable split into two wires, one going directly into an old tube TV, and one into the hvr 1600.  My tube TV can get ~22 channels, which leads me to believe it's not all digital, yet.

But, I'll try setting up the digital half of the card to see if that makes a difference.

There are many versions of the analog tuner used in the various flavors of the 1600. The cx18 driver in 10.04 is a bit old, and may not have detected your precise tuner correctly. dmesg may return a line something like this:

[   27.037268] cx18-0: tveeprom cannot autodetect tuner!

in which case you have a couple of options. You can run Iglenn's little script, found in message #16 of this thread here: [http://ubuntuforums.org/showthread.php?t=1498620&highlight=1600+script](http://ubuntuforums.org/showthread.php?t=1498620&highlight=1600+script) 
It will find which exact tuner you have if the cx18 cannot identify it, so that you may pass the correct tuner parameter to the cx18 module at boot.

Or you can compile and install a recent snapshot of the driver source as found at linuxtv.org as I believe the identification issue has been resolved in currentish cx18s.

For the analog channels 2-99 (whichever ones Comcast still has in your area --most likely 2-22 maximum, and soon to be zippo), you do not actually need to scan with the 1600 and Mythtv. A specific channel may be added to a Video Source manually in the backend setup with the Channel Editor.

---

### Post by defo1 on 2010-12-29
Dmesg returns a line similar to the one you mentioned (tuner 1-0061: tuner type not set), so I tried using Iglenn's script to find out exactly which tuner I have.  I wasn't able to determine my tuner type from it, because it returns the following line, repeated sequentially:
```
Tuner type 1: FATAL: Module cx18_alsa is in use.
FATAL: Module cx18 is in use.
    Signal strength/AFC  : 0%/-187500

```I tried removing those modules via rmmod and modprobe -rf, but neither worked, as they were still in use.

Here's part of my dmesg output, starting where I thought it was relevant:
```

[   23.038834] cx18:  Start initialization, version 1.4.0
[   23.038885] cx18-0: Initializing card 0
[   23.038890] cx18-0: Autodetected Hauppauge card
[   23.039025] cx18 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.039040] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   23.041633] cx18-0: cx23418 revision 01010000 (B)
[   23.263422] tveeprom 0-0050: Hauppauge model 74041, rev C6G8, serial# 7271201
[   23.263430] tveeprom 0-0050: MAC address is 00:0d:fe:6e:f3:21
[   23.263436] tveeprom 0-0050: tuner model is unknown (idx 168, type 4)
[   23.263442] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   23.263449] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   23.263456] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   23.263461] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   23.263466] cx18-0: Autodetected Hauppauge HVR-1600
[   23.263470] cx18-0: tveeprom cannot autodetect tuner!
[   23.263713] cx18-0: Simultaneous Digital and Analog TV capture supported
[   23.358729] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   23.575975] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   23.593359] tda9887 1-0043: creating new instance
[   23.593363] tda9887 1-0043: tda988[5/6/7] found
[   23.596365] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   23.672388] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   23.675168] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   23.675174] DVB: registering new adapter (cx18)
[   23.854081] MXL5005S: Attached at address 0x63
[   23.854090] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   23.854262] cx18-0: DVB Frontend registered
[   23.854268] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   23.854337] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   23.854395] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   23.854451] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   23.854457] cx18-0: Initialized card: Hauppauge HVR-1600
[   23.854506] cx18:  End initialization
[   23.865393] C-Media PCI 0000:05:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   23.884867] cx18-alsa: module loading...
[   23.900870] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   24.173025] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   24.230827] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-apu.fw
[   24.418865] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   24.419248] EXT3 FS on sda1, internal journal
[   24.425810] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   24.632559] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   24.768029] kjournald starting.  Commit interval 5 seconds
[   24.768405] EXT3 FS on sda5, internal journal
[   24.768412] EXT3-fs: mounted filesystem with ordered data mode.
[   24.898237] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-apu.fw
[   25.067457] type=1505 audit(1293658267.971:6):  operation="profile_replace" pid=796 name="/sbin/dhclient3"
[   25.068324] type=1505 audit(1293658267.975:7):  operation="profile_replace" pid=796 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.075416] type=1505 audit(1293658267.979:8):  operation="profile_replace" pid=796 name="/usr/lib/connman/scripts/dhclient-script"
[   25.104016] type=1505 audit(1293658268.011:9):  operation="profile_load" pid=806 name="/usr/sbin/mysqld"
[   25.116147] type=1505 audit(1293658268.023:10):  operation="profile_load" pid=797 name="/usr/bin/evince"
[   25.120163] type=1505 audit(1293658268.027:11):  operation="profile_replace" pid=811 name="/usr/sbin/ntpd"
[   25.187118]   alloc irq_desc for 27 on node -1
[   25.187133]   alloc kstat_irqs on node -1
[   25.187154] tg3 0000:3f:00.0: irq 27 for MSI/MSI-X
[   25.244050] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   25.245088] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.442191] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-dig.fw
[   25.629233] svc: failed to register lockdv1 RPC service (errno 97).
[   25.633919] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   25.651359] NFSD: starting 90-second grace period
[   25.666304] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   25.687587] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   25.689133] tuner 1-0061: tuner type not set
[   25.690079] tuner 1-0061: tuner type not set
[   26.086811] CPU0 attaching NULL sched-domain.
[   26.086821] CPU1 attaching NULL sched-domain.
[   26.108113] CPU0 attaching sched-domain:
[   26.108120]  domain 0: span 0-1 level SIBLING
[   26.108125]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   26.108137]   domain 1: span 0-1 level MC
[   26.108142]    groups: 0-1 (cpu_power = 1178)
[   26.108152] CPU1 attaching sched-domain:
[   26.108157]  domain 0: span 0-1 level SIBLING
[   26.108161]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   26.108172]   domain 1: span 0-1 level MC
[   26.108177]    groups: 0-1 (cpu_power = 1178)
[   26.846774] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   26.846780] tg3: eth0: Flow control is on for TX and on for RX.
[   28.492816] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.980383] tuner 1-0061: tuner type not set
[   39.004020] eth0: no IPv6 routers present

```I'm at a loss of what to do next.

---

### Post by klc5555 on 2010-12-30
Be sure that you have killed the backend prior to running the script (ubuntu is fussier than some distros about what you're allowed to do with the backend running), and that you're running the script sudo. Or if you rmmod by hand you do it sudo.

Otherwise, there's been a lot of good work on the cx18 driver during all of 2010. Quite astonishing really, in regards to both analog and digital performance. Autodetection for certain analog tuners was added as recently as 7/22. You might do well to download, compile, and install a new set of V4L/DVB drivers from [http://linuxtv.org/downloads/](http://linuxtv.org/downloads/)

---

### Post by thatguruguy on 2010-12-30
If I'm not mistaken, tvtime is still available via synaptic.

tvtime seems to have a much easier time auto-configuring itself and finding analog channels (although it doesn't work for digital).  You may want to install it and try to watch tv with it, which will let you know if you're getting any analog signal through your tuner.

---

### Post by klc5555 on 2010-12-30
> **thatguruguy said:**
> If I'm not mistaken, tvtime is still available via synaptic.

tvtime seems to have a much easier time auto-configuring itself and finding analog channels (although it doesn't work for digital).  You may want to install it and try to watch tv with it, which will let you know if you're getting any analog signal through your tuner.

This would normally be reasonable, had the OP's dmesg output not indicated that his cx18 tveeprom could not identify the analog tuner at boot and accordingly could not load with the correct parameter set. The cx18_alsa and cx18 kernel modules have to be unloaded and the cx18 loaded with the correct 'tuner=X' parameter before the analog tuner will pull in anything for any application, including tvtime. The correct 'X' can be determined through automatic detection by a current edition of the cx18 driver, or determined by brute force using something like Iglen's script which tries every 'tuner=X' possibility in sequence (at least from 1-84) Hopefully, one clicks that properly initializes the tuner and gives good analog signal strength. This, then, is set in an 'options.conf' file for modprobe.d or added to a modprobe line in the rc.local, whichever way the OP prefers to set the module to load at boot. 

The Mythbuntu problem here is not in the Myth, it's in the 'buntu.

---

### Post by defo1 on 2010-12-30
I compiled the latest V4L drivers, but that didn't fix the problem with identifying the tuner.  

I still can't seem to unload cx18 and cx18_alsa even with sudo and stopping the backend , as they are always "in use".  So, I blacklisted these modules using blacklist.conf, and then tried running the script. Blacklisting them made the test for tuner=1 work, but they couldn't be unloaded for the rest of them, so I was unable to find out my tuner type. 

However, I searched around, and found that some people had success using tuner=71 with the hvr-1600, so I tried that one.  I was able scan and find 2 channels from that, but they were mis-numbered.  On my tube TV channels 2 and 3 are WGBH and HSN, but on MythTV channels 2 and 3 are some Spanish channels. (channels 17 and 19 on my tube TV). The tv guide for channels 2 and 3 on MythTV shows WGBH's and HSN's guides, not the Spanish programs that are actually playing.  


edit:Here's dmesg with the latest drivers without 'options cx18 tuner=71' in the options.conf

```
[   20.270904] Linux video capture interface: v2.00
[   20.270910] WARNING: You're using an experimental version of the V4L stack. As the driver
[   20.270913]          is backported to an older kernel, it doesn't offer enough quality for
[   20.270916]          its usage in production.
[   20.270918]          Use it with care.
[   20.301792] lirc_dev: lirc_register_driver: sample_rate: 0
[   20.306778] lirc_mceusb[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
[   20.306830] usbcore: registered new interface driver lirc_mceusb
[   20.579366] WARNING: You're using an experimental version of the DVB stack. As the driver
[   20.579370]          is backported to an older kernel, it doesn't offer enough quality for
[   20.579372]          its usage in production.
[   20.579374]          Use it with care.
[   20.688858] cx18:  Start initialization, version 1.4.0
[   20.688920] cx18-0: Initializing card 0
[   20.688925] cx18-0: Autodetected Hauppauge card
[   20.689062] cx18 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.689077] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   20.691402] cx18-0: cx23418 revision 01010000 (B)
[   20.911285] tveeprom 0-0050: Hauppauge model 74041, rev C6G8, serial# 7271201
[   20.911291] tveeprom 0-0050: MAC address is 00:0d:fe:6e:f3:21
[   20.911295] tveeprom 0-0050: tuner model is unknown (idx 168, type 4)
[   20.911299] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   20.911302] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   20.911306] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   20.911309] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   20.911312] cx18-0: Autodetected Hauppauge HVR-1600
[   20.911315] cx18-0: tveeprom cannot autodetect tuner!
[   20.911550] cx18-0: Simultaneous Digital and Analog TV capture supported
[   21.007432] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.350754] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   21.437394] tda9887 1-0043: creating new instance
[   21.437403] tda9887 1-0043: tda988[5/6/7] found
[   21.444345] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   21.477541] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   21.481497] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   21.481504] DVB: registering new adapter (cx18)
[   21.709752] EXT3 FS on sda1, internal journal
[   21.729600] MXL5005S: Attached at address 0x63
[   21.729616] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   21.729836] cx18-0: DVB Frontend registered
[   21.729843] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   21.729911] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   21.729999] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   21.730067] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   21.730073] cx18-0: Initialized card: Hauppauge HVR-1600
[   21.730137] cx18:  End initialization
[   21.730422] C-Media PCI 0000:05:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.900129] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   21.918761] cx18-alsa: module loading...
[   22.100625] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   22.127020] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-apu.fw
[   22.232841] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   22.239230] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   22.300621] kjournald starting.  Commit interval 5 seconds
[   22.300860] EXT3 FS on sda5, internal journal
[   22.300867] EXT3-fs: mounted filesystem with ordered data mode.
[   22.452047] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   22.479588] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   22.517782] type=1505 audit(1293758626.423:6):  operation="profile_load" pid=801 name="/usr/bin/evince"
[   22.527598] type=1505 audit(1293758626.431:7):  operation="profile_load" pid=801 name="/usr/bin/evince-previewer"
[   22.534598] type=1505 audit(1293758626.439:8):  operation="profile_load" pid=801 name="/usr/bin/evince-thumbnailer"
[   22.554798] type=1505 audit(1293758626.459:9):  operation="profile_load" pid=805 name="/usr/sbin/mysqld"
[   22.563667] type=1505 audit(1293758626.467:10):  operation="profile_replace" pid=806 name="/usr/sbin/ntpd"
[   22.571587] type=1505 audit(1293758626.475:11):  operation="profile_replace" pid=800 name="/sbin/dhclient3"
[   22.626739]   alloc irq_desc for 27 on node -1
[   22.626746]   alloc kstat_irqs on node -1
[   22.626773] tg3 0000:3f:00.0: irq 27 for MSI/MSI-X
[   22.688381] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.697571] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-apu.fw
[   23.026407] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-dig.fw
[   23.051519] svc: failed to register lockdv1 RPC service (errno 97).
[   23.053881] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   23.065260] NFSD: starting 90-second grace period
[   23.229196] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   23.251550] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   23.253116] tuner 1-0061: tuner type not set
[   23.254102] tuner 1-0061: tuner type not set
[   23.475912] CPU0 attaching NULL sched-domain.
[   23.475922] CPU1 attaching NULL sched-domain.
[   23.496116] CPU0 attaching sched-domain:
[   23.496122]  domain 0: span 0-1 level SIBLING
[   23.496128]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   23.496140]   domain 1: span 0-1 level MC
[   23.496145]    groups: 0-1 (cpu_power = 1178)
[   23.496156] CPU1 attaching sched-domain:
[   23.496160]  domain 0: span 0-1 level SIBLING
[   23.496165]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   23.496176]   domain 1: span 0-1 level MC
[   23.496181]    groups: 0-1 (cpu_power = 1178)
[   24.286499] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   24.286504] tg3: eth0: Flow control is on for TX and on for RX.
[   25.986810] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.573205] tuner 1-0061: tuner type not set
[   26.584362] tuner 1-0061: tuner type not set
[   36.084068] eth0: no IPv6 routers present

```Here's dmesg with the latest drivers **with** 'options cx18 tuner=71' in the options.conf

```

[   19.129232] Linux video capture interface: v2.00
[   19.129238] WARNING: You're using an experimental version of the V4L stack. As the driver
[   19.129241]          is backported to an older kernel, it doesn't offer enough quality for
[   19.129243]          its usage in production.
[   19.129245]          Use it with care.
[   19.200240] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.200256] nvidia 0000:01:00.0: setting latency timer to 64
[   19.200265] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.200475] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   19.349166] Console: switching to colour frame buffer device 80x30
[   19.612407] RPC: Registered udp transport module.
[   19.612413] RPC: Registered tcp transport module.
[   19.612417] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   19.640154] WARNING: You're using an experimental version of the DVB stack. As the driver
[   19.640158]          is backported to an older kernel, it doesn't offer enough quality for
[   19.640161]          its usage in production.
[   19.640163]          Use it with care.
[   19.742258] cx18:  Start initialization, version 1.4.0
[   19.742310] cx18-0: Initializing card 0
[   19.742316] cx18-0: Autodetected Hauppauge card
[   19.742478] cx18 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.742494] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   19.743904] cx18-0: cx23418 revision 01010000 (B)
[   19.963476] tveeprom 0-0050: Hauppauge model 74041, rev C6G8, serial# 7271201
[   19.963482] tveeprom 0-0050: MAC address is 00:0d:fe:6e:f3:21
[   19.963486] tveeprom 0-0050: tuner model is unknown (idx 168, type 4)
[   19.963490] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   19.963494] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   19.963497] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   19.963501] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   19.963504] cx18-0: Autodetected Hauppauge HVR-1600
[   19.963507] cx18-0: tveeprom cannot autodetect tuner!
[   19.963743] cx18-0: Simultaneous Digital and Analog TV capture supported
[   20.058217] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   20.201871] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   20.483724] tda9887 1-0043: creating new instance
[   20.483731] tda9887 1-0043: tda988[5/6/7] found
[   20.489855] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   20.521030] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   20.578419] xc2028 1-0061: creating new instance
[   20.578426] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   20.579089] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   20.579106] DVB: registering new adapter (cx18)
[   20.644286] EXT3 FS on sda1, internal journal
[   20.773381] MXL5005S: Attached at address 0x63
[   20.773401] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   20.773653] cx18-0: DVB Frontend registered
[   20.773662] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   20.773760] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   20.773864] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   20.773959] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   20.773969] cx18-0: Initialized card: Hauppauge HVR-1600
[   20.774049] cx18:  End initialization
[   20.774827] C-Media PCI 0000:05:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.836229] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   20.981158] cx18-alsa: module loading...
[   21.261068] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   21.312898] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-apu.fw
[   21.473222] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   21.479608] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   21.536967] kjournald starting.  Commit interval 5 seconds
[   21.537231] EXT3 FS on sda5, internal journal
[   21.537238] EXT3-fs: mounted filesystem with ordered data mode.
[   21.668050]   alloc irq_desc for 27 on node -1
[   21.668056]   alloc kstat_irqs on node -1
[   21.668078] tg3 0000:3f:00.0: irq 27 for MSI/MSI-X
[   21.689783] type=1505 audit(1293762893.599:6):  operation="profile_load" pid=791 name="/usr/bin/evince"
[   21.714440] type=1505 audit(1293762893.623:7):  operation="profile_replace" pid=790 name="/sbin/dhclient3"
[   21.715358] type=1505 audit(1293762893.623:8):  operation="profile_replace" pid=790 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.716562] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   21.719865] type=1505 audit(1293762893.627:9):  operation="profile_replace" pid=790 name="/usr/lib/connman/scripts/dhclient-script"
[   21.732214] type=1505 audit(1293762893.643:10):  operation="profile_load" pid=791 name="/usr/bin/evince-previewer"
[   21.748695] type=1505 audit(1293762893.659:11):  operation="profile_load" pid=796 name="/usr/sbin/mysqld"
[   21.876481] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.880877] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-apu.fw
[   22.022696] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   22.246315] cx18 0000:05:04.0: firmware: requesting v4l-cx23418-dig.fw
[   22.281705] svc: failed to register lockdv1 RPC service (errno 97).
[   22.283002] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.293099] NFSD: starting 90-second grace period
[   22.448874] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   22.471053] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   22.472933] cx18 0000:05:04.0: firmware: requesting xc3028-v27.fw
[   22.536191] xc2028 1-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   22.536319] xc2028 1-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   22.686812] CPU0 attaching NULL sched-domain.
[   22.686821] CPU1 attaching NULL sched-domain.
[   22.789216] CPU0 attaching sched-domain:
[   22.789223]  domain 0: span 0-1 level SIBLING
[   22.789228]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   22.789239]   domain 1: span 0-1 level MC
[   22.789243]    groups: 0-1 (cpu_power = 1178)
[   22.789252] CPU1 attaching sched-domain:
[   22.789256]  domain 0: span 0-1 level SIBLING
[   22.789260]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   22.789270]   domain 1: span 0-1 level MC
[   22.789274]    groups: 0-1 (cpu_power = 1178)
[   23.340129] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   23.340135] tg3: eth0: Flow control is on for TX and on for RX.
[   23.341102] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.121937] xc2028 1-0061: Loading firmware for type=(0), id 000000000000b700.
[   24.149030] SCODE (20000000), id 000000000000b700:
[   24.149040] xc2028 1-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   24.155500] xc2028 1-0061: Incorrect readback of firmware version.
[   24.212147] xc2028 1-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   25.849588] xc2028 1-0061: Loading firmware for type=(0), id 000000000000b700.
[   25.875075] SCODE (20000000), id 000000000000b700:
[   25.875083] xc2028 1-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   25.881108] xc2028 1-0061: Incorrect readback of firmware version.
[   26.001476] xc2028 1-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   27.536867] xc2028 1-0061: Loading firmware for type=(0), id 000000000000b700.
[   27.562304] SCODE (20000000), id 000000000000b700:
[   27.562311] xc2028 1-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   27.568335] xc2028 1-0061: Incorrect readback of firmware version.
[   27.624038] xc2028 1-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   29.156878] xc2028 1-0061: Loading firmware for type=(0), id 000000000000b700.
[   29.182321] SCODE (20000000), id 000000000000b700:
[   29.182328] xc2028 1-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   29.188347] xc2028 1-0061: Incorrect readback of firmware version.
[   34.000047] eth0: no IPv6 routers present

```That incorrect readback of the firmware version could be the problem.

---

### Post by klc5555 on 2010-12-31
You could very likely be right. The current firmware files for this card are dated from 22 June and are to be found at 

[http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/)

Beyond replacing the older firmware with the newer, the odds are that tuner=71 may be close, but not quite the correct parameter for initializing your particular tuner. It's unfortunate that the current cx18 driver still can't identify yours.

After your firmware is updated, short of identifying what may be burdening your particular cx18_alsa (by using things like lsmod and modinfo cx18_alsa) so that you can't unload the cx18 driver from the CLI or from the script, to avoid the insanity-inducing option of editing your .conf file (or modprobe line in rc.local) through 82 reboots (since you already know the results of '1' and '71') you may need to contact Andy Walls and the cx18 development crew at linuxtv.org for help on getting the driver to work your particular tuner. As described here: [http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

---

### Post by PatrickD-52761 on 2011-03-25
> **klc5555 said:**
> You could very likely be right. The current firmware files for this card are dated from 22 June and are to be found at 

[http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/)

Beyond replacing the older firmware with the newer, the odds are that tuner=71 may be close, but not quite the correct parameter for initializing your particular tuner. It's unfortunate that the current cx18 driver still can't identify yours.

After your firmware is updated, short of identifying what may be burdening your particular cx18_alsa (by using things like lsmod and modinfo cx18_alsa) so that you can't unload the cx18 driver from the CLI or from the script, to avoid the insanity-inducing option of editing your .conf file (or modprobe line in rc.local) through 82 reboots (since you already know the results of '1' and '71') you may need to contact Andy Walls and the cx18 development crew at linuxtv.org for help on getting the driver to work your particular tuner. As described here: [http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

Try 50 for the TV Tuner eeprom.  In my dmesg, it shows the following for my TV Tuner cards (I have two Hauppauge HVR-1600 cards installed):
```
[   12.230863] cx18:  Start initialization, version 1.4.0
[   12.230990] cx18-0: Initializing card 0
[   12.231000] cx18-0: Autodetected Hauppauge card
[   12.246837]   alloc irq_desc for 17 on node -1
[   12.246848]   alloc kstat_irqs on node -1
[   12.246870] cx18 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.246889] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   12.268527] cx18-0: cx23418 revision 01010000 (B)
[   12.498234] tveeprom 1-0050: Hauppauge model 74541, rev C6B6, serial# 7071649
[   12.498244] tveeprom 1-0050: MAC address is 00:0d:fe:6b:e7:a1
[   12.498251] tveeprom 1-0050: tuner model is Philips FM1236 MK5 (idx 116, type 43)
[   12.498259] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   12.498265] tveeprom 1-0050: audio processor is CX23418 (idx 38)
[   12.498271] tveeprom 1-0050: decoder processor is CX23418 (idx 31)
[   12.498276] tveeprom 1-0050: has radio
[   12.498281] cx18-0: Autodetected Hauppauge HVR-1600
[   12.498286] cx18-0: Simultaneous Digital and Analog TV capture supported

```In lspci, it shows:

```

00:09.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder [14f1:5b7a]
    Subsystem: Hauppauge computer works Inc. WinTV HVR-1600 [0070:7444]
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at e4000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: cx18
    Kernel modules: cx18

00:0a.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder [14f1:5b7a]
    Subsystem: Hauppauge computer works Inc. WinTV HVR-1600 [0070:7444]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: cx18
    Kernel modules: cx18

```Hope this helps you out. Have a great day:)
Patrick.

---

### Post by doogiekd on 2012-01-03
friends, 

i got my hvr-1600 to work by doing the following:

1. download the driver & firmware from: [http://ivtvdriver.org/index.php/Download](http://ivtvdriver.org/index.php/Download)

direct download address of driver: [http://dl.ivtvdriver.org/ivtv/archiv...-0.10.6.tar.gz](http://dl.ivtvdriver.org/ivtv/archiv...-0.10.6.tar.gz)

direct download of firmware: [http://dl.ivtvdriver.org/ivtv/firmwa...irmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmwa...irmware.tar.gz)

2. extract both files by right clicking and selecting "extract" 
an error may appear indicating: 
"this does not look like a .tar archive."

the workaround to extract both the firmware and driver files is:
a. install gunzip. from terminal enter: sudo apt-get install gunzip

b. after gunzip is installed, open terminal and change directory to where both files are - usually desktop. ex: cd \Desktop. 

c. enter in terminal: gunzip filename.tar.gz (replacing file name with the name of driver. enter this command again to do the same for the firmware. ex. sudo gunzip ivtv-firmware.tar.gz & sudo gunzip ivtv-0.10.6.tar.gz

d. change permissions of both files by entering in terminal:
sudo tar xvzf filename.tar - replacing filname with both the driver file and firmware file as described above.

e. once extracted, in terminal change to the directory of the driver file (usually cd \Desktop\ivtv-0.10.6.tar.gz

f. enter sudo build. program will install. let finish and do not interrupt the process.

g. install the firmware. in terminal enter sudo nautilus. be careful, errors doing sudo nautilus can be deadly to your system. (gksu did not work for me here).

h. the root file manager will open. move all files AS INDIVIDUAL FILES (not the folder) from the FIRMWARE directory to \lib\firmware. some firmware files are the same in both the ivtv driver and ivtv firmware folders. just copy all of them as individual files and choose replace when prompted. yes, the ivtv driver will contain some firmware files.

i. close the terminal and nautilus.

j. open the app: STARTUP APPLICATIONS.

K. in startup applications, click ADD. 

l. enter "tv tuner card detect" in the DESCRIPTION field.

m. enter the following in the command field:
ivtv-tune -t us-bcast -c 3 -d /dev/video0

you may have another location for your tv tuner card - video1, ect...

n. shut down your computer.

o. add a coaxial splitter from the output of your cable box. one end will connect to your tv, the other end will connect to the ANALOG input of your tv tuner card.

p. turn on the computer. your tv tuner card should now work. try first in movie player and vlc.

q. go to /dev/video0 (or video1, ect), right click on the tv tuner card and select open with movie player.

r. yes, you will only receive the channel that the cable box is currently set to only.

s. tv-viewer in my opinion is the best app for single recording. add the tv-viewer ppa to your software sources. in terminal type:
sudo deb [http://ppa.launchpad.net/blueyed/ppa/ubuntu](http://ppa.launchpad.net/blueyed/ppa/ubuntu) oneiric main

t. update software sources by entering in terminal: 
sudo apt-get update

u. install tv-viewer from synaptic.

v. IMPORTANT: you will probably have to repeat most of these steps after EVERY kernel update.

enjoy, doogiekd.

---

