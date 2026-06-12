---
title: "Video playback issues"
date: 2011-08-11
forum: Mythbuntu
---

### Post by mtbdrew on 2011-08-11
Running Mythbuntu 10.10 and for some reason the video playback has started going fuzzy for a second then clears up. This happens continuously now after the updates were applied. I have a Nvidi 430 card running current drivers. I've tried turning off vdpau but it didn't help. Anyone seen this issue?

---

### Post by williammanda on 2011-08-12
> **mtbdrew said:**
> Running Mythbuntu 10.10 and for some reason the video playback has started going fuzzy for a second then clears up. This happens continuously now after the updates were applied. I have a Nvidi 430 card running current drivers. I've tried turning off vdpau but it didn't help. Anyone seen this issue?

Sorry to say this...why did you update if things were working fine?

---

### Post by mtbdrew on 2011-08-12
Like to keep the system up to date, why shouldn't I be able to?

---

### Post by williammanda on 2011-08-12
> **mtbdrew said:**
> Like to keep the system up to date, why shouldn't I be able to?

Post your log files.

---

### Post by mtbdrew on 2011-08-12
> **williammanda said:**
> Post your log files.

How do I do that?

---

### Post by williammanda on 2011-08-12
Use a file browser and goto:

var/log/mythtv

Post both the mythfrontend and the mythbackend logs.

---

### Post by mtbdrew on 2011-08-12
> **williammanda said:**
> Use a file browser and goto:

var/log/mythtv

Post both the mythfrontend and the mythbackend logs.

Okay here they are and thank you for the help.

---

### Post by williammanda on 2011-08-12
> **mtbdrew said:**
> Okay here they are and thank you for the help.


Since your files are so big....I want you copy part of the mythfrontend log. The entry in the log "Starting mythfrontend.real.." would be the start point. The best situation would be for you to copy the part of the log during your issue.

I'm going to post part of the mythbackend:

```
2011-08-12 11:42:09.011 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 11:57:09.100 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 12:12:09.176 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 12:13:52.110 MainServer::ANN Monitor
2011-08-12 12:13:52.181 adding: mythbox as a client (events: 0)
2011-08-12 12:13:52.232 MainServer::ANN Monitor
2011-08-12 12:13:52.281 adding: mythbox as a client (events: 1)
2011-08-12 12:17:02.221 MainServer::ANN Monitor
2011-08-12 12:17:02.294 adding: mythbox as a client (events: 0)
2011-08-12 12:27:09.247 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 12:42:09.332 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 12:57:09.414 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 13:12:09.494 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 14:02:32.808 mythbackend version: branches/release-0-23-fixes [26437] www.mythtv.org
2011-08-12 14:02:32.926 Using runtime prefix = /usr
2011-08-12 14:02:32.976 Using configuration directory = /home/mythtv/.mythtv
2011-08-12 14:02:33.027 Empty LocalHostName.
2011-08-12 14:02:33.076 Using localhost value of mythbox
2011-08-12 14:02:33.137 New DB connection, total: 1
2011-08-12 14:02:33.200 Connected to database 'mythconverg' at host: localhost
2011-08-12 14:02:33.260 Closing DB connection named 'DBManager0'
2011-08-12 14:02:33.311 Connected to database 'mythconverg' at host: localhost
2011-08-12 14:02:33.374 Current MythTV Schema Version (DBSchemaVer): 1254
2011-08-12 14:02:33.429 MythBackend: Starting up as the master server.
2011-08-12 14:02:33.529 New DB connection, total: 2
2011-08-12 14:02:33.603 Connected to database 'mythconverg' at host: localhost
2011-08-12 14:02:33.689 New DB connection, total: 3
2011-08-12 14:02:33.745 Connected to database 'mythconverg' at host: localhost
2011-08-12 14:02:36.280 New DB scheduler connection
2011-08-12 14:02:36.356 Connected to database 'mythconverg' at host: localhost
2011-08-12 14:02:36.504 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-08-12 14:02:36.790 Main::Registering HttpStatus Extension
2011-08-12 14:02:36.975 Enabled verbose msgs:  important general
2011-08-12 14:02:37.050 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 14:02:39.536 Reschedule requested for id -1.
2011-08-12 14:02:39.921 Scheduled 36 items in 0.4 = 0.13 match + 0.25 place
2011-08-12 14:02:39.957 Seem to be woken up by USER
2011-08-12 14:02:40.018 MainServer::ANN Monitor
2011-08-12 14:02:40.062 adding: mythbox as a client (events: 0)
2011-08-12 14:03:56.501 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 14:06:06.315 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:09:11.809 MainServer::ANN Monitor
2011-08-12 14:09:11.869 adding: mythbox as a client (events: 0)
2011-08-12 14:09:11.919 MainServer::ANN Monitor
2011-08-12 14:09:11.969 adding: mythbox as a client (events: 1)
2011-08-12 14:09:16.185 MainServer::ANN Monitor
2011-08-12 14:09:16.253 adding: mythbox as a client (events: 0)
2011-08-12 14:09:16.304 MainServer::ANN Monitor
2011-08-12 14:09:16.353 adding: mythbox as a client (events: 1)
2011-08-12 14:11:10.075 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:16:13.791 DVBSM(/dev/dvb/adapter1/frontend0),
 Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:17:02.355 MainServer::ANN Monitor
2011-08-12 14:17:02.423 adding: mythbox as a client (events: 0)
2011-08-12 14:18:56.588 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 14:21:17.699 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:26:21.451 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:31:25.187 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:33:56.659 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-08-12 14:36:22.875 MainServer::ANN Monitor
2011-08-12 14:36:22.930 adding: mythbox as a client (events: 0)
2011-08-12 14:36:22.973 MainServer::ANN Monitor
2011-08-12 14:36:23.014 adding: mythbox as a client (events: 1)
2011-08-12 14:36:28.971 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2011-08-12 14:41:32.663 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)

```

---

### Post by mtbdrew on 2011-08-12
Seems like there are a lot of decode errors:

Starting mythfrontend.real..
2011-08-12 08:54:17.608 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2011-08-12 08:54:17.608 Using runtime prefix = /usr
2011-08-12 08:54:17.609 Using configuration directory = /home/mythbox/.mythtv
2011-08-12 08:54:18.207 Empty LocalHostName.
2011-08-12 08:54:18.207 Using localhost value of mythbox
2011-08-12 08:54:18.224 New DB connection, total: 1
2011-08-12 08:54:18.226 Connected to database 'mythconverg' at host: localhost
2011-08-12 08:54:18.237 Closing DB connection named 'DBManager0'
2011-08-12 08:54:18.284 ScreenSaverX11Private: Gnome screen saver support enabled
2011-08-12 08:54:18.294 DPMS is active.
2011-08-12 08:54:18.296 Primary screen: 0.
2011-08-12 08:54:18.297 Connected to database 'mythconverg' at host: localhost
2011-08-12 08:54:18.298 Using screen 0, 1920x1080 at 0,0
2011-08-12 08:54:18.332 Desktop video mode: 1920x1080 59.9988 Hz
2011-08-12 08:54:18.428 MythUI Image Cache size set to 20971520 bytes
2011-08-12 08:54:18.566 AudioPulseUtil: Suspend Success
2011-08-12 08:54:18.567 Enabled verbose msgs:  important general
2011-08-12 08:54:18.600 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2011-08-12 08:54:18.616 Primary screen: 0.
2011-08-12 08:54:18.616 Using screen 0, 1920x1080 at 0,0
2011-08-12 08:54:18.634 Using theme base resolution of 1280x720
2011-08-12 08:54:18.678 LIRC: Successfully initialized '/dev/lircd' using '/home/mythbox/.mythtv/lircrc' config
2011-08-12 08:54:18.678 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2011-08-12 08:54:18.712 Using Frameless Window
2011-08-12 08:54:18.713 Using Full Screen Window
2011-08-12 08:54:19.211 Using the OpenGL painter
2011-08-12 08:54:19.516 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-08-12 08:54:19.587 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-08-12 08:54:19.626 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-08-12 08:54:19.626 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-08-12 08:54:19.631 Current MythTV Schema Version (DBSchemaVer): 1254
2011-08-12 08:54:20.267 Registering Internal as a media playback plugin.
2011-08-12 08:54:20.318 Cannot load language en_us for module mytharchive
2011-08-12 08:54:20.353 Cannot load language en_us for module mythbrowser
2011-08-12 08:54:20.356 Registering WebBrowser as a media playback plugin.
2011-08-12 08:54:20.356 Cannot load language en_us for module mythbrowser
2011-08-12 08:54:20.431 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-12 08:54:20.432 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-12 08:54:20.432 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-12 08:54:20.433 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-08-12 08:54:20.433 Cannot load language en_us for module mythgallery
2011-08-12 08:54:20.593 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-08-12 08:54:20.626 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-08-12 08:54:20.632 Cannot load language en_us for module mythmusic
2011-08-12 08:54:20.653 Cannot load language en_us for module mythnews
2011-08-12 08:54:20.666 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-08-12 08:54:20.694 Cannot load language en_us for module mythvideo
2011-08-12 08:54:20.708 Cannot load language en_us for module mythweather
2011-08-12 08:54:20.711 NetworkControl: Listening for remote connections on port 6546
2011-08-12 08:54:20.712 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-08-12 08:54:20.802 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-08-12 08:54:20.822 Found mainmenu.xml for theme 'Mythbuntu'
2011-08-12 08:54:21.798 Using NV NPOT texture extension
2011-08-12 08:54:21.959 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-08-12 08:54:21.960 Using protocol version 23056
2011-08-12 08:57:29.457 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2011-08-12 08:57:32.279 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2011-08-12 08:57:32.527 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythbox/var/lib/mythtv/videos/)
2011-08-12 08:57:32.548 MythVideo::ScanVideoDirectory Scanning (/media/TV_Shows/TV Shows)
2011-08-12 08:58:17.107 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2011-08-12 08:58:18.485 New DB connection, total: 2
2011-08-12 08:58:18.486 Connected to database 'mythconverg' at host: localhost
2011-08-12 08:58:18.578 TV: Attempting to change from None to WatchingVideo
2011-08-12 08:58:18.848 VDPAU: Version 1
2011-08-12 08:58:18.848 VDPAU: Information NVIDIA VDPAU Driver Shared Library  280.13  Wed Jul 27 17:18:15 PDT 2011
2011-08-12 08:58:18.848 AFD: Opened codec 0x8e84210, id(MPEG4) type(Video)
2011-08-12 08:58:18.849 AFD: codec MP3 has 2 channels
2011-08-12 08:58:18.849 AFD: Opened codec 0x8e47140, id(MP3) type(Audio)
2011-08-12 08:58:18.873 Opening audio device 'plughw:0,9'. ch 2(2) sr 48000 (reenc 0)
2011-08-12 08:58:18.873 Opening ALSA audio device 'plughw:0,9'.
2011-08-12 08:58:19.125 VDPAU: Created 2 output surfaces.
2011-08-12 08:58:19.125 VDPAU: Created VDPAU render device 1920x1080
2011-08-12 08:58:19.138 NVP(0): Forcing decode extra audio option on (Video method requires it).
2011-08-12 08:58:19.139 FilterManager: Failed to load filter ''ivtc', no such filter exists
2011-08-12 08:58:19.140 OSD Theme Dimensions W: 1280 H: 720
2011-08-12 08:58:19.360 TV: Changing from None to WatchingVideo
2011-08-12 08:58:19.362 The realtime priority setting is not enabled.
2011-08-12 08:58:19.398 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.398 AFD Error: Unknown decoding error
2011-08-12 08:58:19.398 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.398 AFD Error: Unknown decoding error
2011-08-12 08:58:19.399 OpenGLVideoSync()
2011-08-12 08:58:19.400 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.400 AFD Error: Unknown decoding error
2011-08-12 08:58:19.400 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.400 AFD Error: Unknown decoding error
2011-08-12 08:58:19.401 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.401 AFD Error: Unknown decoding error
2011-08-12 08:58:19.402 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.402 AFD Error: Unknown decoding error
2011-08-12 08:58:19.403 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.403 AFD Error: Unknown decoding error
2011-08-12 08:58:19.404 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.405 AFD Error: Unknown decoding error
2011-08-12 08:58:19.406 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.406 AFD Error: Unknown decoding error
2011-08-12 08:58:19.408 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.408 AFD Error: Unknown decoding error
2011-08-12 08:58:19.409 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.409 AFD Error: Unknown decoding error
2011-08-12 08:58:19.411 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.411 AFD Error: Unknown decoding error
2011-08-12 08:58:19.412 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.413 AFD Error: Unknown decoding error
2011-08-12 08:58:19.414 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.414 AFD Error: Unknown decoding error
2011-08-12 08:58:19.416 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.416 AFD Error: Unknown decoding error
2011-08-12 08:58:19.417 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.417 AFD Error: Unknown decoding error
2011-08-12 08:58:19.425 ScreenSaverX11Private: DPMS Deactivated 1
2011-08-12 08:58:19.456 Video timing method: SGI OpenGL
2011-08-12 08:58:19.475 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-08-12 08:58:19.498 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.554 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.572 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.572 AFD Error: Unknown decoding error
2011-08-12 08:58:19.574 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.574 AFD Error: Unknown decoding error
2011-08-12 08:58:19.585 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.606 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.606 AFD Error: Unknown decoding error
2011-08-12 08:58:19.616 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.656 AFD Error: Unknown decoding error
2011-08-12 08:58:19.661 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.717 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.739 AFD Error: Unknown decoding error
2011-08-12 08:58:19.748 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.772 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.772 AFD Error: Unknown decoding error
2011-08-12 08:58:19.778 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.809 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.822 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.822 AFD Error: Unknown decoding error
2011-08-12 08:58:19.840 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.856 AFD Error: Unknown decoding error
2011-08-12 08:58:19.870 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.901 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.906 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.906 AFD Error: Unknown decoding error
2011-08-12 08:58:19.931 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.936 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.939 AFD Error: Unknown decoding error
2011-08-12 08:58:19.967 AO: dropping back audio_buffer_unused
2011-08-12 08:58:19.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:19.989 AFD Error: Unknown decoding error
2011-08-12 08:58:19.998 AO: dropping back audio_buffer_unused
2011-08-12 08:58:20.022 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.022 AFD Error: Unknown decoding error
2011-08-12 08:58:20.072 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.072 AFD Error: Unknown decoding error
2011-08-12 08:58:20.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.106 AFD Error: Unknown decoding error
2011-08-12 08:58:20.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.239 AFD Error: Unknown decoding error
2011-08-12 08:58:20.272 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.272 AFD Error: Unknown decoding error
2011-08-12 08:58:20.322 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.322 AFD Error: Unknown decoding error
2011-08-12 08:58:20.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.356 AFD Error: Unknown decoding error
2011-08-12 08:58:20.406 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.406 AFD Error: Unknown decoding error
2011-08-12 08:58:20.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.489 AFD Error: Unknown decoding error
2011-08-12 08:58:20.606 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.606 AFD Error: Unknown decoding error
2011-08-12 08:58:20.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.656 AFD Error: Unknown decoding error
2011-08-12 08:58:20.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.739 AFD Error: Unknown decoding error
2011-08-12 08:58:20.822 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.822 AFD Error: Unknown decoding error
2011-08-12 08:58:20.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.856 AFD Error: Unknown decoding error
2011-08-12 08:58:20.906 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.906 AFD Error: Unknown decoding error
2011-08-12 08:58:20.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.939 AFD Error: Unknown decoding error
2011-08-12 08:58:20.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:20.989 AFD Error: Unknown decoding error
2011-08-12 08:58:21.022 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.022 AFD Error: Unknown decoding error
2011-08-12 08:58:21.072 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.072 AFD Error: Unknown decoding error
2011-08-12 08:58:21.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.106 AFD Error: Unknown decoding error
2011-08-12 08:58:21.156 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.156 AFD Error: Unknown decoding error
2011-08-12 08:58:21.189 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.189 AFD Error: Unknown decoding error
2011-08-12 08:58:21.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.239 AFD Error: Unknown decoding error
2011-08-12 08:58:21.272 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.272 AFD Error: Unknown decoding error
2011-08-12 08:58:21.322 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.322 AFD Error: Unknown decoding error
2011-08-12 08:58:21.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.356 AFD Error: Unknown decoding error
2011-08-12 08:58:21.406 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.406 AFD Error: Unknown decoding error
2011-08-12 08:58:21.439 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.439 AFD Error: Unknown decoding error
2011-08-12 08:58:21.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.489 AFD Error: Unknown decoding error
2011-08-12 08:58:21.522 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.523 AFD Error: Unknown decoding error
2011-08-12 08:58:21.572 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.573 AFD Error: Unknown decoding error
2011-08-12 08:58:21.607 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.607 AFD Error: Unknown decoding error
2011-08-12 08:58:21.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.657 AFD Error: Unknown decoding error
2011-08-12 08:58:21.689 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.689 AFD Error: Unknown decoding error
2011-08-12 08:58:21.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.739 AFD Error: Unknown decoding error
2011-08-12 08:58:21.773 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.773 AFD Error: Unknown decoding error
2011-08-12 08:58:21.823 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.823 AFD Error: Unknown decoding error
2011-08-12 08:58:21.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.856 AFD Error: Unknown decoding error
2011-08-12 08:58:21.906 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.907 AFD Error: Unknown decoding error
2011-08-12 08:58:21.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.939 AFD Error: Unknown decoding error
2011-08-12 08:58:21.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:21.989 AFD Error: Unknown decoding error
2011-08-12 08:58:22.023 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.023 AFD Error: Unknown decoding error
2011-08-12 08:58:22.072 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.073 AFD Error: Unknown decoding error
2011-08-12 08:58:22.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.106 AFD Error: Unknown decoding error
2011-08-12 08:58:22.156 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.156 AFD Error: Unknown decoding error
2011-08-12 08:58:22.189 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.189 AFD Error: Unknown decoding error
2011-08-12 08:58:22.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.239 AFD Error: Unknown decoding error
2011-08-12 08:58:22.273 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.273 AFD Error: Unknown decoding error
2011-08-12 08:58:22.322 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.323 AFD Error: Unknown decoding error
2011-08-12 08:58:22.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.356 AFD Error: Unknown decoding error
2011-08-12 08:58:22.406 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.406 AFD Error: Unknown decoding error
2011-08-12 08:58:22.439 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.439 AFD Error: Unknown decoding error
2011-08-12 08:58:22.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.489 AFD Error: Unknown decoding error
2011-08-12 08:58:22.523 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.523 AFD Error: Unknown decoding error
2011-08-12 08:58:22.572 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.573 AFD Error: Unknown decoding error
2011-08-12 08:58:22.606 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.606 AFD Error: Unknown decoding error
2011-08-12 08:58:22.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.656 AFD Error: Unknown decoding error
2011-08-12 08:58:22.689 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.689 AFD Error: Unknown decoding error
2011-08-12 08:58:22.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.739 AFD Error: Unknown decoding error
2011-08-12 08:58:22.773 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.773 AFD Error: Unknown decoding error
2011-08-12 08:58:22.822 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.823 AFD Error: Unknown decoding error
2011-08-12 08:58:22.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.856 AFD Error: Unknown decoding error
2011-08-12 08:58:22.906 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.906 AFD Error: Unknown decoding error
2011-08-12 08:58:22.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.939 AFD Error: Unknown decoding error
2011-08-12 08:58:22.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:22.989 AFD Error: Unknown decoding error
2011-08-12 08:58:23.023 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.023 AFD Error: Unknown decoding error
2011-08-12 08:58:23.073 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.073 AFD Error: Unknown decoding error
2011-08-12 08:58:23.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.106 AFD Error: Unknown decoding error
2011-08-12 08:58:23.156 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.156 AFD Error: Unknown decoding error
2011-08-12 08:58:23.189 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.189 AFD Error: Unknown decoding error
2011-08-12 08:58:23.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.239 AFD Error: Unknown decoding error
2011-08-12 08:58:23.273 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.273 AFD Error: Unknown decoding error
2011-08-12 08:58:23.323 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.323 AFD Error: Unknown decoding error
2011-08-12 08:58:23.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.356 AFD Error: Unknown decoding error
2011-08-12 08:58:23.407 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.407 AFD Error: Unknown decoding error
2011-08-12 08:58:23.439 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.439 AFD Error: Unknown decoding error
2011-08-12 08:58:23.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.489 AFD Error: Unknown decoding error
2011-08-12 08:58:23.523 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.523 AFD Error: Unknown decoding error
2011-08-12 08:58:23.573 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.573 AFD Error: Unknown decoding error
2011-08-12 08:58:23.606 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.606 AFD Error: Unknown decoding error
2011-08-12 08:58:23.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.656 AFD Error: Unknown decoding error
2011-08-12 08:58:23.689 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.689 AFD Error: Unknown decoding error
2011-08-12 08:58:23.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.739 AFD Error: Unknown decoding error
2011-08-12 08:58:23.773 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.773 AFD Error: Unknown decoding error
2011-08-12 08:58:23.823 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.823 AFD Error: Unknown decoding error
2011-08-12 08:58:23.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.856 AFD Error: Unknown decoding error
2011-08-12 08:58:23.907 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.907 AFD Error: Unknown decoding error
2011-08-12 08:58:23.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.939 AFD Error: Unknown decoding error
2011-08-12 08:58:23.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:23.989 AFD Error: Unknown decoding error
2011-08-12 08:58:24.023 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.023 AFD Error: Unknown decoding error
2011-08-12 08:58:24.073 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.073 AFD Error: Unknown decoding error
2011-08-12 08:58:24.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.106 AFD Error: Unknown decoding error
2011-08-12 08:58:24.156 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.156 AFD Error: Unknown decoding error
2011-08-12 08:58:24.189 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.189 AFD Error: Unknown decoding error
2011-08-12 08:58:24.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.239 AFD Error: Unknown decoding error
2011-08-12 08:58:24.273 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.273 AFD Error: Unknown decoding error
2011-08-12 08:58:24.323 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.323 AFD Error: Unknown decoding error
2011-08-12 08:58:24.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.356 AFD Error: Unknown decoding error
2011-08-12 08:58:24.407 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.407 AFD Error: Unknown decoding error
2011-08-12 08:58:24.439 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.439 AFD Error: Unknown decoding error
2011-08-12 08:58:24.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.489 AFD Error: Unknown decoding error
2011-08-12 08:58:24.523 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.523 AFD Error: Unknown decoding error
2011-08-12 08:58:24.573 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.573 AFD Error: Unknown decoding error
2011-08-12 08:58:24.606 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.606 AFD Error: Unknown decoding error
2011-08-12 08:58:24.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.656 AFD Error: Unknown decoding error
2011-08-12 08:58:24.689 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.689 AFD Error: Unknown decoding error
2011-08-12 08:58:24.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.739 AFD Error: Unknown decoding error
2011-08-12 08:58:24.773 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.773 AFD Error: Unknown decoding error
2011-08-12 08:58:24.822 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.823 AFD Error: Unknown decoding error
2011-08-12 08:58:24.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.856 AFD Error: Unknown decoding error
2011-08-12 08:58:24.906 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.906 AFD Error: Unknown decoding error
2011-08-12 08:58:24.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.939 AFD Error: Unknown decoding error
2011-08-12 08:58:24.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:24.989 AFD Error: Unknown decoding error
2011-08-12 08:58:25.023 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.023 AFD Error: Unknown decoding error
2011-08-12 08:58:25.073 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.073 AFD Error: Unknown decoding error
2011-08-12 08:58:25.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.106 AFD Error: Unknown decoding error
2011-08-12 08:58:25.156 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.156 AFD Error: Unknown decoding error
2011-08-12 08:58:25.189 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.189 AFD Error: Unknown decoding error
2011-08-12 08:58:25.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.239 AFD Error: Unknown decoding error
2011-08-12 08:58:25.273 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.273 AFD Error: Unknown decoding error
2011-08-12 08:58:25.323 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.323 AFD Error: Unknown decoding error
2011-08-12 08:58:25.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.356 AFD Error: Unknown decoding error
2011-08-12 08:58:25.407 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.407 AFD Error: Unknown decoding error
2011-08-12 08:58:25.439 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.439 AFD Error: Unknown decoding error
2011-08-12 08:58:25.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.489 AFD Error: Unknown decoding error
2011-08-12 08:58:25.523 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.523 AFD Error: Unknown decoding error
2011-08-12 08:58:25.573 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.573 AFD Error: Unknown decoding error
2011-08-12 08:58:25.606 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.606 AFD Error: Unknown decoding error
2011-08-12 08:58:25.656 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.656 AFD Error: Unknown decoding error
2011-08-12 08:58:25.689 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.689 AFD Error: Unknown decoding error
2011-08-12 08:58:25.739 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.739 AFD Error: Unknown decoding error
2011-08-12 08:58:25.773 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.773 AFD Error: Unknown decoding error
2011-08-12 08:58:25.823 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.823 AFD Error: Unknown decoding error
2011-08-12 08:58:25.856 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.856 AFD Error: Unknown decoding error
2011-08-12 08:58:25.907 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.907 AFD Error: Unknown decoding error
2011-08-12 08:58:25.939 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.939 AFD Error: Unknown decoding error
2011-08-12 08:58:25.989 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:25.989 AFD Error: Unknown decoding error
2011-08-12 08:58:26.023 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.023 AFD Error: Unknown decoding error
2011-08-12 08:58:26.073 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.073 AFD Error: Unknown decoding error
2011-08-12 08:58:26.106 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.106 AFD Error: Unknown decoding error
2011-08-12 08:58:26.156 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.156 AFD Error: Unknown decoding error
2011-08-12 08:58:26.189 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.190 AFD Error: Unknown decoding error
2011-08-12 08:58:26.239 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.239 AFD Error: Unknown decoding error
2011-08-12 08:58:26.273 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.273 AFD Error: Unknown decoding error
2011-08-12 08:58:26.323 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.323 AFD Error: Unknown decoding error
2011-08-12 08:58:26.356 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.356 AFD Error: Unknown decoding error
2011-08-12 08:58:26.406 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.406 AFD Error: Unknown decoding error
2011-08-12 08:58:26.439 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.439 AFD Error: Unknown decoding error
2011-08-12 08:58:26.489 [mpeg4_vdpau @ 0x2013120]header damaged
2011-08-12 08:58:26.490 AFD Error: Unknown decoding error
2011-08-12 08:58:26.523 [mpeg4_vdpau @ 0x2013120]header damaged

---

### Post by mtbdrew on 2011-08-13
Issue doesn't occur with videos recorded in other formats.

---

### Post by williammanda on 2011-08-13
What kind of updates? Ubuntu? Mythbuntu-repos?

---

### Post by williammanda on 2011-08-13
> **mtbdrew said:**
> Issue doesn't occur with videos recorded in other formats.

You are saying anything but recorded tv plays fine?

---

### Post by nickrout on 2011-08-14
deleted, mistaken double post!

---

### Post by mtbdrew on 2011-08-14
Okay did clean install and issue still there so ruled out updates. Running nvidia-current driver (260.19.06).

Issue does not occur on files recorded with the myth box. 

Common factor is that the files are Xvid.

---

### Post by nickrout on 2011-08-14
what version of mythtv are you now running?

what video card do you have?

---

### Post by mtbdrew on 2011-08-15
> **nickrout said:**
> what version of mythtv are you now running?

what video card do you have?

mythfrontend version: branches/release-0-23-fixes [26437

Video card is a PNY GT430 1Gb

---

### Post by nickrout on 2011-08-15
> **mtbdrew said:**
> mythfrontend version: branches/release-0-23-fixes [26437

Video card is a PNY GT430 1Gb

Like I said before, update to 0.24-fixes via mythbuntu-repos. You are runnning an old and unsupported version. the internal player's handling of xvid improves with every release.

---

### Post by mtbdrew on 2011-08-15
[QUOTE=nickrout;11155010]Like I said before, update to 0.24-fixes via mythbuntu-repos. You are runnning an old and unsupported version. the internal player's handling of xvid improves with every release.[/QU
Okay so have upgraded to 0.24 and the vdpau Xvid error messages have stopped but the image is still pulsing fuzzy every second:

Starting mythfrontend.real..
2011-08-15 19:43:18.786 mythfrontend version: fixes/0.24 [v0.24.1-69-g515171d] [www.mythtv.org](www.mythtv.org)
2011-08-15 19:43:18.786 Using runtime prefix = /usr
2011-08-15 19:43:18.786 Using configuration directory = /home/mythbox/.mythtv
2011-08-15 19:43:18.787 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-08-15 19:43:19.491 Empty LocalHostName.
2011-08-15 19:43:19.492 Using localhost value of mythbox
2011-08-15 19:43:19.503 New DB connection, total: 1
2011-08-15 19:43:19.506 Connected to database 'mythconverg' at host: localhost
2011-08-15 19:43:19.509 Closing DB connection named 'DBManager0'
2011-08-15 19:43:19.509 Connected to database 'mythconverg' at host: localhost
2011-08-15 19:43:19.511 Current locale EN_US
2011-08-15 19:43:19.511 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-08-15 19:43:19.722 ScreenSaverX11Private: Gnome screen saver support enabled
2011-08-15 19:43:19.723 DPMS is active.
2011-08-15 19:43:19.749 Desktop video mode: 1920x1080 60.000 Hz
2011-08-15 19:43:19.774 Enabled verbose msgs:  important general
2011-08-15 19:43:19.791 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2011-08-15 19:43:19.793 New DB connection, total: 2
2011-08-15 19:43:19.794 Loading en_us translation for module mythfrontend
2011-08-15 19:43:19.794 Connected to database 'mythconverg' at host: localhost
2011-08-15 19:43:19.802 LIRC: Successfully initialized '/dev/lircd' using '/home/mythbox/.mythtv/lircrc' config
2011-08-15 19:43:19.802 JoystickMenuThread: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2011-08-15 19:43:19.833 Using Frameless Window
2011-08-15 19:43:19.834 Using Full Screen Window
2011-08-15 19:43:20.090 Using the OpenGL painter
2011-08-15 19:43:20.158 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-08-15 19:43:20.158 OpenGL: OpenGL renderer: GeForce GT 430/PCI/SSE2
2011-08-15 19:43:20.158 OpenGL: OpenGL version : 4.1.0 NVIDIA 260.19.06
2011-08-15 19:43:20.158 OpenGL: Max texture size: 16384 x 16384
2011-08-15 19:43:20.158 OpenGL: Max texture units: 4
2011-08-15 19:43:20.158 OpenGL: Direct rendering: Yes
2011-08-15 19:43:20.158 OpenGL: Initialised MythRenderOpenGL
2011-08-15 19:43:20.340 New DB connection, total: 3
2011-08-15 19:43:20.341 Current MythTV Schema Version (DBSchemaVer): 1264
2011-08-15 19:43:20.343 Connected to database 'mythconverg' at host: localhost
2011-08-15 19:43:20.476 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-08-15 19:43:20.477 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-08-15 19:43:20.478 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-08-15 19:43:20.478 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-08-15 19:43:20.786 Pulse: PulseAudio suspend OK
2011-08-15 19:43:20.983 Pulse: PulseAudio resume OK
2011-08-15 19:43:21.149 Registering Internal as a media playback plugin.
2011-08-15 19:43:21.190 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-15 19:43:21.191 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-15 19:43:21.191 MediaMonitorUnix::AddDevice() - empty device path.
2011-08-15 19:43:21.192 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-08-15 19:43:21.192 Loading en_us translation for module mythgallery
2011-08-15 19:43:21.209 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-08-15 19:43:21.248 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-08-15 19:43:21.254 Loading en_us translation for module mythmusic
2011-08-15 19:43:21.258 Loading en_us translation for module mythnews
2011-08-15 19:43:21.265 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-08-15 19:43:21.283 Loading en_us translation for module mythvideo
2011-08-15 19:43:21.292 Loading en_us translation for module mythweather
2011-08-15 19:43:21.295 NetworkControl: Listening for remote connections on port 6546
2011-08-15 19:43:21.551 Found mainmenu.xml for theme 'Mythbuntu'
2011-08-15 19:43:21.837 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-08-15 19:43:21.838 Using protocol version 63
2011-08-15 19:43:27.964 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythbox/var/lib/mythtv/videos/)
2011-08-15 19:43:27.967 MythVideo::ScanVideoDirectory Scanning (/media/TV_Shows/TV Shows)
2011-08-15 19:44:08.782 TV: Attempting to change from None to WatchingVideo
2011-08-15 19:44:09.115 Pulse: PulseAudio suspend OK
2011-08-15 19:44:10.787 VDPAU: Version 1
2011-08-15 19:44:10.787 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 07:05:35 PDT 2010
2011-08-15 19:44:10.787 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-08-15 19:44:10.787 AFD: Opened codec 0x9b61e90, id(MPEG4) type(Video)
2011-08-15 19:44:10.788 AFD: codec MP3 has 2 channels
2011-08-15 19:44:10.788 AFD: Opened codec 0x9b628c0, id(MP3) type(Audio)
2011-08-15 19:44:10.939 Pulse: PulseAudio resume OK
2011-08-15 19:44:11.139 Pulse: PulseAudio suspend OK
2011-08-15 19:44:11.174 AO: Opening audio device 'plughw:0,9' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-08-15 19:44:11.268 AudioPlayer: Enabling Audio
2011-08-15 19:44:11.293 Clearing OpenGL painter cache.
2011-08-15 19:44:11.442 VDPAU: Created 2 output surfaces.
2011-08-15 19:44:11.442 VDPAU: Created VDPAU render device 1920x1080
2011-08-15 19:44:11.541 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-08-15 19:44:11.618 Player(0): Video timing method: USleep with busy wait
2011-08-15 19:44:11.618 TV: Changing from None to WatchingVideo
2011-08-15 19:44:11.865 ScreenSaverX11Private: DPMS Deactivated 1
2011-08-15 19:44:11.882 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-08-15 19:44:22.052 TV: Attempting to change from WatchingVideo to None
2011-08-15 19:44:22.066 VDPAU Painter: Clearing VDPAU painter cache.
2011-08-15 19:44:22.066 MythPainter: 2 images not yet de-allocated.
2011-08-15 19:44:22.319 Pulse: PulseAudio resume OK
2011-08-15 19:44:22.370 TV: Changing from WatchingVideo to None
2011-08-15 19:44:22.371 ScreenSaverX11Private: DPMS Reactivated 1
2011-08-15 19:44:29.218 OpenGL: Deleting OpenGL Resources
2011-08-15 19:44:29.286 Pulse: Cleaning up PulseHandler
2011-08-15 19:44:29.287 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

---

### Post by nickrout on 2011-08-16
Just on one file, or one particular batch of files? 

What do you mean "pulse"

---

### Post by mtbdrew on 2011-08-16
So far it seems to be any Xvid file in Mythtv or VLC etc. Shows recorded on the box itself and not trans-coded play fine.

Cycles fuzzy to clear to fuzzy to clear continuously.

---

### Post by nickrout on 2011-08-16
> **mtbdrew said:**
> So far it seems to be any Xvid file in Mythtv or VLC etc. Shows recorded on the box itself and not trans-coded play fine.

Cycles fuzzy to clear to fuzzy to clear continuously.

How were these xvid files created? did you transcode them yourself or are they downloaded from somewhere?

Can you make one, or a portion of one that shows the problem, available?

can you post the output of the playback of the file with playback logging enabled?

---

### Post by mtbdrew on 2011-08-16
> **nickrout said:**
> How were these xvid files created? did you transcode them yourself or are they downloaded from somewhere?

Can you make one, or a portion of one that shows the problem, available?

can you post the output of the playback of the file with playback logging enabled?

Downloaded,
Not sure
How do I turn on the playback logging?

---

### Post by nickrout on 2011-08-16
> **mtbdrew said:**
> Downloaded,
Not sure
How do I turn on the playback logging?

edit /etc/mythtv/session-settings to contain a line like:

```
MYTHFRONTEND_OPTS="--verbose playback"
```

and restart mythfrontend

You can play with the options, they can be seen by running from a terminal

```
mythfrontend -v help
```

Here is the output:

> nick@media:~$ mythfrontend -v help
xprop:  unable to open display ''
Verbose debug levels.
 Accepts any combination (separated by comma) of:

 "  all          "  -  ALL available debug output
 "  most         "  -  Most debug (nodatabase,notimestamp,noextra)
 "  important    "  -  Errors or other very important messages
 "  general      "  -  General info
 "  record       "  -  Recording related messages
 "  playback     "  -  Playback related messages
 "  channel      "  -  Channel related messages
 "  osd          "  -  On-Screen Display related messages
 "  file         "  -  File and AutoExpire related messages
 "  schedule     "  -  Scheduling related messages
 "  network      "  -  Network protocol related messages
 "  commflag     "  -  Commercial detection related messages
 "  audio        "  -  Audio related messages
 "  libav        "  -  Enables libav debugging
 "  jobqueue     "  -  JobQueue related messages
 "  siparser     "  -  Siparser related messages
 "  eit          "  -  EIT related messages
 "  vbi          "  -  VBI related messages
 "  database     "  -  Display all SQL commands executed
 "  dsmcc        "  -  DSMCC carousel related messages
 "  mheg         "  -  MHEG debugging messages
 "  upnp         "  -  upnp debugging messages
 "  socket       "  -  socket debugging messages
 "  xmltv        "  -  xmltv output and related messages
 "  dvbcam       "  -  DVB CAM debugging messages
 "  media        "  -  Media Manager debugging messages
 "  idle         "  -  System idle messages
 "  channelscan  "  -  Channel Scanning messages
 "  gui          "  -  GUI related messages
 "  extra        "  -  More detailed messages in selected levels
 "  timestamp    "  -  Conditional data driven messages
 "  none         "  -  NO debug output

 The default for this program appears to be: '-v  "important,general" '

 Most options are additive except for none, all, and important.
 These three are semi-exclusive and take precedence over any
 prior options given.  You can however use something like
 '-v none,jobqueue' to get only JobQueue related messages
 and override the default verbosity level.

 The additive options may also be subtracted from 'all' by
 prefixing them with 'no', so you may use '-v all,nodatabase'
 to view all but database debug messages.

 Some debug levels may not apply to this program.


---

### Post by mtbdrew on 2011-08-16
Here is the log file had to attach it as it was too large.

Thanks

---

### Post by mtbdrew on 2011-08-17
Bump

---

### Post by nickrout on 2011-08-17
have you tried with any windows players? 

or with vdpau disabled?

or with mplayer?

I can't see anything that sticks out of the log, perhaps the files are faulty. I did ask you to post one, or a sample somewhere. You haven't.

---

### Post by mtbdrew on 2011-08-18
I've tried with VLC and mplayer and with MythTV with the vdpau turned off.

Could be the files but can't really see that every single Xvid file is bad.

raw mpeg2 and mkv files are fine.

File is too large how would I post just a portion of it?

Thanks
Andrew

---

