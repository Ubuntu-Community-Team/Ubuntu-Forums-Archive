---
title: "Can't play HD through on-board HDMI"
date: 2013-05-07
forum: Mythbuntu
---

### Post by bpmod on 2013-05-07
I have a machine I have been using as a dedicated backend for about a year and a half or so. It has been almost completely trouble-free. I have posted the specs in the [Hardware thread]("http://ubuntuforums.org/showthread.php?t=566529&page=37&p=12637790#post12637790"). As mentioned there, I have recently decided to use this machine as a combined frontend/backend, but am having trouble getting the on-board HDMI to output HD content, either from live TV, recordings, or videos.

I had had the same problem with anther machine (specs also shown in the [same post in the Hardware thread]("http://ubuntuforums.org/showthread.php?t=566529&page=37&p=12637790#post12637790")), but simply going into the BIOS and changing the video memory to the maximum (1GB) solved that. This board's BIOS seems to allow only 128MB to the on-board video, which seems strange to me.

The board in question is an Asus P8Z68-V LX

The most likely scenario is that I am missing something totally obvious.

Any ideas?

Thanks

Brian

---

### Post by larsolav on 2013-05-08
Maybe the best thing to do is to get a VDPAU supported Nvidia card?
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by bpmod on 2013-05-08
Thank you for that suggestion. But I highly doubt that that solution is the **best** thing to do. Yes, it might allow me to watch HD, but so will fixing whatever problem I have. If I have a flat tire on my car, one solution is to buy a new car. But not many people would suggest that that is the **best** solution.

Brian

---

### Post by larsolav on 2013-05-08
What happens when you try to play HD content? What does the front-end log say?

---

### Post by bpmod on 2013-05-08
When I try to play HD content I get a purplish tint to the video with vertical lines running through the picture. Here is the frontend log:
```
Starting mythfrontend.real..
2013-05-08 17:02:36.924 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2013-05-08 17:02:36.924 Using runtime prefix = /usr
2013-05-08 17:02:36.924 Using configuration directory = /home/brian/.mythtv
2013-05-08 17:02:36.925 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2013-05-08 17:02:37.598 Empty LocalHostName.
2013-05-08 17:02:37.598 Using localhost value of PAUL
2013-05-08 17:02:37.602 New DB connection, total: 1
2013-05-08 17:02:37.604 Connected to database 'mythconverg' at host: localhost
2013-05-08 17:02:37.607 Closing DB connection named 'DBManager0'
2013-05-08 17:02:37.607 Connected to database 'mythconverg' at host: localhost
2013-05-08 17:02:37.608 Current locale EN_CA
2013-05-08 17:02:37.608 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2013-05-08 17:02:37.817 ScreenSaverX11Private: XScreenSaver support enabled
2013-05-08 17:02:37.818 DPMS is disabled.
2013-05-08 17:02:37.825 Desktop video mode: 1920x1080 60.000 Hz
2013-05-08 17:02:38.538 Enabled verbose msgs:  important general
2013-05-08 17:02:38.540 Loading en_us translation for module mythfrontend
2013-05-08 17:02:38.546 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2013-05-08 17:02:38.546 JoystickMenuThread: Joystick disabled - Failed to read /home/brian/.mythtv/joystickmenurc
2013-05-08 17:02:38.574 Using Frameless Window
2013-05-08 17:02:38.574 Using Full Screen Window
2013-05-08 17:02:38.646 Using the Qt painter
2013-05-08 17:02:38.807 New DB connection, total: 2
2013-05-08 17:02:38.807 Connected to database 'mythconverg' at host: localhost
2013-05-08 17:02:38.808 New DB connection, total: 3
2013-05-08 17:02:38.808 Current MythTV Schema Version (DBSchemaVer): 1264
2013-05-08 17:02:38.808 Connected to database 'mythconverg' at host: localhost
2013-05-08 17:02:39.089 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2013-05-08 17:02:39.089 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2013-05-08 17:02:39.092 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2013-05-08 17:02:39.092 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2013-05-08 17:02:39.320 Registering Internal as a media playback plugin.
2013-05-08 17:02:39.332 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2013-05-08 17:02:39.352 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.353 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.353 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.354 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.355 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.356 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.357 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.357 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.357 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.358 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.359 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.359 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.360 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.360 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.361 MediaMonitorUnix::AddDevice() - empty device path.
2013-05-08 17:02:39.362 Loading en_us translation for module mythvideo
2013-05-08 17:02:39.549 Found mainmenu.xml for theme 'Mythbuntu'
2013-05-08 17:02:39.623 MythCoreContext: Connecting to backend server: 192.168.0.101:6543 (try 1 of 1)
2013-05-08 17:02:39.623 Using protocol version 63
2013-05-08 17:02:47.479 TV: Attempting to change from None to WatchingLiveTV
2013-05-08 17:02:47.479 MythCoreContext: Connecting to backend server: 192.168.0.101:6543 (try 1 of 1)
2013-05-08 17:02:47.479 Using protocol version 63
2013-05-08 17:02:47.498 Spawning LiveTV Recorder -- begin
2013-05-08 17:02:47.569 Spawning LiveTV Recorder -- end
2013-05-08 17:02:47.574 We have a playbackURL(/var/lib/mythtv/livetv/1091_20130508170247.mpg) & cardtype(DUMMY)
2013-05-08 17:02:47.574 We have a RingBuffer
2013-05-08 17:02:47.650 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2013-05-08 17:02:47.668 OSD: Base theme size: 1280x720
2013-05-08 17:02:47.668 OSD: Scaling factors: 0.5625x0.8
2013-05-08 17:02:47.686 OSD: Base theme size: 1280x720
2013-05-08 17:02:47.686 OSD: Scaling factors: 0.5625x0.8
2013-05-08 17:02:47.707 Player(0): Video timing method: DRM
2013-05-08 17:02:47.723 TV: Changing from None to WatchingLiveTV
2013-05-08 17:02:47.723 TV: State is LiveTV & mctx == ctx
2013-05-08 17:02:47.725 TV: UpdateOSDInput done
2013-05-08 17:02:47.725 TV: UpdateLCD done
2013-05-08 17:02:47.725 TV: ITVRestart done
2013-05-08 17:02:47.728 pause_active: 0
2013-05-08 17:02:49.880 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:49.938 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:49.938 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:49.943 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.008 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.009 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.009 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.074 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.139 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.139 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.204 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.204 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.269 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.334 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:50.541 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2013-05-08 17:02:50.591 OSD: Base theme size: 1280x720
2013-05-08 17:02:50.591 OSD: Scaling factors: 3.20078x1.05833
2013-05-08 17:02:50.610 AFD: Opened codec 0x317c2a0, id(MPEG2VIDEO) type(Video)
2013-05-08 17:02:50.610 AFD: codec AC3 has 6 channels
2013-05-08 17:02:50.610 AFD: Opened codec 0x3550bb0, id(AC3) type(Audio)
2013-05-08 17:02:50.610 AFD: codec AC3 has 2 channels
2013-05-08 17:02:50.611 AFD: Opened codec 0x297d770, id(AC3) type(Audio)
2013-05-08 17:02:50.736 AO: Opening audio device 'hdmi:CARD=PCH,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2013-05-08 17:02:50.739 AudioPlayer: Enabling Audio
2013-05-08 17:02:50.755 AFD: Resetting byte context eof (livetv 1 was eof 0)
2013-05-08 17:02:50.912 AFD: Audio stream changed
2013-05-08 17:02:51.011 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAUUuULL
2013-05-08 17:02:51.027 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAUUuULL
2013-05-08 17:02:55.759 RingBuf(/var/lib/mythtv/livetv/1091_20130508170255.mpg) Warning: Not starting read ahead thread, already running
2013-05-08 17:02:56.126 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.126 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.126 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.127 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.127 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.127 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.128 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.128 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.128 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.129 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.311 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.312 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.312 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.313 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:02:56.625 AFD: Opened codec 0x297d770, id(MPEG2VIDEO) type(Video)
2013-05-08 17:02:56.625 AFD: codec AC3 has 6 channels
2013-05-08 17:02:56.626 AFD: Opened codec 0x2adb7a0, id(AC3) type(Audio)
2013-05-08 17:02:56.626 AFD: codec AC3 has 2 channels
2013-05-08 17:02:56.626 AFD: Opened codec 0x313a540, id(AC3) type(Audio)
2013-05-08 17:02:56.631 AFD: Resetting byte context eof (livetv 1 was eof 0)
2013-05-08 17:02:56.829 VideoOutput: Created YV12 OSD.
2013-05-08 17:02:56.857 msg: On known multiplex...
2013-05-08 17:02:56.993 AFD: Audio stream changed
2013-05-08 17:02:59.927 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:02:59.944 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.177 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.310 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.327 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.560 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.577 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.694 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.710 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.944 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:00.960 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:01.094 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:01.201 RingBuf(/var/lib/mythtv/livetv/1091_20130508170255.mpg): Waited 2.0 seconds for data 
            to become available... 0 < 32768
2013-05-08 17:03:01.327 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:01.344 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:01.710 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:01.727 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:01.977 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.094 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.110 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.360 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.377 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.494 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.744 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:02.760 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.127 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.144 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.201 RingBuf(/var/lib/mythtv/livetv/1091_20130508170255.mpg): Waited 4.0 seconds for data 
            to become available... 0 < 32768
2013-05-08 17:03:03.377 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.510 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.527 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.760 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.777 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.894 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:03.910 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.144 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.160 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.294 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.527 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.544 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.910 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:04.927 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.177 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.193 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.294 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.310 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.560 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.577 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.943 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:05.960 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.193 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.327 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.343 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.577 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.593 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.710 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.727 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.960 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:06.977 Player(0): Waited 100ms for video buffers ALUALLAUAAAAAAAUAAfAALUAUUUUuUU
2013-05-08 17:03:07.110 Player(0): Waited 100ms for video buffers ALUALLAUAAALAAAUAAfAALUAUUUUUUU
2013-05-08 17:03:08.074 TV: Attempting to change from WatchingLiveTV to None
2013-05-08 17:03:08.266 TV: Changing from WatchingLiveTV to None
2013-05-08 17:03:25.863 TV: Attempting to change from None to WatchingPreRecorded
2013-05-08 17:03:26.164 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.165 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.169 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.170 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.174 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.175 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.180 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.180 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.185 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.190 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.190 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.195 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.196 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.201 [mpeg2video @ 0x7f5bc11c0700]mpeg_decode_postinit() failure
2013-05-08 17:03:26.238 AFD: Opened codec 0x7f5b9c15fa50, id(MPEG2VIDEO) type(Video)
2013-05-08 17:03:26.238 AFD: codec AC3 has 6 channels
2013-05-08 17:03:26.239 AFD: Opened codec 0x7f5b9c18dc60, id(AC3) type(Audio)
2013-05-08 17:03:26.239 AFD: codec AC3 has 2 channels
2013-05-08 17:03:26.239 AFD: Opened codec 0x7f5b9c1ceb30, id(AC3) type(Audio)
2013-05-08 17:03:26.239 AFD: codec AC3 has 2 channels
2013-05-08 17:03:26.239 AFD: Opened codec 0x7f5b9c1483a0, id(AC3) type(Audio)
2013-05-08 17:03:26.359 AO: Opening audio device 'hdmi:CARD=PCH,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2013-05-08 17:03:26.360 AudioPlayer: Enabling Audio
2013-05-08 17:03:26.377 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2013-05-08 17:03:26.445 AFD: Audio stream changed
2013-05-08 17:03:26.456 Player(1): Video timing method: DRM
2013-05-08 17:03:26.472 TV: Changing from None to WatchingPreRecorded
2013-05-08 17:03:26.553 VideoOutput: Created YV12 OSD.
2013-05-08 17:03:30.823 TV: Attempting to change from WatchingPreRecorded to None
2013-05-08 17:03:30.861 TV: Changing from WatchingPreRecorded to None
2013-05-08 17:05:49.804 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit


```

---

### Post by BicyclerBoy on 2013-05-09
The intel HD3000/4000 stuff does not work until much later kernels than yours...

If you were using 12.04.. I would suggest xorg-edgers ppa to upgrade kernel & intel drivers..
With this you could try VAAPI & openGL painter.

You could try openGL playback (decode & painter) now.

I find that 12.04, xorg-edgers ppa & i3 (1st gen) VAAPI & mythtv git master works badly with OTA interlaced video.

---

### Post by bpmod on 2013-05-10
I didn't know that there would be that kind of a difference between 11.10 and 12.04, but that makes sense.

I also contacted Asus to see why my BIOS only allows 128MB of shared video memory when the specs say that there is 1748MB available. They told me to update my BIOS, which I have. I now have a 1GB (not 1748MB) option for iGPU memory, but am still experiencing the same issue. Well, almost the same issue. I can now play HD content captured from Blu-ray and converted to mkv. I can also play mkv's that I have created from OTA 1080i source. However, with the BIOS upgrade, I have now lost my sound which worked perfectly before.

I am likely going to upgrade to 12.04 when I can find time between recordings. I had [a problem]("http://ubuntuforums.org/showthread.php?t=2129481") upgrading on a new installation. I never solved that problem and am not going to wipe this one and reload from scratch. Does anybody here know of a way to upgrade without wiping and reloading?

I will keep you posted on my progress.

Brian

---

### Post by BicyclerBoy on 2013-05-10
Maybe your CPU was so new that there was no detection support in BIOS..
Had similar BIOS drama with RAM & PCIe3 video cards..

You should try openGL ..I think Xv is deprecated..
The purple tint could be wrong colourspace or video playback adjustments need to be reset via OSD GUI.

What are you testing the sound with ? mythtv ?
You should rescan audio devices (in mythtv FE).

To move to new install (same or later version)
The only thing you need to keep from an old installation is a (couple of) database backups & the folders of storage groups (recordings etc).
Should make backups of the mythtv.txt/config.xml files from:
/etc/mythtv/
/home/mythtv/.mythtv/
/home/<fe-user>/.mythtv/

& my.cnf from /etc/mysql/

*buntu 12.04 still has a little support life left.
Compared to 11.10..the kernel versions would be very different + there are additional ppa (xorg-edgers) with the latest intel drivers etc.

---

### Post by bpmod on 2013-05-12
> **BicyclerBoy said:**
> Maybe your CPU was so new that there was no detection support in BIOS..
Had similar BIOS drama with RAM & PCIe3 video cards..

You should try openGL ..I think Xv is deprecated..
The purple tint could be wrong colourspace or video playback adjustments need to be reset via OSD GUI.
Not sure what you mean about the CPU being new. Also, the purple tint (if that's even the best description) was exactly the same on the other machine which was fixed by selecting 1GB on the iGPU in the BIOS. The one difference, though, is that the other one is running 12.04.

> **BicyclerBoy said:**
>  What are you testing the sound with ? mythtv ?
You should rescan audio devices (in mythtv FE).
Yes. I am testing the sound by running a video (or live TV) through the default mythtv player. I have scanned each time. Actually, this brings up another question that you or somebody else might be able to answer: When I go to the audio part of the frontend setup, I cannot choose any different audio output until I first select scan for audio devices. But I would expect something to happen at that point rather than just suddenly having several more choices that aren't apparent until I choose that field and scroll through them. Is this by design? In any event, I have now tried every option that mentions hdmi, and none of them seems to work.

> **BicyclerBoy said:**
>  To move to new install (same or later version)
The only thing you need to keep from an old installation is a (couple of) database backups & the folders of storage groups (recordings etc).
Should make backups of the mythtv.txt/config.xml files from:
/etc/mythtv/
/home/mythtv/.mythtv/
/home/<fe-user>/.mythtv/

& my.cnf from /etc/mysql/
Not to mention modifying either all of the permissions of the files on the NAS, or the users' and groups' uids & gids set up on the new version of Mythbuntu. I did a complete install of 12.04 (to a new device, thankfully), and when I connected to the NAS, all of my recordings and videos were owned by different users. No telling what else might be awry.

> **BicyclerBoy said:**
>  *buntu 12.04 still has a little support life left.
I would hope that there is a bit more than "a little" support life left, considering that when I started this (latest) ordeal one month ago, 12.04 was (and still is) the latest version available.

Brian

---

### Post by BicyclerBoy on 2013-05-14
If you required a BIOS update to get the IGPU memory sorted then the CPU was not being supported..
The HD3000/4000 iGPU is inside the iCPU.

BIOS updates play havoc with CMOS settings..
Check you haven't got HDA turned off (set to AC97 mode)

Your mythtv user is a member of the audio group ?
aplay -l
aplay -L
speaker-test -c 2 -l 1 -r 48000 -D hw:0,0

Very odd that you have to scan every time to get a complete list..seems like the audio devices are not being found your alsa install.
Mythtv stops pulse audio server & does do some strong foo..

Can you try painter set to automatic (not Qt) & playback to opengl ?
Refresh/update your themes..
The strange colour tint can be a side-effect of video driver (or version of) or the video playback method used in mythtv (i.e Xv).

The later intel GPUs are not identified by old kernels ..you get i915 (if lucky) or vesa driver. Because you get 1920x1080 it looks like some intel driver..
Post your /var/log/Xorg.0.log as an file attachment.

The trick to avoid users & groups ids changing is to always create the mythtv user first on every box.
The numbers are just a list against labels in a file so you can fix the problem.

12.04 is a (one year old) LTS release so should be support for some time (inc mythbuntu).

There is an intel driver/vaapi solution that is getting favourable responses on the mailing lists
[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)

I find comments that kernel 3.7 is required for HDMI audio on sandy/ivybridge unless you have a patched kernel.
So I would think 12.04 & xorg-edgers is the way to go..

---

### Post by gga96 on 2013-05-14
> 
I have now lost my sound which worked perfectly before

I had similar sound loss. The sound had been muted. Got sound back with alsamixer.

---

### Post by bpmod on 2013-05-15
UPDATE: After installing 12.04 and discovering that the uids & gids were all screwy, I removed that drive and put the old 11.10 installation back into the machine, as I do not have much time to play between recordings. I have verified, however, that the sound works fine in the 12.04 installation. I am having several other problems with that installation, though, so I have not (yet) been able to tell if I can play video.

I don't know if I should start a new thread for this, but it is driving me around the bend.

In this new installation, when I try to play live TV (simply to test if I can get HD video), I get a message "cannot connect to backend. Is it running?" or something to that effect. I have verified that the backend is running, and restart the frontend. The first time (and this can be repeated over and over) that I try to play Live TV (I cannot play any recordings as I haven't taken the time yet to fix all of the user/group ids) after restarting the frontend, the message is "All tuners are in use", even though none of them is. Then hitting OK and retrying, I get the "cannot connect to backend" message.

Brian

---

