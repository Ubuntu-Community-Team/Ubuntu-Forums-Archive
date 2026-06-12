---
title: "Frontend Crashes"
date: 2010-11-10
forum: Mythbuntu
---

### Post by clintj on 2010-11-10
I am a Nube and need a little help. When I watch live TV and I turn to certain channels my mythTV crashes on the frontend and I have to re-log back in. It only happens on certain channels but my backend stays running. If I schedule something to record on the channel that crashes the frontend it will record just fine, but has to be streamed through mythweb. Below is a copy of my crash log. Any help would be much appreciated, Thanks.

2010-11-09 19:06:58.394 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org]("http://www.mythtv.org")
2010-11-09 19:06:58.394 Using runtime prefix = /usr
2010-11-09 19:06:58.394 Using configuration directory = /home/clintj/.mythtv
2010-11-09 19:06:59.175 Empty LocalHostName.
2010-11-09 19:06:59.176 Using localhost value of ubuntu
2010-11-09 19:06:59.176 Testing network connectivity to '10.249.250.134'
2010-11-09 19:06:59.192 New DB connection, total: 1
2010-11-09 19:06:59.254 Connected to database 'mythconverg' at host: 10.249.250.134
2010-11-09 19:06:59.255 Closing DB connection named 'DBManager0'
2010-11-09 19:06:59.273 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-09 19:06:59.279 DPMS is disabled.
2010-11-09 19:06:59.285 Primary screen: 0.
2010-11-09 19:06:59.345 Connected to database 'mythconverg' at host: 10.249.250.134
2010-11-09 19:06:59.378 Using screen 0, 800x600 at 0,0
2010-11-09 19:06:59.712 Desktop video mode: 800x600 60.3173 Hz
2010-11-09 19:07:00.514 MythUI Image Cache size set to 20971520 bytes
2010-11-09 19:07:00.594 AudioPulseUtil: Suspend Success
2010-11-09 19:07:00.595 Enabled verbose msgs:  important general
2010-11-09 19:07:00.839 Primary screen: 0.
2010-11-09 19:07:00.867 Using screen 0, 800x600 at 0,0
2010-11-09 19:07:00.869 Using theme base resolution of 1280x720
2010-11-09 19:07:01.344 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No such file or directory (2)
2010-11-09 19:07:01.345 JoystickMenuThread Error: Joystick disabled - Failed to read /home/clintj/.mythtv/joystickmenurc
2010-11-09 19:07:03.530 Using Frameless Window
2010-11-09 19:07:03.531 Using Full Screen Window
2010-11-09 19:07:03.699 Using the Qt painter
2010-11-09 19:07:04.008 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Graphite/base.xml'
2010-11-09 19:07:04.022 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-11-09 19:07:04.041 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-11-09 19:07:04.042 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-09 19:07:04.085 New DB connection, total: 2
2010-11-09 19:07:04.122 Connected to database 'mythconverg' at host: 10.249.250.134
2010-11-09 19:07:04.207 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-09 19:07:17.215 Registering Internal as a media playback plugin.
2010-11-09 19:07:17.247 No plugins directory /usr/lib/mythtv/plugins
2010-11-09 19:07:17.392 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-09 19:07:17.393 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-09 19:07:17.393 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-09 19:07:17.459 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Graphite/menu-ui.xml
2010-11-09 19:07:17.628 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-09 19:07:17.666 Found mainmenu.xml for theme 'Graphite'
2010-11-09 19:07:18.010 MythContext: Connecting to backend server: 10.249.250.134:6543 (try 1 of 1)
2010-11-09 19:07:18.031 Using protocol version 23056
2010-11-09 19:07:20.161 TV: Attempting to change from None to WatchingLiveTV
2010-11-09 19:07:20.162 MythContext: Connecting to backend server: 10.249.250.134:6543 (try 1 of 1)
2010-11-09 19:07:20.183 Using protocol version 23056
2010-11-09 19:07:20.313 Spawning LiveTV Recorder -- begin
2010-11-09 19:07:20.571 Spawning LiveTV Recorder -- end
2010-11-09 19:07:20.643 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190729.mpg'
2010-11-09 19:07:21.009 We have a playbackURL(myth://10.249.250.134:6543/8820_20101109190729.mpg) & cardtype(DUMMY)
2010-11-09 19:07:21.015 We have a RingBuffer
2010-11-09 19:07:21.847 NVP(0): Disabling Audio, params(-1,2,44100)
2010-11-09 19:07:21.964 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:22.188 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:22.441 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:22.682 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:22.866 VideoOutputXv: XVideo Adaptor Name: 'VMware Video Engine'
2010-11-09 19:07:22.903 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:23.144 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:23.232 OSD Theme Dimensions W: 1280 H: 720
2010-11-09 19:07:23.373 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:23.580 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:23.802 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:24.001 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:24.008 New DB connection, total: 3
2010-11-09 19:07:24.053 Realtime priority would require SUID as root.
2010-11-09 19:07:24.070 Connected to database 'mythconverg' at host: 10.249.250.134
2010-11-09 19:07:24.105 Video timing method: USleep with busy wait
2010-11-09 19:07:24.107 TV: Changing from None to WatchingLiveTV
2010-11-09 19:07:24.108 TV: State is LiveTV & mctx == ctx
2010-11-09 19:07:24.176 TV: UpdateOSDInput done
2010-11-09 19:07:24.177 TV: UpdateLCD done
2010-11-09 19:07:24.177 TV: ITVRestart done
2010-11-09 19:07:24.203 ProgramInfo(): Updated pathname '':'' -> '8820_20101109190730.mpg'
2010-11-09 19:07:26.235 VideoOutputXv: XVideo Adaptor Name: 'VMware Video Engine'
2010-11-09 19:07:26.599 AFD: Opened codec 0xaef03620, id(MPEG2VIDEO) type(Video)
2010-11-09 19:07:26.600 AFD: codec AC3 has 6 channels
2010-11-09 19:07:26.603 AFD: Opened codec 0xaef03d70, id(AC3) type(Audio)
2010-11-09 19:07:27.659 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-11-09 19:07:27.668 Opening ALSA audio device 'default'.
2010-11-09 19:07:27.833 NVP(0): Enabling Audio
2010-11-09 19:07:31.516 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Graphite/schedule-ui.xml
2010-11-09 19:07:46.991 ProgramInfo(): Updated pathname '':'' -> '8800_20101109190755.mpg'
2010-11-09 19:07:47.132 ProgramInfo(): Updated pathname '':'' -> '8800_20101109190755.mpg'
2010-11-09 19:07:47.235 msg: On known multiplex...
2010-11-09 19:07:48.724 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.770 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.815 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.815 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.865 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.903 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.966 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:48.967 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:49.016 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:49.017 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:49.067 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:49.067 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:49.120 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:49.239 [mpeg2video @ 0x11dd120]mpeg_decode_postinit() failure
2010-11-09 19:07:51.931 AudioPulseUtil, Warning: Can not connect to sound server, can not suspend.
            Connection terminated
<unknown>: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

---

### Post by mr_luksom on 2010-11-21
I had the exact same issue setting up my front end. Whenever I tried to watch a HD interlaced channel, it would crash Xorg, and then restart myth and Xorg.

I googled a bit, and found that XvMC is the problem. Some graphics chipsets don't like it. I fixed my machine by setting the playback profile (Setup -> Playback Settings) to 'Slim' from 'CPU--'.

No issues now. Let us know how you go.

---

### Post by lightpriest on 2010-12-03
mr_luksom: Thanks for the tip, that did the trick for me. I used VDPAU Slim instead. I guess the cause is really XvMC.
I just upgraded from Lucid to Maverick, now to get LIRC working again :)

---

