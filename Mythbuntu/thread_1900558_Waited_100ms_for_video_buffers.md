---
title: "Waited 100ms for video buffers"
date: 2011-12-26
forum: Mythbuntu
---

### Post by williammanda on 2011-12-26
Here lately I have come to notice a problem I have had and it is comes in two versions with the "Waited 100ms for video buffers" error in the frontend log. During the time of the issues the cpu load on the backend never got any higher than 50% and this was only a spike. The cpu load on the frontends was about 30%. Also there don't seem to be any network issues.

Hardware:
MBE/FE ( call this FE1 ): C2Q 9300, 4G ram, Nvidia 8400, 11-04 Ubuntu w/ Mythtv latest fixes via MCC, Video profile - slim, Nvidia 290.10
FE2: AMD 64x2 4200, 2G ram, Nvidia 9600GT, 11-10 Ubuntu w/ Mythtv latest fixes via MCC, Video profile - high quality, Nvidia 290.10
FE3: C2D 6400, 2G ram, Nvidia 210, 11-10 Ubuntu w/ Mythtv latest fixes via MCC, Video profile - slim, Nvidia 290.10
FE4: P4, 512M ram, Nvidia ? agp, 11-10 Mythbuntu latest fixes, Video profile - CPU+, Nvidia 290.10

The first scenario:
When playing a tv recording ( this could be the same recording or different ones ) on both FE2 and FE3, the video and audio has intermittent pausing every few seconds. This only happens with a tv recording not a video. This problem is continuous until one FE stops the recording playback. Here is the frontend log from FE2:

```
Starting mythfrontend.real..
2011-12-24 19:26:11.070 mythfrontend version: fixes/0.24 [v0.24.1-112-g40f3bae] www.mythtv.org
2011-12-24 19:26:11.098 Using runtime prefix = /usr
2011-12-24 19:26:11.098 Using configuration directory = /home/william/.mythtv
2011-12-24 19:26:11.177 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-24 19:26:12.083 Empty LocalHostName.
2011-12-24 19:26:12.084 Using localhost value of AMD
2011-12-24 19:26:12.179 New DB connection, total: 1
2011-12-24 19:26:12.187 Unable to connect to database!
2011-12-24 19:26:12.187 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

.
2011-12-24 19:26:12.213 UPnPautoconf() - Found one UPnP backend
2011-12-24 19:26:12.805 Testing network connectivity to '192.168.1.100'
2011-12-24 19:26:12.929 Closing DB connection named 'DBManager0'
2011-12-24 19:26:12.969 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-24 19:26:12.972 Closing DB connection named 'DBManager0'
2011-12-24 19:26:12.976 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-24 19:26:12.980 Current locale en_US
2011-12-24 19:26:13.018 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-12-24 19:26:13.229 ScreenSaverX11Private: XScreenSaver support enabled
2011-12-24 19:26:13.230 DPMS is disabled.
2011-12-24 19:26:13.371 Desktop video mode: 1920x1080 60.000 Hz
2011-12-24 19:26:13.433 Enabled verbose msgs:  important general
2011-12-24 19:26:13.465 Loading en_us translation for module mythfrontend
2011-12-24 19:26:13.586 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2011-12-24 19:26:13.586 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2011-12-24 19:26:13.746 Using Frameless Window
2011-12-24 19:26:13.746 Using Full Screen Window
2011-12-24 19:26:14.250 Using the OpenGL painter
2011-12-24 19:26:14.363 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-12-24 19:26:14.363 OpenGL: OpenGL renderer: GeForce 9600 GT/PCI/SSE2/3DNOW!
2011-12-24 19:26:14.363 OpenGL: OpenGL version : 3.3.0 NVIDIA 280.13
2011-12-24 19:26:14.363 OpenGL: Max texture size: 8192 x 8192
2011-12-24 19:26:14.363 OpenGL: Max texture units: 4
2011-12-24 19:26:14.363 OpenGL: Direct rendering: Yes
2011-12-24 19:26:14.363 OpenGL: Initialised MythRenderOpenGL
2011-12-24 19:26:15.099 Current MythTV Schema Version (DBSchemaVer): 1264
2011-12-24 19:26:16.559 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-12-24 19:26:16.559 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-12-24 19:26:16.590 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-12-24 19:26:16.590 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-12-24 19:26:17.556 Registering Internal as a media playback plugin.
2011-12-24 19:26:17.733 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-24 19:26:17.733 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-24 19:26:17.734 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-24 19:26:17.734 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-12-24 19:26:17.751 Loading en_us translation for module mythgallery
2011-12-24 19:26:18.003 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-12-24 19:26:18.171 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-12-24 19:26:18.209 Loading en_us translation for module mythmusic
2011-12-24 19:26:18.314 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-12-24 19:26:18.406 Loading en_us translation for module mythvideo
2011-12-24 19:26:18.446 Loading en_us translation for module mythweather
2011-12-24 19:26:18.451 NetworkControl: Listening for remote connections on port 6546
2011-12-24 19:26:18.715 Found mainmenu.xml for theme 'Mythbuntu'
2011-12-24 19:26:19.067 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2011-12-24 19:26:19.069 Using protocol version 63
2011-12-24 19:27:15.094 New DB connection, total: 2
2011-12-24 19:27:15.098 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-24 19:27:16.755 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:17.268 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:17.268 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:17.413 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:17.413 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:17.413 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:17.413 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2011-12-24 19:27:25.233 TV: Attempting to change from None to WatchingPreRecorded
2011-12-24 19:27:25.878 AFD: Opened codec 0xaedbf440, id(MPEG2VIDEO) type(Video)
2011-12-24 19:27:25.878 AFD: codec AC3 has 6 channels
2011-12-24 19:27:25.879 AFD: Opened codec 0xaedbe3f0, id(AC3) type(Audio)
2011-12-24 19:27:25.905 AO: Opening audio device 'pulse' ch 2(6) sr 48000 sf 32 bit floating point reenc 0
2011-12-24 19:27:25.912 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-12-24 19:27:26.026 AudioPlayer: Enabling Audio
2011-12-24 19:27:26.172 Clearing OpenGL painter cache.
2011-12-24 19:27:26.315 VDPAU: Created 2 output surfaces.
2011-12-24 19:27:26.315 VDPAU: Version 1
2011-12-24 19:27:26.315 VDPAU: Information NVIDIA VDPAU Driver Shared Library  280.13  Wed Jul 27 17:18:15 PDT 2011
2011-12-24 19:27:26.315 VDPAU: Created VDPAU render device 1920x1080
2011-12-24 19:27:26.508 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-12-24 19:27:26.643 Player(0): Video timing method: USleep with busy wait
2011-12-24 19:27:26.644 TV: Changing from None to WatchingPreRecorded
2011-12-24 19:27:26.823 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-12-24 19:29:22.272 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:22.377 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAADddL
2011-12-24 19:29:22.386 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAADddL
2011-12-24 19:29:22.394 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAADddL
2011-12-24 19:29:30.670 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:30.767 Player(0): Waited 100ms for video buffers AAAdAAAAAAAdDAAAL
2011-12-24 19:29:30.776 Player(0): Waited 100ms for video buffers AAAdAAAAAAAdDAAAL
2011-12-24 19:29:30.785 Player(0): Waited 100ms for video buffers AAUDAAAAALADDAAAL
2011-12-24 19:29:34.872 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:35.318 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:35.559 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:35.659 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.672 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.681 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.787 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.792 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.800 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.809 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.912 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.920 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.929 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:35.938 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.040 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.049 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.058 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.066 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.169 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.178 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.186 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.195 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.297 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.306 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.315 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.426 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.435 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.443 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:36.448 Player(0): Waited 100ms for video buffers LAdAAAdAADAAAAAAA
2011-12-24 19:29:39.142 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:39.234 Player(0): Waited 100ms for video buffers ALDAAAAAAdAAdAAAA
2011-12-24 19:29:39.243 Player(0): Waited 100ms for video buffers ALDAAALAADAADAAAA
2011-12-24 19:29:39.252 Player(0): Waited 100ms for video buffers LuDAAALAADAADAAAA
2011-12-24 19:29:41.523 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:41.839 Player(0): Waited 100ms for video buffers DdAAAALAAAAAAdAAA
2011-12-24 19:29:41.844 Player(0): Waited 100ms for video buffers DdAAAALAAAAAAdAAA
2011-12-24 19:29:41.852 Player(0): Waited 100ms for video buffers DdAAAALAAAAAAdAAA
2011-12-24 19:29:41.861 Player(0): Waited 100ms for video buffers DdAAAALAAAAAAdAAA
2011-12-24 19:29:42.185 RingBuf(/var/lib/mythtv/recordings/2051_20111221210000.mpg): Waited 0.2 seconds for data 
			to become available... 0 < 32768
2011-12-24 19:29:42.377 Player(0): Waited 100ms for video buffers AAAAAAADAAuLAADDL
2011-12-24 19:29:43.633 Player(0): Waited 100ms for video buffers AAAAAAADdAdAAAALA
2011-12-24 19:29:43.646 Player(0): Waited 100ms for video buffers AAAAAAADdAdAAAALA
2011-12-24 19:29:43.655 Player(0): Waited 100ms for video buffers AAAAAAADdAdAAAALA
2011-12-24 19:29:46.095 Player(0): Waited 100ms for video buffers AAdALAAAAAAADAAAd
2011-12-24 19:29:46.108 Player(0): Waited 100ms for video buffers AADALAAAALAADAAAD
2011-12-24 19:29:46.117 Player(0): Waited 100ms for video buffers ALDAuAAAALAADAAAD
2011-12-24 19:29:47.852 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:51.199 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:52.794 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:29:52.893 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:52.901 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:52.906 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:52.914 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.021 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.029 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.034 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.042 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.149 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.154 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.162 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.171 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.282 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.291 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.299 Player(0): Waited 100ms for video buffers AAALAdADAAAAADAAA
2011-12-24 19:29:53.617 RingBuf(/var/lib/mythtv/recordings/2051_20111221210000.mpg): Waited 0.2 seconds for data 
			to become available... 0 < 32768
2011-12-24 19:29:59.880 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:29:59.889 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:29:59.902 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.009 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.017 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.022 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.030 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.142 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.150 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.159 Player(0): Waited 100ms for video buffers AAAAAAAAADAAdAADL
2011-12-24 19:30:00.722 Player(0): Waited 100ms for video buffers LDdADAAAAAAAAAAAA
2011-12-24 19:30:00.731 Player(0): Waited 100ms for video buffers LDdADAAAAAAAAAAAA
2011-12-24 19:30:00.736 Player(0): Waited 100ms for video buffers LDdADAAAAAAAAAAAA
2011-12-24 19:30:00.744 Player(0): Waited 100ms for video buffers LDdADAAAAAAAAAAAA
2011-12-24 19:30:00.851 Player(0): Waited 100ms for video buffers LDDADALAAAAAAAAAA
2011-12-24 19:30:02.128 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:03.228 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:03.425 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:03.522 Player(0): Waited 100ms for video buffers AAAAAAAAAAADDALAd
2011-12-24 19:30:03.527 Player(0): Waited 100ms for video buffers AAAAAAAAAAADDALAd
2011-12-24 19:30:03.535 Player(0): Waited 100ms for video buffers AAAAAAAAAAADDALAd
2011-12-24 19:30:03.544 Player(0): Waited 100ms for video buffers AAAAAAAAAAADDALAd
2011-12-24 19:30:05.041 Player(0): Waited 100ms for video buffers ALDAdAAAAAAAAAAAD
2011-12-24 19:30:05.050 Player(0): Waited 100ms for video buffers ALDAdAAAAAAAAAAAD
2011-12-24 19:30:05.063 Player(0): Waited 100ms for video buffers ALDAdAAAAAAAAAAAD
2011-12-24 19:30:06.299 RingBuf(/var/lib/mythtv/recordings/2051_20111221210000.mpg): Waited 0.2 seconds for data 
			to become available... 0 < 32768
2011-12-24 19:30:07.364 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:07.526 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:07.626 Player(0): Waited 100ms for video buffers AAADADAAAUDLLAAfA
2011-12-24 19:30:09.069 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:09.163 Player(0): Waited 100ms for video buffers ALdADADAAAAAAAAFA
2011-12-24 19:30:09.176 Player(0): Waited 100ms for video buffers ALdADADAAAAAAAAFA
2011-12-24 19:30:09.185 Player(0): Waited 100ms for video buffers ALdADADAAAAAAAAFA
2011-12-24 19:30:10.700 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:11.996 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:12.183 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:12.326 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:12.421 Player(0): Waited 100ms for video buffers AAAAdALAAAAAdAAFD
2011-12-24 19:30:12.430 Player(0): Waited 100ms for video buffers AAAAdALAAAAAdAAFD
2011-12-24 19:30:12.438 Player(0): Waited 100ms for video buffers AAAAdALAAAAAdAAFD
2011-12-24 19:30:12.443 Player(0): Waited 100ms for video buffers AAAAdALAAAAAdAAFD
2011-12-24 19:30:12.788 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.796 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.801 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.809 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.916 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.921 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.929 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:12.938 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.044 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.049 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.057 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.066 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.169 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.177 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.186 Player(0): Waited 100ms for video buffers ADLAAAdAdAAAAAAFA
2011-12-24 19:30:13.195 Player(0): Waited 100ms for video buffers ADLAALDADAAAAAAFA
2011-12-24 19:30:14.441 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:14.536 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.541 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.549 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.558 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.661 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.669 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.678 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.686 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.789 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.797 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.806 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:14.815 Player(0): Waited 100ms for video buffers AAdAALAAADDAAAAFA
2011-12-24 19:30:16.208 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:17.419 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:17.647 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:20.970 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:21.123 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:21.262 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:21.360 Player(0): Waited 100ms for video buffers ADAAAAAADAAALAdFA
2011-12-24 19:30:25.006 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.014 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.023 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.032 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.134 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.143 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.147 RingBuf(/var/lib/mythtv/recordings/2051_20111221210000.mpg): Waited 0.5 seconds for data 
			to become available... 0 < 32768
2011-12-24 19:30:25.151 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.160 Player(0): Waited 100ms for video buffers DAAALAAAAAAAAAdFd
2011-12-24 19:30:25.643 RingBuf(/var/lib/mythtv/recordings/2051_20111221210000.mpg): Waited 0.2 seconds for data 
			to become available... 0 < 32768
2011-12-24 19:30:28.032 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:28.194 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:28.318 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:28.413 Player(0): Waited 100ms for video buffers AAAADAAAAdALdAAFA
2011-12-24 19:30:28.422 Player(0): Waited 100ms for video buffers AAAADAAAAdALdAAFA
2011-12-24 19:30:28.431 Player(0): Waited 100ms for video buffers AAAADAAAAdALdAAFA
2011-12-24 19:30:28.440 Player(0): Waited 100ms for video buffers AAAADAAAAdALdAAFA
2011-12-24 19:30:34.865 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:37.216 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:37.493 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:37.590 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.603 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.612 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.723 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.731 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.740 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.843 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.851 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.860 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.868 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.971 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.980 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.988 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:37.997 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:38.724 RingBuf(/var/lib/mythtv/recordings/2051_20111221210000.mpg): Waited 0.5 seconds for data 
			to become available... 0 < 32768
2011-12-24 19:30:38.852 Player(0): Waited 100ms for video buffers AAAAAADAAALADdAAA
2011-12-24 19:30:38.861 Player(0): Waited 100ms for video buffers AAAAAADAAALADdAAA
2011-12-24 19:30:38.874 Player(0): Waited 100ms for video buffers AAAAAADAAALADdAAA
2011-12-24 19:30:38.981 Player(0): Waited 100ms for video buffers AAAAAADAAALADdAAA
2011-12-24 19:30:38.994 Player(0): Waited 100ms for video buffers AAAAAADAAALADdAAA
2011-12-24 19:30:39.003 Player(0): Waited 100ms for video buffers AAAAAADAAALADdAAA
2011-12-24 19:30:40.852 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:40.988 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:41.090 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:41.098 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:41.103 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:41.111 Player(0): Waited 100ms for video buffers AAALAdADAAAdAAAAA
2011-12-24 19:30:42.534 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:42.924 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:43.042 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:43.515 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.523 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.532 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.541 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.644 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.652 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.661 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.670 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.772 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.781 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.790 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:43.798 Player(0): Waited 100ms for video buffers AAAAAAdAALAAdDAAA
2011-12-24 19:30:45.659 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:45.804 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:30:45.949 ALSA, Error: WriteAudio: buffer underrun
2011-12-24 19:40:30.696 TV: Attempting to change from WatchingPreRecorded to None
2011-12-24 19:40:30.715 VDPAU Painter: Clearing VDPAU painter cache.
2011-12-24 19:40:30.717 MythPainter: 2 images not yet de-allocated.
2011-12-24 19:40:30.805 TV: Changing from WatchingPreRecorded to None
```

This situation only occurs with FE2 and FE3. I have tried all combinations (FE1 & FE2, FE1 & FE3, FE1 & FE4, etc...).

The 2nd scenario:
When playing a video or tv recording and I select skip forward / the right arrow key ( sometimes change the volume for the 1st time ) with the keyboard or remote on FE2 or FE3 I get this: Here is the frontend log from FE2

```
Starting mythfrontend.real..
2011-12-26 12:46:12.738 mythfrontend version: fixes/0.24 [v0.24.1-112-g40f3bae] www.mythtv.org
2011-12-26 12:46:12.738 Using runtime prefix = /usr
2011-12-26 12:46:12.738 Using configuration directory = /home/william/.mythtv
2011-12-26 12:46:12.758 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-26 12:46:13.608 Empty LocalHostName.
2011-12-26 12:46:13.608 Using localhost value of AMD
2011-12-26 12:46:13.650 New DB connection, total: 1
2011-12-26 12:46:13.650 Unable to connect to database!
2011-12-26 12:46:13.650 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


2011-12-26 12:46:13.777 UPnPautoconf() - Found one UPnP backend
2011-12-26 12:46:13.995 Testing network connectivity to '192.168.1.100'
2011-12-26 12:46:14.098 Closing DB connection named 'DBManager0'
2011-12-26 12:46:14.102 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 12:46:14.106 Closing DB connection named 'DBManager0'
2011-12-26 12:46:14.110 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 12:46:14.115 Current locale en_US
2011-12-26 12:46:14.115 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-12-26 12:46:14.298 ScreenSaverX11Private: XScreenSaver support enabled
2011-12-26 12:46:14.299 DPMS is disabled.
2011-12-26 12:46:14.335 Desktop video mode: 1920x1080 60.000 Hz
2011-12-26 12:46:14.398 Enabled verbose msgs:  important general
2011-12-26 12:46:14.416 Loading en_us translation for module mythfrontend
2011-12-26 12:46:14.453 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2011-12-26 12:46:14.454 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2011-12-26 12:46:14.615 Using Frameless Window
2011-12-26 12:46:14.615 Using Full Screen Window
2011-12-26 12:46:15.044 Using the OpenGL painter
2011-12-26 12:46:15.177 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-12-26 12:46:15.177 OpenGL: OpenGL renderer: GeForce 9600 GT/PCI/SSE2/3DNOW!
2011-12-26 12:46:15.177 OpenGL: OpenGL version : 3.3.0 NVIDIA 290.10
2011-12-26 12:46:15.177 OpenGL: Max texture size: 8192 x 8192
2011-12-26 12:46:15.178 OpenGL: Max texture units: 4
2011-12-26 12:46:15.178 OpenGL: Direct rendering: Yes
2011-12-26 12:46:15.178 OpenGL: Initialised MythRenderOpenGL
2011-12-26 12:46:15.400 New DB connection, total: 2
2011-12-26 12:46:15.401 New DB connection, total: 3
2011-12-26 12:46:15.407 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 12:46:15.407 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 12:46:15.412 Current MythTV Schema Version (DBSchemaVer): 1264
2011-12-26 12:46:15.755 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-12-26 12:46:15.756 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-12-26 12:46:15.756 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-12-26 12:46:15.756 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-12-26 12:46:16.164 Pulse: PulseAudio suspend OK
2011-12-26 12:46:16.361 Pulse: PulseAudio resume OK
2011-12-26 12:46:16.960 Registering Internal as a media playback plugin.
2011-12-26 12:46:17.074 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-26 12:46:17.075 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-26 12:46:17.075 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-26 12:46:17.075 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-12-26 12:46:17.075 Loading en_us translation for module mythgallery
2011-12-26 12:46:17.212 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-12-26 12:46:17.366 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-12-26 12:46:17.389 Loading en_us translation for module mythmusic
2011-12-26 12:46:17.448 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-12-26 12:46:17.523 Loading en_us translation for module mythvideo
2011-12-26 12:46:17.565 Loading en_us translation for module mythweather
2011-12-26 12:46:17.570 NetworkControl: Listening for remote connections on port 6546
2011-12-26 12:46:17.800 Found mainmenu.xml for theme 'Mythbuntu'
2011-12-26 12:46:18.114 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2011-12-26 12:46:18.116 Using protocol version 63
2011-12-26 12:46:31.057 TV: Attempting to change from None to WatchingPreRecorded
2011-12-26 12:46:31.381 Pulse: PulseAudio suspend OK
2011-12-26 12:46:31.577 AFD: Opened codec 0x9c1ea750, id(MPEG2VIDEO) type(Video)
2011-12-26 12:46:31.577 AFD: codec AC3 has 6 channels
2011-12-26 12:46:31.578 AFD: Opened codec 0x9b54f3a0, id(AC3) type(Audio)
2011-12-26 12:46:31.681 Pulse: PulseAudio resume OK
2011-12-26 12:46:31.882 Pulse: PulseAudio suspend OK
2011-12-26 12:46:31.946 AO: Opening audio device 'dmix:CARD=NVidia,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2011-12-26 12:46:32.007 ALSA, Error: Setting hardware audio buffer size to 6016
2011-12-26 12:46:32.007 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-12-26 12:46:32.007 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-12-26 12:46:32.007 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-12-26 12:46:32.080 AudioPlayer: Enabling Audio
2011-12-26 12:46:32.229 Clearing OpenGL painter cache.
2011-12-26 12:46:32.531 VDPAU: Created 2 output surfaces.
2011-12-26 12:46:32.531 VDPAU: Version 1
2011-12-26 12:46:32.531 VDPAU: Information NVIDIA VDPAU Driver Shared Library  290.10  Wed Nov 16 19:53:31 PST 2011
2011-12-26 12:46:32.531 VDPAU: Created VDPAU render device 1920x1080
2011-12-26 12:46:32.633 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-12-26 12:46:32.697 Player(0): Video sync method can't support double framerate (refresh rate too low for 2x deint)
2011-12-26 12:46:32.707 Player(0): Video timing method: USleep with busy wait
2011-12-26 12:46:32.714 TV: Changing from None to WatchingPreRecorded
2011-12-26 12:46:32.801 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-12-26 12:46:37.220 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAALL
2011-12-26 12:47:27.306 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:27.308 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:27.313 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:27.315 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:27.322 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:27.325 Player(0): Waited 100ms for video buffers ALAAAAAAAAAAAAAAA
2011-12-26 12:47:27.329 Player(0): Waited 100ms for video buffers ALAAAAAAALAAAAAAA
2011-12-26 12:47:27.332 Player(0): Waited 100ms for video buffers AuAAAAAAALAAAAAAA
2011-12-26 12:47:28.931 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:28.938 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:28.940 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
2011-12-26 12:47:28.947 Player(0): Waited 100ms for video buffers ALAAAAAAAAAAAAAAA
2011-12-26 12:47:28.949 Player(0): Waited 100ms for video buffers ALAAAAAAAAAAAAAAA
2011-12-26 12:48:22.832 TV: Attempting to change from WatchingPreRecorded to None
2011-12-26 12:48:22.836 VDPAU Painter: Clearing VDPAU painter cache.
2011-12-26 12:48:22.840 MythPainter: 2 images not yet de-allocated.
2011-12-26 12:48:23.017 Pulse: PulseAudio resume OK
2011-12-26 12:48:23.018 TV: Changing from WatchingPreRecorded to None
2011-12-26 12:48:26.651 OpenGL: Deleting OpenGL Resources
2011-12-26 12:48:26.691 Pulse: Cleaning up PulseHandler
2011-12-26 12:48:26.691 Deleting UPnP client...
```

If I don't select skip forward / right arrow key the error doesn't occur. Here is the frontend log from FE2:

```
Starting mythfrontend.real..
2011-12-26 13:20:10.247 mythfrontend version: fixes/0.24 [v0.24.1-112-g40f3bae] www.mythtv.org
2011-12-26 13:20:10.247 Using runtime prefix = /usr
2011-12-26 13:20:10.247 Using configuration directory = /home/william/.mythtv
2011-12-26 13:20:10.261 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-26 13:20:11.111 Empty LocalHostName.
2011-12-26 13:20:11.111 Using localhost value of AMD
2011-12-26 13:20:11.158 New DB connection, total: 1
2011-12-26 13:20:11.158 Unable to connect to database!
2011-12-26 13:20:11.158 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


2011-12-26 13:20:11.285 UPnPautoconf() - Found one UPnP backend
2011-12-26 13:20:11.532 Testing network connectivity to '192.168.1.100'
2011-12-26 13:20:11.638 Closing DB connection named 'DBManager0'
2011-12-26 13:20:11.652 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 13:20:11.655 Closing DB connection named 'DBManager0'
2011-12-26 13:20:11.659 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 13:20:11.664 Current locale en_US
2011-12-26 13:20:11.664 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-12-26 13:20:11.938 ScreenSaverX11Private: XScreenSaver support enabled
2011-12-26 13:20:11.939 DPMS is disabled.
2011-12-26 13:20:11.971 Desktop video mode: 1920x1080 60.000 Hz
2011-12-26 13:20:12.038 Enabled verbose msgs:  important general
2011-12-26 13:20:12.052 Loading en_us translation for module mythfrontend
2011-12-26 13:20:12.091 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2011-12-26 13:20:12.091 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2011-12-26 13:20:12.250 Using Frameless Window
2011-12-26 13:20:12.250 Using Full Screen Window
2011-12-26 13:20:12.686 Using the OpenGL painter
2011-12-26 13:20:12.813 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-12-26 13:20:12.813 OpenGL: OpenGL renderer: GeForce 9600 GT/PCI/SSE2/3DNOW!
2011-12-26 13:20:12.813 OpenGL: OpenGL version : 3.3.0 NVIDIA 290.10
2011-12-26 13:20:12.813 OpenGL: Max texture size: 8192 x 8192
2011-12-26 13:20:12.813 OpenGL: Max texture units: 4
2011-12-26 13:20:12.813 OpenGL: Direct rendering: Yes
2011-12-26 13:20:12.813 OpenGL: Initialised MythRenderOpenGL
2011-12-26 13:20:13.023 New DB connection, total: 2
2011-12-26 13:20:13.023 New DB connection, total: 3
2011-12-26 13:20:13.028 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 13:20:13.028 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-26 13:20:13.038 Current MythTV Schema Version (DBSchemaVer): 1264
2011-12-26 13:20:13.373 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-12-26 13:20:13.374 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-12-26 13:20:13.374 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-12-26 13:20:13.374 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-12-26 13:20:13.802 Pulse: PulseAudio suspend OK
2011-12-26 13:20:14.000 Pulse: PulseAudio resume OK
2011-12-26 13:20:14.599 Registering Internal as a media playback plugin.
2011-12-26 13:20:14.705 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-26 13:20:14.706 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-26 13:20:14.706 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-26 13:20:14.706 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-12-26 13:20:14.707 Loading en_us translation for module mythgallery
2011-12-26 13:20:14.837 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-12-26 13:20:14.994 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-12-26 13:20:15.018 Loading en_us translation for module mythmusic
2011-12-26 13:20:15.083 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-12-26 13:20:15.161 Loading en_us translation for module mythvideo
2011-12-26 13:20:15.202 Loading en_us translation for module mythweather
2011-12-26 13:20:15.207 NetworkControl: Listening for remote connections on port 6546
2011-12-26 13:20:15.459 Found mainmenu.xml for theme 'Mythbuntu'
2011-12-26 13:20:15.777 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2011-12-26 13:20:15.778 Using protocol version 63
2011-12-26 13:20:34.748 TV: Attempting to change from None to WatchingPreRecorded
2011-12-26 13:20:35.227 Pulse: PulseAudio suspend OK
2011-12-26 13:20:35.911 AFD: Opened codec 0xae4a0300, id(MPEG2VIDEO) type(Video)
2011-12-26 13:20:35.911 AFD: codec AC3 has 6 channels
2011-12-26 13:20:35.912 AFD: Opened codec 0xae4a7a90, id(AC3) type(Audio)
2011-12-26 13:20:36.028 Pulse: PulseAudio resume OK
2011-12-26 13:20:36.227 Pulse: PulseAudio suspend OK
2011-12-26 13:20:36.288 AO: Opening audio device 'dmix:CARD=NVidia,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2011-12-26 13:20:36.339 ALSA, Error: Setting hardware audio buffer size to 6016
2011-12-26 13:20:36.339 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-12-26 13:20:36.339 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-12-26 13:20:36.339 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-12-26 13:20:36.436 AudioPlayer: Enabling Audio
2011-12-26 13:20:36.541 Clearing OpenGL painter cache.
2011-12-26 13:20:36.644 VDPAU: Created 2 output surfaces.
2011-12-26 13:20:36.644 VDPAU: Version 1
2011-12-26 13:20:36.644 VDPAU: Information NVIDIA VDPAU Driver Shared Library  290.10  Wed Nov 16 19:53:31 PST 2011
2011-12-26 13:20:36.644 VDPAU: Created VDPAU render device 1920x1080
2011-12-26 13:20:36.832 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-12-26 13:20:36.885 Player(0): Video timing method: USleep with busy wait
2011-12-26 13:20:36.894 TV: Changing from None to WatchingPreRecorded
2011-12-26 13:20:37.046 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-12-26 13:50:33.444 [ac3 @ 0x16dab40]incomplete frame
2011-12-26 13:50:33.560 TV: Attempting to change from WatchingPreRecorded to None
2011-12-26 13:50:33.564 VDPAU Painter: Clearing VDPAU painter cache.
2011-12-26 13:50:33.564 MythPainter: 2 images not yet de-allocated.
2011-12-26 13:50:33.809 Pulse: PulseAudio resume OK
2011-12-26 13:50:33.814 TV: Changing from WatchingPreRecorded to None
```

This the backend log:

```
2011-12-26 07:16:46.466 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2011-12-26 07:16:46.505 Using protocol version 63
2011-12-26 07:16:46.547 MainServer::ANN Monitor
2011-12-26 07:16:46.588 adding: C2Q as a client (events: 0)
2011-12-26 07:16:46.630 MainServer::ANN Monitor
2011-12-26 07:16:46.672 adding: C2Q as a client (events: 1)
2011-12-26 07:16:46.714 Reschedule requested for id -1.
2011-12-26 07:16:46.716 Received a remote 'Clear Cache' request
2011-12-26 07:16:47.653 Scheduled 139 items in 0.9 = 0.12 match + 0.80 place
2011-12-26 07:16:47.715 mythfilldatabase run complete.
2011-12-26 07:16:47.751 DataDirect: Deleting temporary files
2011-12-26 07:17:02.561 MainServer::ANN Monitor
2011-12-26 07:17:02.630 adding: C2Q as a client (events: 2)
2011-12-26 07:19:01.128 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 07:22:42.613 MainServer::ANN Monitor
2011-12-26 07:22:42.651 adding: C2Q as a client (events: 0)
2011-12-26 07:23:10.470 MainServer::ANN Monitor
2011-12-26 07:23:10.500 adding: C2Q as a client (events: 0)
2011-12-26 07:23:10.535 MainServer::ANN Monitor
2011-12-26 07:23:10.668 adding: C2Q as a client (events: 1)
2011-12-26 07:23:14.027 MainServer::ANN Monitor
2011-12-26 07:23:14.058 adding: C2Q as a client (events: 0)
2011-12-26 07:23:14.093 MainServer::ANN Monitor
2011-12-26 07:23:14.125 adding: C2Q as a client (events: 1)
2011-12-26 07:23:47.890 MainServer::ANN Monitor
2011-12-26 07:23:47.922 adding: C2Q as a client (events: 0)
2011-12-26 07:23:47.956 MainServer::ANN Monitor
2011-12-26 07:23:47.989 adding: C2Q as a client (events: 1)
Error in my_thread_global_end(): 1 threads didn't exit
2011-12-26 07:24:03.461 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 07:24:03.646 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 07:33:18.460 MainServer::ANN Monitor
2011-12-26 07:33:18.500 adding: C2Q as a client (events: 0)
2011-12-26 07:34:01.269 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 07:49:01.435 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 07:49:15.305 MainServer::ANN Monitor
2011-12-26 07:49:15.343 adding: C2Q as a client (events: 0)
2011-12-26 07:54:03.713 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 07:54:03.890 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 07:56:49.408 MainServer::ANN Monitor
2011-12-26 07:56:49.438 adding: C2Q as a client (events: 0)
2011-12-26 07:56:49.798 MainServer::ANN Monitor
2011-12-26 07:56:49.863 adding: C2Q as a client (events: 2)
2011-12-26 07:58:44.373 MainServer::ANN Monitor
2011-12-26 07:58:44.428 adding: C2Q as a client (events: 2)
2011-12-26 08:03:24.773 MainServer::ANN Monitor
2011-12-26 08:03:24.804 adding: C2Q as a client (events: 0)
2011-12-26 08:04:01.590 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 08:17:01.406 MainServer::ANN Monitor
2011-12-26 08:17:01.457 adding: C2Q as a client (events: 2)
2011-12-26 08:18:27.736 MainServer::ANN Monitor
2011-12-26 08:18:27.798 adding: C2Q as a client (events: 0)
2011-12-26 08:19:01.754 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 08:24:04.960 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 08:24:05.155 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 08:33:30.841 MainServer::ANN Monitor
2011-12-26 08:33:30.875 adding: C2Q as a client (events: 0)
2011-12-26 08:34:01.883 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 08:47:51.945 MainServer::ANN Monitor
2011-12-26 08:47:51.980 adding: AMD as a client (events: 0)
2011-12-26 08:47:52.024 MainServer::ANN Monitor
2011-12-26 08:47:52.064 adding: AMD as a client (events: 1)
2011-12-26 08:48:08.923 MainServer::ANN Playback
2011-12-26 08:48:08.972 adding: amd as a client (events: 0)
2011-12-26 08:48:09.006 MainServer::HandleAnnounce FileTransfer
2011-12-26 08:48:09.038 adding: amd as a remote file transfer
2011-12-26 08:48:12.785 MainServer::ANN Monitor
2011-12-26 08:48:12.813 adding: C2Q as a client (events: 0)
2011-12-26 08:48:12.847 MainServer::ANN Monitor
2011-12-26 08:48:12.889 adding: C2Q as a client (events: 1)
2011-12-26 08:48:54.595 MainServer::ANN Monitor
2011-12-26 08:48:54.626 adding: C2Q as a client (events: 0)
2011-12-26 08:49:02.010 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 08:54:05.238 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 08:54:05.419 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 08:57:18.935 MainServer::ANN Monitor
2011-12-26 08:57:18.990 adding: C2Q as a client (events: 0)
2011-12-26 08:57:19.024 MainServer::ANN Monitor
2011-12-26 08:57:19.056 adding: C2Q as a client (events: 1)
2011-12-26 08:57:20.118 Reschedule requested for id 0.
2011-12-26 08:57:20.926 Scheduled 139 items in 0.8 = 0.04 match + 0.76 place
Error in my_thread_global_end(): 1 threads didn't exit
2011-12-26 08:57:24.698 Preview Error: Preview process not ok.
			fileinfo(/media/sdb1/recordings/2051_20111223210000.mpg.png) exists: 0 readable: 0 size: 0
2011-12-26 08:57:24.734 Preview Error: Despite command '/usr/bin/mythpreviewgen --size 0x0 --chanid 2051 --starttime 20111223210000  > /dev/null' returning success
2011-12-26 08:57:27.177 Reschedule requested for id 0.
2011-12-26 08:57:27.951 Scheduled 139 items in 0.8 = 0.03 match + 0.73 place
2011-12-26 09:03:37.082 MainServer::ANN Monitor
2011-12-26 09:03:37.116 adding: C2Q as a client (events: 0)
2011-12-26 09:04:02.169 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 09:17:02.348 MainServer::ANN Monitor
2011-12-26 09:17:02.411 adding: C2Q as a client (events: 2)
2011-12-26 09:18:40.054 MainServer::ANN Monitor
2011-12-26 09:18:40.084 adding: C2Q as a client (events: 0)
2011-12-26 09:19:02.331 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 09:24:10.521 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 09:24:10.716 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 09:34:02.463 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 09:34:42.694 MainServer::ANN Monitor
2011-12-26 09:34:42.730 adding: C2Q as a client (events: 0)
2011-12-26 09:48:46.201 MainServer::ANN Monitor
2011-12-26 09:48:46.256 adding: C2Q as a client (events: 0)
2011-12-26 09:49:02.596 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 09:54:12.785 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 09:54:12.983 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 10:03:49.445 MainServer::ANN Monitor
2011-12-26 10:03:49.473 adding: C2Q as a client (events: 0)
2011-12-26 10:04:02.730 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 10:17:01.660 MainServer::ANN Monitor
2011-12-26 10:17:01.729 adding: C2Q as a client (events: 2)
2011-12-26 10:19:02.858 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 10:19:53.633 MainServer::ANN Monitor
2011-12-26 10:19:53.693 adding: C2Q as a client (events: 0)
2011-12-26 10:24:15.056 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 10:24:15.238 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 10:34:02.985 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 10:45:35.692 MainServer::ANN Monitor
2011-12-26 10:45:35.724 adding: C2Q as a client (events: 0)
2011-12-26 10:45:35.758 MainServer::ANN Monitor
2011-12-26 10:45:35.791 adding: C2Q as a client (events: 1)
2011-12-26 10:45:37.177 Reschedule requested for id 0.
2011-12-26 10:45:38.032 Scheduled 139 items in 0.8 = 0.04 match + 0.80 place
2011-12-26 10:45:44.597 Reschedule requested for id 0.
2011-12-26 10:45:45.349 Scheduled 139 items in 0.7 = 0.04 match + 0.70 place
2011-12-26 10:46:05.202 Reschedule requested for id 0.
2011-12-26 10:46:05.954 Scheduled 139 items in 0.7 = 0.04 match + 0.70 place
2011-12-26 10:46:12.343 Reschedule requested for id 0.
2011-12-26 10:46:13.091 Scheduled 139 items in 0.7 = 0.04 match + 0.69 place
2011-12-26 10:46:37.936 MainServer::ANN Monitor
2011-12-26 10:46:37.987 adding: C2Q as a client (events: 0)
2011-12-26 10:49:03.111 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 10:51:34.411 Reschedule requested for id 287.
2011-12-26 10:51:35.209 Scheduled 140 items in 0.8 = 0.08 match + 0.70 place
2011-12-26 10:52:00.108 Reschedule requested for id 288.
2011-12-26 10:52:00.900 Scheduled 141 items in 0.8 = 0.07 match + 0.71 place
2011-12-26 10:52:45.117 Reschedule requested for id 289.
2011-12-26 10:52:45.907 Scheduled 142 items in 0.8 = 0.06 match + 0.72 place
2011-12-26 10:54:18.312 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 10:54:18.510 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 11:04:03.294 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 11:07:40.184 MainServer::ANN Monitor
2011-12-26 11:07:40.218 adding: C2Q as a client (events: 0)
2011-12-26 11:17:01.786 MainServer::ANN Monitor
2011-12-26 11:17:01.837 adding: C2Q as a client (events: 2)
2011-12-26 11:19:01.230 MainServer::ANN Monitor
2011-12-26 11:19:01.258 adding: C2Q as a client (events: 0)
2011-12-26 11:19:03.453 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 11:24:22.580 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 11:24:22.767 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 11:34:03.600 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 11:34:04.329 MainServer::ANN Monitor
2011-12-26 11:34:04.367 adding: C2Q as a client (events: 0)
2011-12-26 11:49:03.726 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 11:54:28.833 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 11:54:29.026 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 11:56:09.306 MainServer::ANN Monitor
2011-12-26 11:56:09.332 adding: AMD as a client (events: 0)
2011-12-26 11:56:14.983 MainServer::ANN Monitor
2011-12-26 11:56:15.015 adding: AMD as a client (events: 0)
2011-12-26 11:56:15.050 MainServer::ANN Monitor
2011-12-26 11:56:15.082 adding: AMD as a client (events: 1)
2011-12-26 11:56:40.834 MainServer::ANN Monitor
2011-12-26 11:56:40.872 adding: C2Q as a client (events: 0)
2011-12-26 11:56:40.906 MainServer::ANN Monitor
2011-12-26 11:56:40.980 adding: C2Q as a client (events: 1)
2011-12-26 11:56:41.896 MainServer::ANN Monitor
2011-12-26 11:56:41.931 adding: C2Q as a client (events: 0)
2011-12-26 11:56:41.966 MainServer::ANN Monitor
2011-12-26 11:56:41.998 adding: C2Q as a client (events: 1)
2011-12-26 12:04:03.854 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 12:13:59.779 MainServer::ANN Monitor
2011-12-26 12:13:59.819 adding: AMD as a client (events: 0)
2011-12-26 12:13:59.858 MainServer::ANN Monitor
2011-12-26 12:13:59.894 adding: AMD as a client (events: 1)
2011-12-26 12:17:02.005 MainServer::ANN Monitor
2011-12-26 12:17:02.055 adding: C2Q as a client (events: 2)
2011-12-26 12:19:04.004 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 12:24:34.095 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 12:24:34.285 UPnpMedia: BuildMediaMap Done. Found 672 objects
2011-12-26 12:34:04.125 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 12:34:17.035 MainServer::ANN Monitor
2011-12-26 12:34:17.075 adding: C2Q as a client (events: 0)
2011-12-26 12:46:18.364 MainServer::ANN Monitor
2011-12-26 12:46:18.399 adding: AMD as a client (events: 0)
2011-12-26 12:46:18.434 MainServer::ANN Monitor
2011-12-26 12:46:18.474 adding: AMD as a client (events: 1)
2011-12-26 12:49:04.254 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-26 12:50:30.768 MainServer::ANN Monitor
2011-12-26 12:50:30.804 adding: AMD as a client (events: 0)
2011-12-26 12:50:30.839 MainServer::ANN Monitor
2011-12-26 12:50:30.871 adding: AMD as a client (events: 1)
2011-12-26 12:54:35.355 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2011-12-26 12:54:35.549 UPnpMedia: BuildMediaMap Done. Found 672 objects
```

---

### Post by williammanda on 2011-12-29
I reinstalled ubuntu 11.10 and mythtv .24 on both frontends and upgraded the FE / BE to ubuntu 11.10 and reinstalled mythtv .24 and still get the same issues of intermittent video and audio. Has some change happened that could have caused this? This system was working correctly for months.

---

### Post by williammanda on 2011-12-30
I tried a stab in the dark and apparently got lucky. I commented out the recordings statement in the export file on the backend. Now both FE2 and FE3 can play recordings at the same time without the stuttering video / audio and no "Waited 100ms for video buffers". Maybe someone can answer this question...was there a change in Mythtv in reference to NFS? The export file was created automatically by Mythbuntu.


```
Starting mythfrontend.real..
2011-12-30 10:15:08.616 mythfrontend version: fixes/0.24 [v0.24.1-112-g40f3bae] www.mythtv.org
2011-12-30 10:15:08.616 Using runtime prefix = /usr
2011-12-30 10:15:08.616 Using configuration directory = /home/william/.mythtv
2011-12-30 10:15:08.626 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-30 10:15:09.490 Empty LocalHostName.
2011-12-30 10:15:09.491 Using localhost value of AMD
2011-12-30 10:15:09.549 New DB connection, total: 1
2011-12-30 10:15:09.550 Unable to connect to database!
2011-12-30 10:15:09.550 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

.
2011-12-30 10:15:09.576 UPnPautoconf() - Found one UPnP backend
2011-12-30 10:15:09.964 Testing network connectivity to '192.168.1.100'
2011-12-30 10:15:10.067 Closing DB connection named 'DBManager0'
2011-12-30 10:15:10.071 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-30 10:15:10.074 Closing DB connection named 'DBManager0'
2011-12-30 10:15:10.078 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-30 10:15:10.082 Current locale en_US
2011-12-30 10:15:10.082 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-12-30 10:15:10.368 ScreenSaverX11Private: XScreenSaver support enabled
2011-12-30 10:15:10.369 DPMS is disabled.
2011-12-30 10:15:10.416 Desktop video mode: 1920x1080 60.000 Hz
2011-12-30 10:15:10.480 Enabled verbose msgs:  important general
2011-12-30 10:15:10.509 Loading en_us translation for module mythfrontend
2011-12-30 10:15:10.588 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2011-12-30 10:15:10.588 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2011-12-30 10:15:10.746 Using Frameless Window
2011-12-30 10:15:10.746 Using Full Screen Window
2011-12-30 10:15:11.202 Using the OpenGL painter
2011-12-30 10:15:11.355 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-12-30 10:15:11.355 OpenGL: OpenGL renderer: GeForce 9600 GT/PCI/SSE2/3DNOW!
2011-12-30 10:15:11.355 OpenGL: OpenGL version : 3.3.0 NVIDIA 290.10
2011-12-30 10:15:11.355 OpenGL: Max texture size: 8192 x 8192
2011-12-30 10:15:11.355 OpenGL: Max texture units: 4
2011-12-30 10:15:11.355 OpenGL: Direct rendering: Yes
2011-12-30 10:15:11.355 OpenGL: Initialised MythRenderOpenGL
2011-12-30 10:15:11.892 New DB connection, total: 2
2011-12-30 10:15:11.896 Connected to database 'mythconverg' at host: 192.168.1.100
2011-12-30 10:15:11.906 Current MythTV Schema Version (DBSchemaVer): 1264
2011-12-30 10:15:13.051 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-12-30 10:15:13.052 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-12-30 10:15:13.142 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-12-30 10:15:13.142 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-12-30 10:15:13.632 Pulse: PulseAudio suspend OK
2011-12-30 10:15:13.830 Pulse: PulseAudio resume OK
2011-12-30 10:15:14.409 Registering Internal as a media playback plugin.
2011-12-30 10:15:14.545 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-30 10:15:14.546 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-30 10:15:14.546 MediaMonitorUnix::AddDevice() - empty device path.
2011-12-30 10:15:14.546 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-12-30 10:15:14.547 Loading en_us translation for module mythgallery
2011-12-30 10:15:14.670 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-12-30 10:15:14.820 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-12-30 10:15:14.843 Loading en_us translation for module mythmusic
2011-12-30 10:15:14.902 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-12-30 10:15:14.978 Loading en_us translation for module mythvideo
2011-12-30 10:15:15.019 Loading en_us translation for module mythweather
2011-12-30 10:15:15.024 NetworkControl: Listening for remote connections on port 6546
2011-12-30 10:15:15.318 Found mainmenu.xml for theme 'Mythbuntu'
2011-12-30 10:15:15.568 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2011-12-30 10:15:15.570 Using protocol version 63
2011-12-30 10:15:32.371 TV: Attempting to change from None to WatchingPreRecorded
2011-12-30 10:15:32.742 Pulse: PulseAudio suspend OK
2011-12-30 10:15:33.369 AFD: Opened codec 0xbb44240, id(MPEG2VIDEO) type(Video)
2011-12-30 10:15:33.370 AFD: codec AC3 has 6 channels
2011-12-30 10:15:33.370 AFD: Opened codec 0xc0bf0b0, id(AC3) type(Audio)
2011-12-30 10:15:33.547 Pulse: PulseAudio resume OK
2011-12-30 10:15:33.747 Pulse: PulseAudio suspend OK
2011-12-30 10:15:33.808 AO: Opening audio device 'dmix:CARD=NVidia,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2011-12-30 10:15:33.859 ALSA, Error: Setting hardware audio buffer size to 6016
2011-12-30 10:15:33.859 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-12-30 10:15:33.859 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-12-30 10:15:33.859 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-12-30 10:15:33.953 AudioPlayer: Enabling Audio
2011-12-30 10:15:34.044 Clearing OpenGL painter cache.
2011-12-30 10:15:34.150 VDPAU: Created 2 output surfaces.
2011-12-30 10:15:34.150 VDPAU: Version 1
2011-12-30 10:15:34.150 VDPAU: Information NVIDIA VDPAU Driver Shared Library  290.10  Wed Nov 16 19:53:31 PST 2011
2011-12-30 10:15:34.150 VDPAU: Created VDPAU render device 1920x1080
2011-12-30 10:15:34.605 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-12-30 10:15:34.659 Player(0): Video timing method: USleep with busy wait
2011-12-30 10:15:34.664 TV: Changing from None to WatchingPreRecorded
2011-12-30 10:15:34.788 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-12-30 10:37:51.666 Received a remote 'Clear Cache' request
2011-12-30 10:45:29.085 [ac3 @ 0x1910b40]incomplete frame
2011-12-30 10:45:29.329 TV: Attempting to change from WatchingPreRecorded to None
2011-12-30 10:45:29.335 VDPAU Painter: Clearing VDPAU painter cache.
2011-12-30 10:45:29.335 MythPainter: 2 images not yet de-allocated.
2011-12-30 10:45:29.573 Pulse: PulseAudio resume OK
2011-12-30 10:45:29.579 TV: Changing from WatchingPreRecorded to None
2011-12-30 10:45:29.580 TV: Attempting to change from None to None
```

---

