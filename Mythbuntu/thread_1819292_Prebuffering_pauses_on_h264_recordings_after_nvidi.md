---
title: "Prebuffering pauses on h264 recordings after nvidia driver update"
date: 2011-08-05
forum: Mythbuntu
---

### Post by golbez_88rule on 2011-08-05
I am running mythbuntu 10.04 (mythfrontend) on an Acer Aspire Revo 1600, and up until last week, my recordings and videos played fine without any problem.  Back in 2010 I experienced pre-buffering pauses in my high definition recordings, and I resolved that by adding the ubuntu-x-swat ppa ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)) and upgrading the Nvidia proprietary driver (see details in my post: [http://ubuntuforums.org/showthread.php?t=1524257](http://ubuntuforums.org/showthread.php?t=1524257)) Last week, I performed what I thought were pretty innocent system updates, and one of them included an upgrade to the Nvidia driver. Here is an excerpt from the Synaptic update history:

```
nvidia-185-kernel-source (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-185-modaliases (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-current (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-current-modaliases (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-glx-185 (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-settings (260.19.06-0ubuntu1~lucid~xup) to 275.19-0ubuntu1~lucid~xup1
```

After this update, playback of any high-definition videos were met with constant stuttering of audio and choppy video. Ironically, there was another update to the Nvidia driver available a couple of days later.  Since an upgrade of the driver fixed the issue last year, I tried this update as well:
```
nvidia-185-kernel-source (275.19-0ubuntu1~lucid~xup1) to 280.13-0ubuntu1~lucid~xup1
nvidia-185-modaliases (275.19-0ubuntu1~lucid~xup1) to 280.13-0ubuntu1~lucid~xup1
nvidia-current (275.19-0ubuntu1~lucid~xup1) to 280.13-0ubuntu1~lucid~xup1
nvidia-current-modaliases (275.19-0ubuntu1~lucid~xup1) to 280.13-0ubuntu1~lucid~xup1
nvidia-glx-185 (275.19-0ubuntu1~lucid~xup1) to 280.13-0ubuntu1~lucid~xup1
nvidia-settings (275.19-0ubuntu1~lucid~xup1) to 280.13-0ubuntu1~lucid~xup1
```

After a reboot once the update was completed, I still experienced the same audio stuttering and choppy video.  Here is the mythfrontend log output during one of these playbacks:

```
eric@mythtvfront:~$ mythfrontend
2011-08-03 19:19:05.349 mythfrontend version: branches/release-0-23-fixes [s25362] www.mythtv.org
2011-08-03 19:19:05.351 Using runtime prefix = /usr
2011-08-03 19:19:05.351 Using configuration directory = /home/eric/.mythtv
2011-08-03 19:19:06.047 Empty LocalHostName.
2011-08-03 19:19:06.047 Using localhost value of mythtvfront
2011-08-03 19:19:06.048 Testing network connectivity to '192.168.1.2'
2011-08-03 19:19:06.098 New DB connection, total: 1
2011-08-03 19:19:06.305 Unable to connect to database!
2011-08-03 19:19:06.305 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'mythtvfront.local' (using password: YES)


2011-08-03 19:19:06.433 UPnPautoconf() - Found one UPnP backend
2011-08-03 19:19:06.607 Testing network connectivity to '192.168.1.2'
2011-08-03 19:19:06.616 Closing DB connection named 'DBManager0'
2011-08-03 19:19:06.619 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-03 19:19:06.621 Closing DB connection named 'DBManager0'
2011-08-03 19:19:06.678 ScreenSaverX11Private: XScreenSaver support enabled
2011-08-03 19:19:06.678 ScreenSaverX11Private: Gnome screen saver support enabled
2011-08-03 19:19:06.681 DPMS is disabled.
2011-08-03 19:19:06.684 Primary screen: 0.
2011-08-03 19:19:06.686 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-03 19:19:06.689 Using screen 0, 1920x1080 at 0,0
2011-08-03 19:19:06.728 Desktop video mode: 1920x1080 60.0024 Hz
2011-08-03 19:19:06.794 MythUI Image Cache size set to 20971520 bytes
2011-08-03 19:19:06.849 AudioPulseUtil: Suspend Success
2011-08-03 19:19:06.850 Enabled verbose msgs:  important general
2011-08-03 19:19:06.869 Primary screen: 0.
2011-08-03 19:19:06.871 Using screen 0, 1920x1080 at 0,0
2011-08-03 19:19:06.872 Using theme base resolution of 1280x720
2011-08-03 19:19:06.899 LIRC: Successfully initialized '/dev/lircd' using '/home/eric/.mythtv/lircrc' config
2011-08-03 19:19:06.899 JoystickMenuThread Error: Joystick disabled - Failed to read /home/eric/.mythtv/joystickmenurc
2011-08-03 19:19:07.028 Using Frameless Window
2011-08-03 19:19:07.029 Using Full Screen Window
2011-08-03 19:19:07.930 Using the Qt painter
2011-08-03 19:19:08.299 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-08-03 19:19:08.345 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-08-03 19:19:08.377 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-08-03 19:19:08.377 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-08-03 19:19:08.394 Current MythTV Schema Version (DBSchemaVer): 1254
2011-08-03 19:19:09.771 Registering Internal as a media playback plugin.
2011-08-03 19:19:09.852 Cannot load language en_us for module mytharchive
2011-08-03 19:19:09.880 Cannot load language en_us for module mythbrowser
2011-08-03 19:19:09.888 Registering WebBrowser as a media playback plugin.
2011-08-03 19:19:09.888 Cannot load language en_us for module mythbrowser
2011-08-03 19:19:09.981 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-08-03 19:19:09.982 Cannot load language en_us for module mythgallery
2011-08-03 19:19:10.012 Cannot load language en_us for module mythmovies
2011-08-03 19:19:10.096 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-08-03 19:19:10.203 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-08-03 19:19:10.220 Cannot load language en_us for module mythmusic
2011-08-03 19:19:10.263 Cannot load language en_us for module mythnetvision
2011-08-03 19:19:10.300 Cannot load language en_us for module mythnews
2011-08-03 19:19:10.346 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-08-03 19:19:10.418 Cannot load language en_us for module mythvideo
2011-08-03 19:19:10.461 Cannot load language en_us for module mythweather
2011-08-03 19:19:10.466 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-08-03 19:19:10.654 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-08-03 19:19:10.661 Found mainmenu.xml for theme 'Mythbuntu'
2011-08-03 19:19:12.935 MythContext: Connecting to backend server: 192.168.1.2:6543 (try 1 of 1)
2011-08-03 19:19:12.944 Using protocol version 56
2011-08-03 19:19:14.222 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2011-08-03 19:19:15.597 New DB connection, total: 2
2011-08-03 19:19:15.599 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-03 19:19:15.602 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2011-08-03 19:19:19.796 TV: Attempting to change from None to WatchingPreRecorded
2011-08-03 19:19:21.005 AFD: Opened codec 0xa8ad150, id(H264) type(Video)
2011-08-03 19:19:21.006 AFD: codec AAC has 2 channels
2011-08-03 19:19:21.006 AFD: Opened codec 0xa8ac450, id(AAC) type(Audio)
2011-08-03 19:19:21.046 Opening audio device '/dev/dsp1'. ch 2(2) sr 48000 (reenc 0)
2011-08-03 19:19:21.046 Opening OSS audio device '/dev/dsp1'.
2011-08-03 19:19:21.494 VDPAU: Created 2 output surfaces.
2011-08-03 19:19:21.494 VDPAU: Version 1
2011-08-03 19:19:21.494 VDPAU: Information NVIDIA VDPAU Driver Shared Library  280.13  Wed Jul 27 17:18:15 PDT 2011
2011-08-03 19:19:21.494 VDPAU: Created VDPAU render device 1920x1080
2011-08-03 19:19:22.189 NVP(0): Forcing decode extra audio option on (Video method requires it).
2011-08-03 19:19:22.196 OSD Theme Dimensions W: 1280 H: 720
2011-08-03 19:19:23.068 TV: Changing from None to WatchingPreRecorded
2011-08-03 19:19:23.070 The realtime priority setting is not enabled.
2011-08-03 19:19:23.081 OpenGLVideoSync()
2011-08-03 19:19:23.535 Video timing method: SGI OpenGL
2011-08-03 19:19:23.573 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-08-03 19:19:24.849 NVP(0): prebuffering pause
2011-08-03 19:19:24.890 NVP(0): prebuffering pause
2011-08-03 19:19:24.966 NVP(0): prebuffering pause
2011-08-03 19:19:25.012 NVP(0): prebuffering pause
2011-08-03 19:19:25.050 NVP(0): prebuffering pause
2011-08-03 19:19:25.133 NVP(0): prebuffering pause
2011-08-03 19:19:25.216 NVP(0): prebuffering pause
2011-08-03 19:19:25.299 NVP(0): prebuffering pause
2011-08-03 19:19:25.384 NVP(0): prebuffering pause
2011-08-03 19:19:25.466 NVP(0): prebuffering pause
2011-08-03 19:19:25.512 NVP(0): prebuffering pause
2011-08-03 19:19:25.560 NVP(0): prebuffering pause
2011-08-03 19:19:25.633 NVP(0): prebuffering pause
2011-08-03 19:19:25.716 NVP(0): prebuffering pause
2011-08-03 19:19:25.800 NVP(0): prebuffering pause
2011-08-03 19:19:25.849 NVP(0): prebuffering pause
2011-08-03 19:19:25.883 NVP(0): prebuffering pause
2011-08-03 19:19:25.966 NVP(0): prebuffering pause
2011-08-03 19:19:26.050 NVP(0): prebuffering pause
2011-08-03 19:19:26.133 NVP(0): prebuffering pause
2011-08-03 19:19:26.177 NVP(0): prebuffering pause
2011-08-03 19:19:26.224 NVP(0): prebuffering pause
2011-08-03 19:19:26.302 NVP(0): prebuffering pause
2011-08-03 19:19:26.345 NVP(0): prebuffering pause
2011-08-03 19:19:26.392 NVP(0): prebuffering pause
2011-08-03 19:19:26.466 NVP(0): prebuffering pause
2011-08-03 19:19:26.516 NVP(0): prebuffering pause
2011-08-03 19:19:26.600 NVP(0): prebuffering pause
2011-08-03 19:19:26.633 NVP(0): prebuffering pause
2011-08-03 19:19:26.723 NVP(0): prebuffering pause
2011-08-03 19:19:26.800 NVP(0): prebuffering pause
2011-08-03 19:19:26.900 NVP(0): prebuffering pause
2011-08-03 19:19:26.974 NVP(0): prebuffering pause
2011-08-03 19:19:27.057 NVP(0): prebuffering pause
2011-08-03 19:19:27.133 NVP(0): prebuffering pause
2011-08-03 19:19:27.200 NVP(0): prebuffering pause
2011-08-03 19:19:27.283 NVP(0): prebuffering pause
2011-08-03 19:19:27.366 NVP(0): prebuffering pause
2011-08-03 19:19:27.450 NVP(0): prebuffering pause
2011-08-03 19:19:27.533 NVP(0): prebuffering pause
2011-08-03 19:19:27.616 NVP(0): prebuffering pause
2011-08-03 19:19:27.700 NVP(0): prebuffering pause
2011-08-03 19:19:27.783 NVP(0): prebuffering pause
2011-08-03 19:19:27.866 NVP(0): prebuffering pause
2011-08-03 19:19:27.950 NVP(0): prebuffering pause
2011-08-03 19:19:28.033 NVP(0): prebuffering pause
2011-08-03 19:19:28.116 NVP(0): prebuffering pause
2011-08-03 19:19:28.207 NVP(0): prebuffering pause
2011-08-03 19:19:28.283 NVP(0): prebuffering pause
2011-08-03 19:19:28.366 NVP(0): prebuffering pause
2011-08-03 19:19:28.450 NVP(0): prebuffering pause
2011-08-03 19:19:28.533 NVP(0): prebuffering pause
2011-08-03 19:19:28.579 NVP(0): prebuffering pause
2011-08-03 19:19:28.608 NVP(0): prebuffering pause
2011-08-03 19:19:28.666 NVP(0): prebuffering pause
2011-08-03 19:19:28.706 NVP(0): prebuffering pause
2011-08-03 19:19:28.783 NVP(0): prebuffering pause
2011-08-03 19:19:28.866 NVP(0): prebuffering pause
2011-08-03 19:19:28.950 NVP(0): prebuffering pause
2011-08-03 19:19:29.033 NVP(0): prebuffering pause
2011-08-03 19:19:29.116 NVP(0): prebuffering pause
2011-08-03 19:19:29.207 NVP(0): prebuffering pause
2011-08-03 19:19:29.283 NVP(0): prebuffering pause
2011-08-03 19:19:29.332 NVP(0): prebuffering pause
2011-08-03 19:19:29.366 NVP(0): prebuffering pause
2011-08-03 19:19:29.450 NVP(0): prebuffering pause
2011-08-03 19:19:29.533 NVP(0): prebuffering pause
2011-08-03 19:19:29.617 NVP(0): prebuffering pause
2011-08-03 19:19:29.700 NVP(0): prebuffering pause
2011-08-03 19:19:29.783 NVP(0): prebuffering pause
2011-08-03 19:19:29.866 NVP(0): prebuffering pause
2011-08-03 19:19:29.950 NVP(0): prebuffering pause
2011-08-03 19:19:30.033 NVP(0): prebuffering pause
2011-08-03 19:19:30.117 NVP(0): prebuffering pause
2011-08-03 19:19:30.217 NVP(0): prebuffering pause
2011-08-03 19:19:30.260 NVP(0): prebuffering pause
2011-08-03 19:19:30.294 NVP(0): prebuffering pause
2011-08-03 19:19:30.349 NVP(0): prebuffering pause
2011-08-03 19:19:30.384 NVP(0): prebuffering pause
2011-08-03 19:19:30.466 NVP(0): prebuffering pause
2011-08-03 19:19:30.550 NVP(0): prebuffering pause
2011-08-03 19:19:30.633 NVP(0): prebuffering pause
2011-08-03 19:19:30.677 NVP(0): prebuffering pause
2011-08-03 19:19:30.725 NVP(0): prebuffering pause
2011-08-03 19:19:30.800 NVP(0): prebuffering pause
2011-08-03 19:19:30.849 NVP(0): prebuffering pause
2011-08-03 19:19:30.886 NVP(0): prebuffering pause
2011-08-03 19:19:30.966 NVP(0): prebuffering pause
2011-08-03 19:19:31.050 NVP(0): prebuffering pause
2011-08-03 19:19:31.133 NVP(0): prebuffering pause
2011-08-03 19:19:31.217 NVP(0): prebuffering pause
2011-08-03 19:19:31.333 NVP(0): prebuffering pause
2011-08-03 19:19:31.369 NVP(0): prebuffering pause
2011-08-03 19:19:31.414 NVP(0): prebuffering pause
2011-08-03 19:19:31.443 NVP(0): prebuffering pause
2011-08-03 19:19:31.495 NVP(0): prebuffering pause
2011-08-03 19:19:31.535 NVP(0): prebuffering pause
2011-08-03 19:19:31.617 NVP(0): prebuffering pause
2011-08-03 19:19:31.700 NVP(0): prebuffering pause
2011-08-03 19:19:31.783 NVP(0): prebuffering pause
2011-08-03 19:19:31.849 NVP(0): prebuffering pause
2011-08-03 19:19:31.887 NVP(0): prebuffering pause
2011-08-03 19:19:31.966 NVP(0): prebuffering pause
2011-08-03 19:19:32.016 NVP(0): prebuffering pause
2011-08-03 19:19:32.050 NVP(0): prebuffering pause
2011-08-03 19:19:32.133 NVP(0): prebuffering pause
2011-08-03 19:19:32.216 NVP(0): prebuffering pause
2011-08-03 19:19:32.300 NVP(0): prebuffering pause
2011-08-03 19:19:32.383 NVP(0): prebuffering pause
2011-08-03 19:19:32.466 NVP(0): prebuffering pause
2011-08-03 19:19:32.566 NVP(0): prebuffering pause
2011-08-03 19:19:32.640 NVP(0): prebuffering pause
2011-08-03 19:19:32.724 NVP(0): prebuffering pause
2011-08-03 19:19:32.783 NVP(0): prebuffering pause
2011-08-03 19:19:32.810 NVP(0): prebuffering pause
2011-08-03 19:19:32.862 NVP(0): prebuffering pause
2011-08-03 19:19:32.909 NVP(0): prebuffering pause
2011-08-03 19:19:32.983 NVP(0): prebuffering pause
2011-08-03 19:19:33.033 NVP(0): prebuffering pause
2011-08-03 19:19:33.066 NVP(0): prebuffering pause
2011-08-03 19:19:33.150 NVP(0): prebuffering pause
2011-08-03 19:19:33.250 NVP(0): prebuffering pause
2011-08-03 19:19:33.324 NVP(0): prebuffering pause
2011-08-03 19:19:33.383 NVP(0): prebuffering pause
2011-08-03 19:19:33.424 NVP(0): prebuffering pause
2011-08-03 19:19:33.500 NVP(0): prebuffering pause
2011-08-03 19:19:33.549 NVP(0): prebuffering pause
2011-08-03 19:19:33.583 NVP(0): prebuffering pause
2011-08-03 19:19:33.666 NVP(0): prebuffering pause
2011-08-03 19:19:33.766 NVP(0): prebuffering pause
2011-08-03 19:19:33.983 NVP(0): prebuffering pause
2011-08-03 19:19:34.066 NVP(0): prebuffering pause
2011-08-03 19:19:34.116 NVP(0): prebuffering pause
2011-08-03 19:19:34.141 NVP(0): prebuffering pause
2011-08-03 19:19:34.233 NVP(0): prebuffering pause
2011-08-03 19:19:34.317 NVP(0): prebuffering pause
2011-08-03 19:19:34.400 NVP(0): prebuffering pause
2011-08-03 19:19:34.483 NVP(0): prebuffering pause
2011-08-03 19:19:34.529 NVP(0): prebuffering pause
2011-08-03 19:19:34.567 NVP(0): prebuffering pause
2011-08-03 19:19:34.650 NVP(0): prebuffering pause
2011-08-03 19:19:34.699 NVP(0): prebuffering pause
2011-08-03 19:19:34.733 NVP(0): prebuffering pause
2011-08-03 19:19:34.817 NVP(0): prebuffering pause
2011-08-03 19:19:34.862 NVP(0): prebuffering pause
2011-08-03 19:19:34.910 NVP(0): prebuffering pause
2011-08-03 19:19:34.986 NVP(0): prebuffering pause
2011-08-03 19:19:35.067 NVP(0): prebuffering pause
2011-08-03 19:19:35.150 NVP(0): prebuffering pause
2011-08-03 19:19:35.234 NVP(0): prebuffering pause
2011-08-03 19:19:35.317 NVP(0): prebuffering pause
2011-08-03 19:19:35.361 NVP(0): prebuffering pause
2011-08-03 19:19:35.408 NVP(0): prebuffering pause
2011-08-03 19:19:35.483 NVP(0): prebuffering pause
2011-08-03 19:19:35.567 NVP(0): prebuffering pause
2011-08-03 19:19:35.650 NVP(0): prebuffering pause
2011-08-03 19:19:35.734 NVP(0): prebuffering pause
2011-08-03 19:19:35.817 NVP(0): prebuffering pause
2011-08-03 19:19:35.883 NVP(0): prebuffering pause
2011-08-03 19:19:35.967 NVP(0): prebuffering pause
2011-08-03 19:19:36.050 NVP(0): prebuffering pause
2011-08-03 19:19:36.133 NVP(0): prebuffering pause
2011-08-03 19:19:36.217 NVP(0): prebuffering pause
2011-08-03 19:19:36.264 NVP(0): prebuffering pause
2011-08-03 19:19:36.292 NVP(0): prebuffering pause
2011-08-03 19:19:36.390 NVP(0): prebuffering pause
2011-08-03 19:19:36.428 NVP(0): prebuffering pause
2011-08-03 19:19:36.460 NVP(0): prebuffering pause
2011-08-03 19:19:36.516 NVP(0): prebuffering pause
2011-08-03 19:19:36.550 NVP(0): prebuffering pause
2011-08-03 19:19:36.623 NVP(0): prebuffering pause
2011-08-03 19:19:36.683 NVP(0): prebuffering pause
2011-08-03 19:19:36.723 NVP(0): prebuffering pause
2011-08-03 19:19:36.766 NVP(0): prebuffering pause
2011-08-03 19:19:36.792 NVP(0): prebuffering pause
2011-08-03 19:19:36.849 NVP(0): prebuffering pause
2011-08-03 19:19:36.893 NVP(0): prebuffering pause
2011-08-03 19:19:36.967 NVP(0): prebuffering pause
2011-08-03 19:19:37.016 NVP(0): prebuffering pause
2011-08-03 19:19:37.050 NVP(0): prebuffering pause
2011-08-03 19:19:37.133 NVP(0): prebuffering pause
2011-08-03 19:19:37.183 NVP(0): prebuffering pause
2011-08-03 19:19:37.221 NVP(0): prebuffering pause
2011-08-03 19:19:37.264 NVP(0): prebuffering pause
2011-08-03 19:19:37.294 NVP(0): prebuffering pause
2011-08-03 19:19:37.349 NVP(0): prebuffering pause
2011-08-03 19:19:37.384 NVP(0): prebuffering pause
2011-08-03 19:19:37.456 NVP(0): prebuffering pause
2011-08-03 19:19:37.516 NVP(0): prebuffering pause
2011-08-03 19:19:37.557 NVP(0): prebuffering pause
2011-08-03 19:19:37.633 NVP(0): prebuffering pause
2011-08-03 19:19:37.677 NVP(0): prebuffering pause
2011-08-03 19:19:37.725 NVP(0): prebuffering pause
2011-08-03 19:19:37.790 NVP(0): prebuffering pause
2011-08-03 19:19:37.849 NVP(0): prebuffering pause
2011-08-03 19:19:37.887 NVP(0): prebuffering pause
2011-08-03 19:19:37.957 NVP(0): prebuffering pause
2011-08-03 19:19:38.016 NVP(0): prebuffering pause
2011-08-03 19:19:38.057 NVP(0): prebuffering pause
2011-08-03 19:19:38.123 NVP(0): prebuffering pause
2011-08-03 19:19:38.183 NVP(0): prebuffering pause
2011-08-03 19:19:38.224 NVP(0): prebuffering pause
2011-08-03 19:19:38.300 NVP(0): prebuffering pause
2011-08-03 19:19:38.384 NVP(0): prebuffering pause
2011-08-03 19:19:38.433 NVP(0): prebuffering pause
2011-08-03 19:19:38.458 NVP(0): prebuffering pause
2011-08-03 19:19:38.516 NVP(0): prebuffering pause
2011-08-03 19:19:38.556 NVP(0): prebuffering pause
2011-08-03 19:19:38.623 NVP(0): prebuffering pause
2011-08-03 19:19:38.683 NVP(0): prebuffering pause
2011-08-03 19:19:38.723 NVP(0): prebuffering pause
2011-08-03 19:19:38.766 NVP(0): prebuffering pause
2011-08-03 19:19:38.793 NVP(0): prebuffering pause
2011-08-03 19:19:38.847 NVP(0): prebuffering pause
2011-08-03 19:19:38.885 NVP(0): prebuffering pause
2011-08-03 19:19:38.967 NVP(0): prebuffering pause
2011-08-03 19:19:39.057 NVP(0): prebuffering pause
2011-08-03 19:19:39.167 NVP(0): prebuffering pause
2011-08-03 19:19:39.210 NVP(0): prebuffering pause
2011-08-03 19:19:39.285 NVP(0): prebuffering pause
2011-08-03 19:19:39.367 NVP(0): prebuffering pause
2011-08-03 19:19:39.483 NVP(0): prebuffering pause
2011-08-03 19:19:39.521 NVP(0): prebuffering pause
2011-08-03 19:19:39.564 NVP(0): prebuffering pause
2011-08-03 19:19:39.595 NVP(0): prebuffering pause
2011-08-03 19:19:39.683 NVP(0): prebuffering pause
2011-08-03 19:19:39.757 NVP(0): prebuffering pause
2011-08-03 19:19:39.840 NVP(0): prebuffering pause
2011-08-03 19:19:39.917 NVP(0): prebuffering pause
2011-08-03 19:19:39.961 NVP(0): prebuffering pause
2011-08-03 19:19:40.007 NVP(0): prebuffering pause
2011-08-03 19:19:40.049 NVP(0): prebuffering pause
2011-08-03 19:19:40.076 NVP(0): prebuffering pause
2011-08-03 19:19:40.167 NVP(0): prebuffering pause
2011-08-03 19:19:40.216 NVP(0): prebuffering pause
2011-08-03 19:19:40.240 NVP(0): prebuffering pause
2011-08-03 19:19:40.317 NVP(0): prebuffering pause
2011-08-03 19:19:40.400 NVP(0): prebuffering pause
2011-08-03 19:19:40.444 NVP(0): prebuffering pause
2011-08-03 19:19:40.489 NVP(0): prebuffering pause
2011-08-03 19:19:40.531 NVP(0): prebuffering pause
2011-08-03 19:19:40.561 NVP(0): prebuffering pause
2011-08-03 19:19:40.616 NVP(0): prebuffering pause
2011-08-03 19:19:40.650 NVP(0): prebuffering pause
2011-08-03 19:19:40.699 NVP(0): prebuffering pause
2011-08-03 19:19:40.725 NVP(0): prebuffering pause
2011-08-03 19:19:40.783 NVP(0): prebuffering pause
2011-08-03 19:19:40.824 NVP(0): prebuffering pause
2011-08-03 19:19:40.864 NVP(0): prebuffering pause
2011-08-03 19:19:40.891 NVP(0): prebuffering pause
2011-08-03 19:19:40.967 NVP(0): prebuffering pause
2011-08-03 19:19:41.011 NVP(0): prebuffering pause
2011-08-03 19:19:41.040 NVP(0): prebuffering pause
2011-08-03 19:19:41.124 NVP(0): prebuffering pause
2011-08-03 19:19:41.200 NVP(0): prebuffering pause
2011-08-03 19:19:41.249 NVP(0): prebuffering pause
2011-08-03 19:19:41.288 NVP(0): prebuffering pause
2011-08-03 19:19:41.330 NVP(0): prebuffering pause
2011-08-03 19:19:41.362 NVP(0): prebuffering pause
2011-08-03 19:19:41.440 NVP(0): prebuffering pause
2011-08-03 19:19:41.517 NVP(0): prebuffering pause
2011-08-03 19:19:41.600 NVP(0): prebuffering pause
2011-08-03 19:19:41.683 NVP(0): prebuffering pause
2011-08-03 19:19:41.727 NVP(0): prebuffering pause
2011-08-03 19:19:41.773 NVP(0): prebuffering pause
2011-08-03 19:19:41.815 NVP(0): prebuffering pause
2011-08-03 19:19:41.843 NVP(0): prebuffering pause
2011-08-03 19:19:41.899 NVP(0): prebuffering pause
2011-08-03 19:19:41.939 NVP(0): prebuffering pause
2011-08-03 19:19:41.982 NVP(0): prebuffering pause
2011-08-03 19:19:42.013 NVP(0): prebuffering pause
2011-08-03 19:19:42.061 NVP(0): prebuffering pause
2011-08-03 19:19:42.140 NVP(0): prebuffering pause
2011-08-03 19:19:42.217 NVP(0): prebuffering pause
2011-08-03 19:19:42.263 NVP(0): prebuffering pause
2011-08-03 19:19:42.300 NVP(0): prebuffering pause
2011-08-03 19:19:42.383 NVP(0): prebuffering pause
2011-08-03 19:19:42.457 NVP(0): prebuffering pause
2011-08-03 19:19:42.524 NVP(0): prebuffering pause
2011-08-03 19:19:42.600 NVP(0): prebuffering pause
2011-08-03 19:19:42.667 NVP(0): prebuffering pause
2011-08-03 19:19:42.751 NVP(0): prebuffering pause
2011-08-03 19:19:42.834 NVP(0): prebuffering pause
2011-08-03 19:19:42.900 NVP(0): prebuffering pause
2011-08-03 19:19:42.984 NVP(0): prebuffering pause
2011-08-03 19:19:43.057 NVP(0): prebuffering pause
2011-08-03 19:19:43.134 NVP(0): prebuffering pause
2011-08-03 19:19:43.178 NVP(0): prebuffering pause
2011-08-03 19:19:43.220 NVP(0): prebuffering pause
2011-08-03 19:19:43.284 NVP(0): prebuffering pause
2011-08-03 19:19:43.367 NVP(0): prebuffering pause
2011-08-03 19:19:43.434 NVP(0): prebuffering pause
2011-08-03 19:19:43.517 NVP(0): prebuffering pause
2011-08-03 19:19:43.584 NVP(0): prebuffering pause
2011-08-03 19:19:43.667 NVP(0): prebuffering pause
2011-08-03 19:19:43.740 NVP(0): prebuffering pause
2011-08-03 19:19:43.850 NVP(0): prebuffering pause
2011-08-03 19:19:43.891 NVP(0): prebuffering pause
2011-08-03 19:19:43.970 NVP(0): prebuffering pause
2011-08-03 19:19:44.034 NVP(0): prebuffering pause
2011-08-03 19:19:44.150 NVP(0): prebuffering pause
2011-08-03 19:19:44.190 NVP(0): prebuffering pause
2011-08-03 19:19:44.232 NVP(0): prebuffering pause
2011-08-03 19:19:44.275 NVP(0): prebuffering pause
2011-08-03 19:19:44.341 NVP(0): prebuffering pause
2011-08-03 19:19:44.567 NVP(0): prebuffering pause
2011-08-03 19:19:44.634 NVP(0): prebuffering pause
2011-08-03 19:19:44.679 NVP(0): prebuffering pause
2011-08-03 19:19:44.719 NVP(0): prebuffering pause
2011-08-03 19:19:44.784 NVP(0): prebuffering pause
2011-08-03 19:19:44.867 NVP(0): prebuffering pause
2011-08-03 19:19:44.934 NVP(0): prebuffering pause
2011-08-03 19:19:45.017 NVP(0): prebuffering pause
2011-08-03 19:19:45.084 NVP(0): prebuffering pause
2011-08-03 19:19:45.167 NVP(0): prebuffering pause
2011-08-03 19:19:45.250 NVP(0): prebuffering pause
2011-08-03 19:19:45.324 NVP(0): prebuffering pause
2011-08-03 19:19:45.400 NVP(0): prebuffering pause
2011-08-03 19:19:45.444 NVP(0): prebuffering pause
2011-08-03 19:19:45.485 NVP(0): prebuffering pause
2011-08-03 19:19:45.550 NVP(0): prebuffering pause
2011-08-03 19:19:45.634 NVP(0): prebuffering pause
2011-08-03 19:19:45.700 NVP(0): prebuffering pause
2011-08-03 19:19:45.784 NVP(0): prebuffering pause
2011-08-03 19:19:45.867 NVP(0): prebuffering pause
2011-08-03 19:19:45.941 NVP(0): prebuffering pause
2011-08-03 19:19:46.017 NVP(0): prebuffering pause
2011-08-03 19:19:46.101 NVP(0): prebuffering pause
2011-08-03 19:19:46.167 NVP(0): prebuffering pause
2011-08-03 19:19:46.252 NVP(0): prebuffering pause
2011-08-03 19:19:46.277 TV: Attempting to change from WatchingPreRecorded to None
2011-08-03 19:19:46.304 TV: Changing from WatchingPreRecorded to None
2011-08-03 19:19:46.383 ~OpenGLVideoSync() -- closing opengl vsync
2011-08-03 19:19:51.205 AudioPulseUtil: Resume Success
2011-08-03 19:19:51.206 Deleting UPnP client...
eric@mythtvfront:~$
```

These prebuffering pauses happen with all h264 files, whether they are high-definition shows recorded from cable, or home videos from my high-definition camera.  However, all standard definition recordings, as well as videos downloaded via Mirobridge play back fine without any stuttering.  Interestingly, even playback of a bluray rip of the Dark Night (a 10 GM MKV file) played back fine without any prebuffering pauses.  Here is the mythfrontend log for that particular playback:

```
eric@mythtvfront:~$ mythfrontend 
2011-08-05 20:31:39.368 mythfrontend version: branches/release-0-23-fixes [s25362] www.mythtv.org
2011-08-05 20:31:39.370 Using runtime prefix = /usr
2011-08-05 20:31:39.370 Using configuration directory = /home/eric/.mythtv
2011-08-05 20:31:40.066 Empty LocalHostName.
2011-08-05 20:31:40.066 Using localhost value of mythtvfront
2011-08-05 20:31:40.067 Testing network connectivity to '192.168.1.2'
2011-08-05 20:31:40.117 New DB connection, total: 1
2011-08-05 20:31:40.120 Unable to connect to database!
2011-08-05 20:31:40.120 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'mythtvfront.local' (using password: YES)


2011-08-05 20:31:40.297 UPnPautoconf() - Found one UPnP backend
2011-08-05 20:31:40.467 Testing network connectivity to '192.168.1.2'
2011-08-05 20:31:40.476 Closing DB connection named 'DBManager0'
2011-08-05 20:31:40.479 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-05 20:31:40.481 Closing DB connection named 'DBManager0'
2011-08-05 20:31:40.520 ScreenSaverX11Private: XScreenSaver support enabled
2011-08-05 20:31:40.521 ScreenSaverX11Private: Gnome screen saver support enabled
2011-08-05 20:31:40.523 DPMS is disabled.
2011-08-05 20:31:40.528 Primary screen: 0.
2011-08-05 20:31:40.530 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-05 20:31:40.536 Using screen 0, 1920x1080 at 0,0
2011-08-05 20:31:40.573 Desktop video mode: 1920x1080 60.0024 Hz
2011-08-05 20:31:40.639 MythUI Image Cache size set to 20971520 bytes
2011-08-05 20:31:40.693 AudioPulseUtil: Suspend Success
2011-08-05 20:31:40.694 Enabled verbose msgs:  important general
2011-08-05 20:31:40.708 Primary screen: 0.
2011-08-05 20:31:40.710 Using screen 0, 1920x1080 at 0,0
2011-08-05 20:31:40.712 Using theme base resolution of 1280x720
2011-08-05 20:31:40.734 LIRC: Successfully initialized '/dev/lircd' using '/home/eric/.mythtv/lircrc' config
2011-08-05 20:31:40.735 JoystickMenuThread Error: Joystick disabled - Failed to read /home/eric/.mythtv/joystickmenurc
2011-08-05 20:31:40.832 Using Frameless Window
2011-08-05 20:31:40.832 Using Full Screen Window
2011-08-05 20:31:41.716 Using the Qt painter
2011-08-05 20:31:42.048 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-08-05 20:31:42.081 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-08-05 20:31:42.116 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-08-05 20:31:42.116 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-08-05 20:31:42.126 New DB connection, total: 2
2011-08-05 20:31:42.127 New DB connection, total: 3
2011-08-05 20:31:42.128 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-05 20:31:42.128 Connected to database 'mythconverg' at host: 192.168.1.2
2011-08-05 20:31:42.129 Current MythTV Schema Version (DBSchemaVer): 1254
2011-08-05 20:31:43.248 Registering Internal as a media playback plugin.
2011-08-05 20:31:43.340 Cannot load language en_us for module mytharchive
2011-08-05 20:31:43.369 Cannot load language en_us for module mythbrowser
2011-08-05 20:31:43.378 Registering WebBrowser as a media playback plugin.
2011-08-05 20:31:43.378 Cannot load language en_us for module mythbrowser
2011-08-05 20:31:43.469 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-08-05 20:31:43.470 Cannot load language en_us for module mythgallery
2011-08-05 20:31:43.501 Cannot load language en_us for module mythmovies
2011-08-05 20:31:43.587 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-08-05 20:31:43.697 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-08-05 20:31:43.713 Cannot load language en_us for module mythmusic
2011-08-05 20:31:43.758 Cannot load language en_us for module mythnetvision
2011-08-05 20:31:43.796 Cannot load language en_us for module mythnews
2011-08-05 20:31:43.844 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-08-05 20:31:43.920 Cannot load language en_us for module mythvideo
2011-08-05 20:31:43.964 Cannot load language en_us for module mythweather
2011-08-05 20:31:43.969 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-08-05 20:31:44.157 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-08-05 20:31:44.163 Found mainmenu.xml for theme 'Mythbuntu'
2011-08-05 20:31:46.384 MythContext: Connecting to backend server: 192.168.1.2:6543 (try 1 of 1)
2011-08-05 20:31:46.386 Using protocol version 56
2011-08-05 20:31:46.738 Warning! Time difference between the master backend and this system is 28 seconds.
2011-08-05 20:31:48.634 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2011-08-05 20:31:51.292 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2011-08-05 20:32:03.134 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2011-08-05 20:32:05.946 TV: Attempting to change from None to WatchingVideo
2011-08-05 20:32:07.066 AFD: Opened codec 0xadfb3c70, id(H264) type(Video)
2011-08-05 20:32:07.067 AFD: codec AC3 has 6 channels
2011-08-05 20:32:07.068 AFD: Opened codec 0xadfb4010, id(AC3) type(Audio)
2011-08-05 20:32:07.068 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2011-08-05 20:32:07.107 Opening audio device '/dev/dsp1'. ch 2(6) sr 48000 (reenc 1)
2011-08-05 20:32:07.107 Opening OSS audio device '/dev/dsp1'.
2011-08-05 20:32:07.152 Opening audio device '/dev/dsp1'. ch 2(6) sr 48000 (reenc 1)
2011-08-05 20:32:07.152 Opening OSS audio device '/dev/dsp1'.
2011-08-05 20:32:07.200 Opening audio device '/dev/dsp1'. ch 2(6) sr 48000 (reenc 1)
2011-08-05 20:32:07.200 Opening OSS audio device '/dev/dsp1'.
2011-08-05 20:32:07.387 VDPAU: Created 2 output surfaces.
2011-08-05 20:32:07.387 VDPAU: Version 1
2011-08-05 20:32:07.387 VDPAU: Information NVIDIA VDPAU Driver Shared Library  280.13  Wed Jul 27 17:18:15 PDT 2011
2011-08-05 20:32:07.387 VDPAU: Created VDPAU render device 1920x1080
2011-08-05 20:32:08.018 NVP(0): Forcing decode extra audio option on (Video method requires it).
2011-08-05 20:32:08.022 OSD Theme Dimensions W: 1280 H: 720
2011-08-05 20:32:08.383 TV: Changing from None to WatchingVideo
2011-08-05 20:32:08.386 The realtime priority setting is not enabled.
2011-08-05 20:32:08.398 OpenGLVideoSync()
2011-08-05 20:32:08.929 Video timing method: SGI OpenGL
2011-08-05 20:32:08.953 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-08-05 20:35:56.810 TV: Attempting to change from WatchingVideo to None
2011-08-05 20:35:56.815 TV: Changing from WatchingVideo to None
2011-08-05 20:35:56.851 ~OpenGLVideoSync() -- closing opengl vsync
2011-08-05 20:36:04.524 AudioPulseUtil: Resume Success
2011-08-05 20:36:04.524 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```

Here is what I have tried so far to troubleshoot the issue, in addition to the steps listed in the Mythtv prebuffering troubleshooting page ([http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause):](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause):)
[LIST=1]
[*]All high definition recordings play back without any stuttering on my backend machine (it has an ATI Radeon 5770 and AMD Quad core processor with 4 GB memory).
[*]I tried to add an additional filter to the vdpau Slim playback profile: vdpaubuffersize=50.  This had no effect, in fact I tried many numbers and it had no effect.  
[*]I checked the CPU load during high-definition video playback.  The load topped at between 15-20%, which it has always been.
[/LIST]

The frontend is connected via gigabit ethernet, so I don't believe network connectivity is an issue. Here are the rest of the system updates I performed in addition to the nvidia driver update:

```
Commit Log for Sun Jul 31 14:24:31 2011


Upgraded the following packages:
apparmor (2.5-0ubuntu3) to 2.5.1-0ubuntu0.10.04.3
apparmor-utils (2.5-0ubuntu3) to 2.5.1-0ubuntu0.10.04.3
apt (0.7.25.3ubuntu9.3) to 0.7.25.3ubuntu9.6
apt-transport-https (0.7.25.3ubuntu9.3) to 0.7.25.3ubuntu9.6
apt-utils (0.7.25.3ubuntu9.3) to 0.7.25.3ubuntu9.6
apturl (0.4.1ubuntu4) to 0.4.1ubuntu4.1
apturl-common (0.4.1ubuntu4) to 0.4.1ubuntu4.1
at (3.1.11-1ubuntu5) to 3.1.11-1ubuntu5.1
avahi-autoipd (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
avahi-daemon (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
base-files (5.0.0ubuntu20.10.04.2) to 5.0.0ubuntu20.10.04.4
bind9-host (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
binutils (2.20.1-3ubuntu7) to 2.20.1-3ubuntu7.1
bsdutils (1:2.17.2-0ubuntu1) to 1:2.17.2-0ubuntu1.10.04.2
consolekit (0.4.1-3ubuntu1) to 0.4.1-3ubuntu2
coreutils (7.4-2ubuntu2) to 7.4-2ubuntu3
dbus (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.3
dbus-x11 (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.3
dhcp3-client (3.1.3-2ubuntu3) to 3.1.3-2ubuntu3.2
dhcp3-common (3.1.3-2ubuntu3) to 3.1.3-2ubuntu3.2
dkms (2.1.1.2-2fakesync1) to 2.1.1.2-2ubuntu1
dmsetup (2:1.02.39-1ubuntu4) to 2:1.02.39-1ubuntu4.1
dnsmasq-base (2.52-1) to 2.52-1ubuntu0.1
dnsutils (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
dpkg (1.15.5.6ubuntu4.3) to 1.15.5.6ubuntu4.5
e2fslibs (1.41.11-1ubuntu2) to 1.41.11-1ubuntu2.1
e2fsprogs (1.41.11-1ubuntu2) to 1.41.11-1ubuntu2.1
ethtool (6+20091202-1) to 6+20091202-1ubuntu1
evince (2.30.3-0ubuntu1.1) to 2.30.3-0ubuntu1.2
ffmpeg (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
fglrx-modaliases (2:8.771-0ubuntu0sarvatt~lucid) to 2:8.801-0ubuntu1~xup~lucid
firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) to 3.6.18+build2+nobinonly-0ubuntu0.10.04.2
firefox-branding (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) to 3.6.18+build2+nobinonly-0ubuntu0.10.04.2
firefox-gnome-support (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) to 3.6.18+build2+nobinonly-0ubuntu0.10.04.2
flashplugin-installer (10.1.85.3ubuntu0.10.04.1) to 10.3.181.34ubuntu0.10.04.1
fuse-utils (2.8.1-1.1ubuntu2) to 2.8.1-1.1ubuntu3.1
gdm (2.30.2.is.2.30.0-0ubuntu3) to 2.30.2.is.2.30.0-0ubuntu5.2
gnome-screensaver (2.30.0-0ubuntu2) to 2.30.0-0ubuntu2.1
gnome-system-tools (2.30.0-0ubuntu2) to 2.30.0-0ubuntu3
grub-common (1.98-1ubuntu7) to 1.98-1ubuntu12
grub-pc (1.98-1ubuntu7) to 1.98-1ubuntu12
ifupdown (0.6.8ubuntu29.1) to 0.6.8ubuntu29.2
imagemagick (7:6.5.7.8-1ubuntu1) to 7:6.5.7.8-1ubuntu1.1
initscripts (2.87dsf-4ubuntu17) to 2.87dsf-4ubuntu17.4
libapparmor-perl (2.5-0ubuntu3) to 2.5.1-0ubuntu0.10.04.3
libapparmor1 (2.5-0ubuntu3) to 2.5.1-0ubuntu0.10.04.3
libapr1 (1.3.8-1build1) to 1.3.8-1ubuntu0.3
libavahi-client3 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-common-data (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-common3 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-core6 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavahi-glib1 (0.6.25-1ubuntu6.1) to 0.6.25-1ubuntu6.2
libavcodec52 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavdevice52 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavfilter0 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavformat52 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libavutil49 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libbind9-60 (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
libblkid1 (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.2
libc-bin (2.11.1-0ubuntu7.2) to 2.11.1-0ubuntu7.8
libc-dev-bin (2.11.1-0ubuntu7.2) to 2.11.1-0ubuntu7.8
libc6 (2.11.1-0ubuntu7.2) to 2.11.1-0ubuntu7.8
libc6-dev (2.11.1-0ubuntu7.2) to 2.11.1-0ubuntu7.8
libc6-i686 (2.11.1-0ubuntu7.2) to 2.11.1-0ubuntu7.8
libck-connector0 (0.4.1-3ubuntu1) to 0.4.1-3ubuntu2
libcomerr2 (1.41.11-1ubuntu2) to 1.41.11-1ubuntu2.1
libcups2 (1.4.3-1ubuntu1.2) to 1.4.3-1ubuntu1.3
libcupsimage2 (1.4.3-1ubuntu1.2) to 1.4.3-1ubuntu1.3
libcurl3-gnutls (7.19.7-1ubuntu1) to 7.19.7-1ubuntu1.1
libdbus-1-3 (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.3
libdbus-glib-1-2 (0.84-1) to 0.84-1ubuntu0.2
libdevmapper1.02.1 (2:1.02.39-1ubuntu4) to 2:1.02.39-1ubuntu4.1
libdns64 (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
libevdocument2 (2.30.3-0ubuntu1.1) to 2.30.3-0ubuntu1.2
libevview2 (2.30.3-0ubuntu1.1) to 2.30.3-0ubuntu1.2
libfreetype6 (2.3.11-1ubuntu2.2) to 2.3.11-1ubuntu2.4
libfuse2 (2.8.1-1.1ubuntu2) to 2.8.1-1.1ubuntu3.1
libgksu2-0 (2.0.13~pre1-1ubuntu4) to 2.0.13~pre1-1ubuntu4.1
libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.2) to 1.8.1+dfsg-2ubuntu0.9
libgudev-1.0-0 (1:151-12.1) to 1:151-12.3
libimobiledevice0 (0.9.7-1ubuntu1) to 0.9.7-1ubuntu1.1
libisc60 (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
libisccc60 (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
libisccfg60 (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
libk5crypto3 (1.8.1+dfsg-2ubuntu0.2) to 1.8.1+dfsg-2ubuntu0.9
libkrb5-3 (1.8.1+dfsg-2ubuntu0.2) to 1.8.1+dfsg-2ubuntu0.9
libkrb5support0 (1.8.1+dfsg-2ubuntu0.2) to 1.8.1+dfsg-2ubuntu0.9
liblcms1 (1.18.dfsg-1ubuntu2) to 1.18.dfsg-1ubuntu2.10.04.1
libldap-2.4-2 (2.4.21-0ubuntu5.3) to 2.4.21-0ubuntu5.5
liblircclient0 (0.8.6-0ubuntu4.1) to 0.8.6-0ubuntu4.2
liblwres60 (1:9.7.0.dfsg.P1-1) to 1:9.7.0.dfsg.P1-1ubuntu0.3
libmagickcore2 (7:6.5.7.8-1ubuntu1) to 7:6.5.7.8-1ubuntu1.1
libmagickcore2-extra (7:6.5.7.8-1ubuntu1) to 7:6.5.7.8-1ubuntu1.1
libmagickwand2 (7:6.5.7.8-1ubuntu1) to 7:6.5.7.8-1ubuntu1.1
libmodplug0c2 (1:0.8.7-1build1) to 1:0.8.7-1ubuntu0.2
libmysqlclient16 (5.1.41-3ubuntu12.6) to 5.1.41-3ubuntu12.10
libnm-glib2 (0.8-0ubuntu3) to 0.8-0ubuntu3.2
libnm-util1 (0.8-0ubuntu3) to 0.8-0ubuntu3.2
libnspr4-0d (4.8.4-0ubuntu1) to 4.8.6-0ubuntu0.10.04.2
libnss3-1d (3.12.6-0ubuntu3) to 3.12.9+ckbi-1.82-0ubuntu0.10.04.1
libpam-ck-connector (0.4.1-3ubuntu1) to 0.4.1-3ubuntu2
libpam-modules (1.1.1-2ubuntu5) to 1.1.1-2ubuntu5.3
libpam-runtime (1.1.1-2ubuntu5) to 1.1.1-2ubuntu5.3
libpam0g (1.1.1-2ubuntu5) to 1.1.1-2ubuntu5.3
libpango1.0-0 (1.28.0-0ubuntu2) to 1.28.0-0ubuntu2.2
libpango1.0-common (1.28.0-0ubuntu2) to 1.28.0-0ubuntu2.2
libparted0debian1 (2.2-5ubuntu5.1) to 2.2-5ubuntu5.2
libpcsclite1 (1.5.3-1ubuntu4.1) to 1.5.3-1ubuntu4.2
libperl5.10 (5.10.1-8ubuntu2) to 5.10.1-8ubuntu2.1
libphonon4 (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libplymouth2 (0.8.2-2ubuntu2) to 0.8.2-2ubuntu2.2
libpng12-0 (1.2.42-1ubuntu2.1) to 1.2.42-1ubuntu2.2
libpolkit-agent-1-0 (0.96-2) to 0.96-2ubuntu0.1
libpolkit-backend-1-0 (0.96-2) to 0.96-2ubuntu0.1
libpolkit-gobject-1-0 (0.96-2) to 0.96-2ubuntu0.1
libpoppler-glib4 (0.12.4-0ubuntu5) to 0.12.4-0ubuntu5.2
libpoppler5 (0.12.4-0ubuntu5) to 0.12.4-0ubuntu5.2
libpostproc51 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libqt4-assistant (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-core (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-dbus (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-designer (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-gui (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-network (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-opengl (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-phonon (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-qt3support (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-script (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-sql (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-sql-mysql (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-svg (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-test (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-webkit (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-xml (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqt4-xmlpatterns (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqtcore4 (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libqtgui4 (4:4.6.2-0ubuntu5.1) to 4:4.6.2-0ubuntu5.2
libsmbclient (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
libsndfile1 (1.0.21-2) to 1.0.21-2ubuntu0.10.04.1
libsoup-gnome2.4-1 (2.30.2-0ubuntu0.1) to 2.30.2-0ubuntu0.2
libsoup2.4-1 (2.30.2-0ubuntu0.1) to 2.30.2-0ubuntu0.2
libss2 (1.41.11-1ubuntu2) to 1.41.11-1ubuntu2.1
libssl0.9.8 (0.9.8k-7ubuntu8.1) to 0.9.8k-7ubuntu8.6
libswscale0 (4:0.5.1-1ubuntu1) to 4:0.5.1-1ubuntu1.1
libtiff4 (3.9.2-2ubuntu0.3) to 3.9.2-2ubuntu0.7
libudev0 (151-12.1) to 151-12.3
libuuid1 (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.2
libwbclient0 (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
libwebkit-1.0-2 (1.2.0-1) to 1.2.5-0ubuntu0.10.04.1
libwebkit-1.0-common (1.2.0-1) to 1.2.5-0ubuntu0.10.04.1
libxml2 (2.7.6.dfsg-1ubuntu1) to 2.7.6.dfsg-1ubuntu1.2
linux-firmware (1.34.1) to 1.34.7
linux-generic (2.6.32.23.24) to 2.6.32.33.39
linux-headers-generic (2.6.32.23.24) to 2.6.32.33.39
linux-image-generic (2.6.32.23.24) to 2.6.32.33.39
linux-libc-dev (2.6.32-25.44) to 2.6.32-33.71
lirc (0.8.6-0ubuntu4.1) to 0.8.6-0ubuntu4.2
login (1:4.1.4.2-1ubuntu2) to 1:4.1.4.2-1ubuntu2.2
logrotate (3.7.8-4ubuntu2) to 3.7.8-4ubuntu2.2
man-db (2.5.7-2) to 2.5.7-2ubuntu1
mobile-broadband-provider-info (20100407-1) to 20100716-1ubuntu0.1
modemmanager (0.3-0ubuntu2) to 0.3-0ubuntu2.2
mount (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.2
mountall (2.15.2) to 2.15.3
mplayer (2:1.0~rc3+svn20090426-1ubuntu16) to 2:1.0~rc3+svn20090426-1ubuntu16.1
mysql-client (5.1.41-3ubuntu12.6) to 5.1.41-3ubuntu12.10
mysql-client-5.1 (5.1.41-3ubuntu12.6) to 5.1.41-3ubuntu12.10
mysql-client-core-5.1 (5.1.41-3ubuntu12.6) to 5.1.41-3ubuntu12.10
mysql-common (5.1.41-3ubuntu12.6) to 5.1.41-3ubuntu12.10
mythbuntu-repos (8.2-0ubuntu0+mythbuntu~auto20100819002723) to 9.3-0ubuntu0+mythbuntu~auto20110703002111
network-manager (0.8-0ubuntu3) to 0.8-0ubuntu3.2
nfs-common (1:1.2.0-4ubuntu4) to 1:1.2.0-4ubuntu4.1
nfs-kernel-server (1:1.2.0-4ubuntu4) to 1:1.2.0-4ubuntu4.1
ntpdate (1:4.2.4p8+dfsg-1ubuntu2) to 1:4.2.4p8+dfsg-1ubuntu2.1
nvidia-185-kernel-source (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-185-modaliases (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-current (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-current-modaliases (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-glx-185 (260.19.06-0ubuntu1~xup1~lucid) to 275.19-0ubuntu1~lucid~xup1
nvidia-settings (260.19.06-0ubuntu1~lucid~xup) to 275.19-0ubuntu1~lucid~xup1
openssh-client (1:5.3p1-3ubuntu4) to 1:5.3p1-3ubuntu7
openssh-server (1:5.3p1-3ubuntu4) to 1:5.3p1-3ubuntu7
openssl (0.9.8k-7ubuntu8.1) to 0.9.8k-7ubuntu8.6
parted (2.2-5ubuntu5.1) to 2.2-5ubuntu5.2
passwd (1:4.1.4.2-1ubuntu2) to 1:4.1.4.2-1ubuntu2.2
perl (5.10.1-8ubuntu2) to 5.10.1-8ubuntu2.1
perl-base (5.10.1-8ubuntu2) to 5.10.1-8ubuntu2.1
perl-modules (5.10.1-8ubuntu2) to 5.10.1-8ubuntu2.1
perlmagick (7:6.5.7.8-1ubuntu1) to 7:6.5.7.8-1ubuntu1.1
plymouth (0.8.2-2ubuntu2) to 0.8.2-2ubuntu2.2
plymouth-label (0.8.2-2ubuntu2) to 0.8.2-2ubuntu2.2
plymouth-theme-ubuntu-text (0.8.2-2ubuntu2) to 0.8.2-2ubuntu2.2
pm-utils (1.3.0-1ubuntu2) to 1.3.0-1ubuntu3
policykit-1 (0.96-2) to 0.96-2ubuntu0.1
portmap (6.0.0-1ubuntu2) to 6.0.0-1ubuntu2.1
python-apt (0.7.94.2ubuntu6.2) to 0.7.94.2ubuntu6.4
python-imaging (1.1.7-1) to 1.1.7-1ubuntu0.1
python-libxml2 (2.7.6.dfsg-1ubuntu1) to 2.7.6.dfsg-1ubuntu1.2
rsync (3.0.7-1ubuntu1) to 3.0.7-1ubuntu1.1
rsyslog (4.2.0-2ubuntu8) to 4.2.0-2ubuntu8.1
samba (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
samba-common (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
samba-common-bin (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
smbclient (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
smbfs (2:3.4.7~dfsg-1ubuntu3.2) to 2:3.4.7~dfsg-1ubuntu3.6
sudo (1.7.2p1-1ubuntu5.2) to 1.7.2p1-1ubuntu5.3
system-tools-backends (2.9.4-0ubuntu1) to 2.9.4-0ubuntu1.1
sysv-rc (2.87dsf-4ubuntu17) to 2.87dsf-4ubuntu17.4
sysvinit-utils (2.87dsf-4ubuntu17) to 2.87dsf-4ubuntu17.4
tar (1.22-2) to 1.22-2ubuntu1
tzdata (2010l-0ubuntu0.10.04) to 2011g-0ubuntu0.10.04
udev (151-12.1) to 151-12.3
unattended-upgrades (0.55ubuntu4) to 0.55ubuntu5
update-inetd (4.35) to 4.35ubuntu0.1
update-manager (1:0.134.10) to 1:0.134.11
update-manager-core (1:0.134.10) to 1:0.134.11
upstart (0.6.5-7) to 0.6.5-8
util-linux (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.2
uuid-runtime (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.2
w3m (0.5.2-2.1ubuntu1.1) to 0.5.2-2.1ubuntu1.2
x11-xserver-utils (7.5+1ubuntu2) to 7.5+1ubuntu2.1
xdg-utils (1.0.2-6.1ubuntu3) to 1.0.2-6.1ubuntu3.1
xkb-data (1.8-1ubuntu8) to 1.8-1ubuntu8.1~10.04.1
xserver-common (2:1.7.6-2ubuntu7.3) to 2:1.7.6-2ubuntu7.6
xserver-xorg-core (2:1.7.6-2ubuntu7.3) to 2:1.7.6-2ubuntu7.6
xserver-xorg-input-wacom (1:0.10.5-0ubuntu4) to 1:0.10.8-0ubuntu1~xup2~lucid
xserver-xorg-video-geode (2.11.8-4) to 2.11.11-1~lucid1
xserver-xorg-video-intel (2:2.9.1-3ubuntu5) to 2:2.11.0-1ubuntu1~xup

Installed the following packages:
libx11-xcb1 (2:1.3.2-1ubuntu3)
libxcb-dri2-0 (1.5-2)
linux-headers-2.6.32-33 (2.6.32-33.71)
linux-headers-2.6.32-33-generic (2.6.32-33.71)
linux-image-2.6.32-33-generic (2.6.32-33.71)
```

Are there any other settings or configurations that could have been affected by the system update?  Or is there a way to downgrade the Nvidia driver to the previous version that I know was working correctly before the update?

---

