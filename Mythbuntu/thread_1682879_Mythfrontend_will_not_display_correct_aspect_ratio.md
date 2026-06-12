---
title: "Mythfrontend will not display correct aspect ratio."
date: 2011-02-06
forum: Mythbuntu
---

### Post by heyho on 2011-02-06
After a show-stopping problem connecting my display to my frontend using HDMI, as detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=1629273](http://ubuntuforums.org/showthread.php?t=1629273)

I have gone back to a (good quality) VGA cable.  All is good, except that anything played through mythtv is displayed incorrectly.  My screen res is 1920x1080, and the desktop displays perfectly.  The myth GUI displays perfectly, filling the whole screen.  The screen is 16:9, and the broadcasts are 16:9, but myth insists on "letterboxing" and squashing the output, as if it were being sent to a 4:3 screen.  I have tried changing everything obvious in the appearance setup - forcing the aspect ratio, changing the overscan, adjusting zoom etc, but nothing works.

If I use VLC to open a recorded TV show directly from the livetv folder, it displays it perfectly - filling the screen and everything in proportion, as does the TVs built in DVB tuner.

I hope this turns out to be something easy, as it's the last step preventing me from going forward now, and it's very frustrating!  The install is fully-up-to-date 10.04 mythbuntu 32bit.

As pictures speak a thousand words, here is a picture of the entire TV first with myth playing back a recorded show, and then VLC.  The same problem occurs watching videos.

[IMG]http://i116.photobucket.com/albums/o25/heyho1974/DSC02639.jpg[/IMG]

[IMG]http://i116.photobucket.com/albums/o25/heyho1974/DSC02640.jpg[/IMG]

---

### Post by nickrout on 2011-02-06
In settings|appearance, about page 3, do you have anything set there which is telling the system that the screen is 4:3?

Also TV settings, Playback has some relevant settings.

Also your frontend logs may have some clues?

---

### Post by heyho on 2011-02-07
Thank for your reply.  I'll get back on this tonight after work, and report back with any progress.

---

### Post by alien878 on 2011-02-09
Is it an SD broadcast?  If so, I expect you are seeing the raw "4:3" picture.  The broadcasters will sometimes squish or letterbox things to fit a 16:9 picture into it and it is up to the receiver to figure out how to un-squish or un-letterbox it.

Unfortunately (in my experience), mythtv can be bad at detecting this and you often see the raw 4:3 picture .  Sometimes it works, sometimes it doesn't.  You can fix it temporarily by pressing m->video->adjustFill.  You can also set the default fill in the settings, but this will affect all shows/channels.

If you find a way to improve the mythtv fill detection, I would be interesting in knowing.

---

### Post by heyho on 2011-02-09
It is an SD broadcast, but it is definitely a proper 16:9 picture.

If I conncect over HDMI, the picture displays perfectly(ie in proportion albeit almost completely green - see link in first post!), as it does on other televisions.

I have an inkling that this is to do with the way the tv is detected, as it at first defaults to 1440x900(using VGA connection), which I believe to be a 16:10 resolution, which would make sense.  The frontend logs show it to be a 1920x1080 screen, as that is what I have set it to be on the desktop.  I will post the logs from both connection methods in a short while when I am back on the other machine.

Using the HDMI lead, the correct resolution is detected straight away.

---

### Post by heyho on 2011-02-20
Right, managed to get back on this.

I have been looking at the frontend logs, and have created 2 separate logs , the first with the "squashed" playback connected over vga, and the second with the correct playback dimension over HDMI (but colours completely askew - ie mostly green!)  Other than the refresh rate difference, I don't know what else I should be looking for.

Here is the first log.  VGA, picture squashed.

```
Starting mythfrontend.real..
2011-02-20 13:14:41.564 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2011-02-20 13:14:41.564 Using runtime prefix = /usr
2011-02-20 13:14:41.565 Using configuration directory = /home/myth/.mythtv
2011-02-20 13:14:42.377 Empty LocalHostName.
2011-02-20 13:14:42.377 Using localhost value of myth-desktop
2011-02-20 13:14:42.383 New DB connection, total: 1
2011-02-20 13:14:42.386 Connected to database 'mythconverg' at host: localhost
2011-02-20 13:14:42.387 Closing DB connection named 'DBManager0'
2011-02-20 13:14:42.400 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-20 13:14:42.401 DPMS is disabled.
2011-02-20 13:14:42.402 Primary screen: 0.
2011-02-20 13:14:42.403 Connected to database 'mythconverg' at host: localhost
2011-02-20 13:14:42.404 Using screen 0, 1920x1080 at 0,0
2011-02-20 13:14:42.418 Desktop video mode: 1920x1080 60.0024 Hz
2011-02-20 13:14:42.735 MythUI Image Cache size set to 20971520 bytes
2011-02-20 13:14:42.754 Enabled verbose msgs:  important general
2011-02-20 13:14:42.758 Primary screen: 0.
2011-02-20 13:14:42.759 Using screen 0, 1920x1080 at 0,0
2011-02-20 13:14:42.759 Using theme base resolution of 1280x720
2011-02-20 13:14:42.765 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-02-20 13:14:42.765 JoystickMenuThread Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2011-02-20 13:14:42.796 Using Frameless Window
2011-02-20 13:14:42.796 Using Full Screen Window
2011-02-20 13:14:43.065 Using the Qt painter
2011-02-20 13:14:43.160 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-02-20 13:14:43.170 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-02-20 13:14:43.178 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-02-20 13:14:43.178 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-02-20 13:14:43.181 New DB connection, total: 2
2011-02-20 13:14:43.181 Connected to database 'mythconverg' at host: localhost
2011-02-20 13:14:43.182 Current MythTV Schema Version (DBSchemaVer): 1254
2011-02-20 13:14:43.717 Registering Internal as a media playback plugin.
2011-02-20 13:14:43.738 Cannot load language en_us for module mytharchive
2011-02-20 13:14:43.764 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.764 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.764 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.766 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.766 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.766 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.768 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.768 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.769 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.770 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.770 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.771 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.772 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.772 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.773 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 13:14:43.773 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-20 13:14:43.774 Cannot load language en_us for module mythgallery
2011-02-20 13:14:43.777 Cannot load language en_us for module mythmovies
2011-02-20 13:14:43.792 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-20 13:14:43.828 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-20 13:14:43.833 Cannot load language en_us for module mythmusic
2011-02-20 13:14:43.840 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-02-20 13:14:43.863 Cannot load language en_us for module mythvideo
2011-02-20 13:14:43.869 Cannot load language en_us for module mythweather
2011-02-20 13:14:43.870 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-20 13:14:43.931 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-02-20 13:14:43.933 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-20 13:14:44.980 MythContext: Connecting to backend server: 192.168.1.68:6543 (try 1 of 1)
2011-02-20 13:14:44.980 Using protocol version 56
2011-02-20 13:14:55.813 TV: Attempting to change from None to WatchingLiveTV
2011-02-20 13:14:55.813 MythContext: Connecting to backend server: 192.168.1.68:6543 (try 1 of 1)
2011-02-20 13:14:55.813 Using protocol version 56
2011-02-20 13:14:55.871 Spawning LiveTV Recorder -- begin
2011-02-20 13:14:56.438 Spawning LiveTV Recorder -- end
2011-02-20 13:14:56.440 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.443 We have a playbackURL(/var/lib/mythtv/livetv/1001_20110220131456.mpg) & cardtype(DUMMY)
2011-02-20 13:14:56.443 We have a RingBuffer
2011-02-20 13:14:56.575 NVP(0): Disabling Audio, params(-1,2,44100)
2011-02-20 13:14:56.602 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-02-20 13:14:56.627 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.640 OSD Theme Dimensions W: 1280 H: 720
2011-02-20 13:14:56.680 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.733 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.786 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.839 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.892 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.945 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:56.998 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.051 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.104 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.158 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.211 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.264 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.317 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.370 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.423 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.476 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.529 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.582 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131456.mpg'
2011-02-20 13:14:57.610 TV: Changing from None to WatchingLiveTV
2011-02-20 13:14:57.610 Realtime priority would require SUID as root.
2011-02-20 13:14:57.611 TV: State is LiveTV & mctx == ctx
2011-02-20 13:14:57.612 TV: UpdateOSDInput done
2011-02-20 13:14:57.612 TV: UpdateLCD done
2011-02-20 13:14:57.612 TV: ITVRestart done
2011-02-20 13:14:57.645 Video timing method: DRM
2011-02-20 13:14:57.822 ProgramInfo(): Updated pathname '':'' -> '1001_20110220131457.mpg'
2011-02-20 13:15:03.213 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-02-20 13:15:03.304 AFD: Opened codec 0xac7fe8d0, id(MPEG2VIDEO) type(Video)
2011-02-20 13:15:03.304 AFD: codec MP2 has 2 channels
2011-02-20 13:15:03.304 AFD: Opened codec 0xa8b01170, id(MP2) type(Audio)
2011-02-20 13:15:03.304 AFD: codec MP2 has 1 channels
2011-02-20 13:15:03.304 AFD: Opened codec 0xa8b018c0, id(MP2) type(Audio)
2011-02-20 13:15:03.304 AFD: Opened codec 0xac796b30, id(DVB_SUBTITLE) type(Subtitle)
2011-02-20 13:15:03.481 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2011-02-20 13:15:03.481 Opening ALSA audio device 'default'.
2011-02-20 13:15:03.524 mixer unable to find control Master 1
2011-02-20 13:15:03.525 NVP(0): Enabling Audio
2011-02-20 13:15:11.255 ProgramInfo(): Updated pathname '':'' -> '1004_20110220131511.mpg'
2011-02-20 13:15:11.258 ProgramInfo(): Updated pathname '':'' -> '1004_20110220131511.mpg'
2011-02-20 13:15:11.261 ProgramInfo(): Updated pathname '':'' -> '1004_20110220131511.mpg'
2011-02-20 13:15:13.777 ProgramInfo(): Updated pathname '':'' -> '1004_20110220131513.mpg'
2011-02-20 13:15:14.079 WriteAudio: buffer underrun
2011-02-20 13:15:15.735 NVP(0): Prebuffer wait timed out 10 times.
2011-02-20 13:15:17.398 NVP(0): Prebuffer wait timed out 20 times.
2011-02-20 13:15:19.061 NVP(0): Prebuffer wait timed out 30 times.
2011-02-20 13:15:19.792 AFD: Opened codec 0x88bcee0, id(MPEG2VIDEO) type(Video)
2011-02-20 13:15:19.792 AFD: codec MP2 has 2 channels
2011-02-20 13:15:19.792 AFD: Opened codec 0x88f5e60, id(MP2) type(Audio)
2011-02-20 13:15:19.793 AFD: codec MP3 has 0 channels
2011-02-20 13:15:19.793 AFD: Opened codec 0x89a8b10, id(MP3) type(Audio)
2011-02-20 13:15:19.793 AFD: Opened codec 0x88b3700, id(DVB_SUBTITLE) type(Subtitle)
2011-02-20 13:20:02.599 ProgramInfo(): Updated pathname '':'' -> '1004_20110220132000.mpg'
2011-02-20 13:20:05.083 RingBuffer::Reset() nonzero readpos.  toAdjust: 1 readpos: 53984 readAdjust: 111619360
2011-02-20 13:20:05.101 [mp2 @ 0x522960]Header missing
2011-02-20 13:20:05.101 AFD Error: Unknown audio decoding error
2011-02-20 13:36:03.966 [dvbsub @ 0x522960]Junk in packet
2011-02-20 13:36:03.967 [dvbsub @ 0x522960]Invalid object location!
2011-02-20 13:48:10.433 [dvbsub @ 0x522960]Junk in packet
2011-02-20 13:48:10.433 [dvbsub @ 0x522960]Invalid object location!
2011-02-20 13:54:08.907 AFD: Setting channels to 2
2011-02-20 13:55:01.451 ProgramInfo(): Updated pathname '':'' -> '1004_20110220135500.mpg'
2011-02-20 13:55:03.876 RingBuffer::Reset() nonzero readpos.  toAdjust: 1 readpos: -111533580 readAdjust: 987476204
2011-02-20 14:12:40.971 TV: Attempting to change from WatchingLiveTV to None
2011-02-20 14:12:41.600 TV: Changing from WatchingLiveTV to None
2011-02-20 14:12:44.968 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
```

And the second log, connected via HDMI, picture dimensions good, colours wrong.

```
Starting mythfrontend.real..
2011-02-20 14:28:09.543 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2011-02-20 14:28:09.543 Using runtime prefix = /usr
2011-02-20 14:28:09.543 Using configuration directory = /home/myth/.mythtv
2011-02-20 14:28:10.364 Empty LocalHostName.
2011-02-20 14:28:10.364 Using localhost value of myth-desktop
2011-02-20 14:28:10.369 New DB connection, total: 1
2011-02-20 14:28:10.372 Connected to database 'mythconverg' at host: localhost
2011-02-20 14:28:10.373 Closing DB connection named 'DBManager0'
2011-02-20 14:28:10.383 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-20 14:28:10.384 DPMS is disabled.
2011-02-20 14:28:10.385 Primary screen: 0.
2011-02-20 14:28:10.386 Connected to database 'mythconverg' at host: localhost
2011-02-20 14:28:10.387 Using screen 0, 1920x1080 at 0,0
2011-02-20 14:28:10.400 Desktop video mode: 1920x1080 50 Hz
2011-02-20 14:28:11.721 MythUI Image Cache size set to 20971520 bytes
2011-02-20 14:28:11.738 Enabled verbose msgs:  important general
2011-02-20 14:28:11.743 Primary screen: 0.
2011-02-20 14:28:11.744 Using screen 0, 1920x1080 at 0,0
2011-02-20 14:28:11.744 Using theme base resolution of 1280x720
2011-02-20 14:28:11.764 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-02-20 14:28:11.764 JoystickMenuThread Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2011-02-20 14:28:11.814 Using Frameless Window
2011-02-20 14:28:11.814 Using Full Screen Window
2011-02-20 14:28:12.082 Using the Qt painter
2011-02-20 14:28:12.214 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-02-20 14:28:12.222 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-02-20 14:28:12.284 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-02-20 14:28:12.284 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-02-20 14:28:12.289 Current MythTV Schema Version (DBSchemaVer): 1254
2011-02-20 14:28:12.351 New DB connection, total: 2
2011-02-20 14:28:12.351 New DB connection, total: 3
2011-02-20 14:28:12.352 Connected to database 'mythconverg' at host: localhost
2011-02-20 14:28:12.352 Connected to database 'mythconverg' at host: localhost
2011-02-20 14:28:14.731 Registering Internal as a media playback plugin.
2011-02-20 14:28:14.750 Cannot load language en_us for module mytharchive
2011-02-20 14:28:14.774 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.774 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.775 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.776 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.776 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.777 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.778 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.778 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.778 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.780 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.780 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.780 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.782 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.782 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.782 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-20 14:28:14.783 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-20 14:28:14.783 Cannot load language en_us for module mythgallery
2011-02-20 14:28:14.785 Cannot load language en_us for module mythmovies
2011-02-20 14:28:14.799 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-20 14:28:14.832 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-20 14:28:14.837 Cannot load language en_us for module mythmusic
2011-02-20 14:28:14.843 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-02-20 14:28:14.865 Cannot load language en_us for module mythvideo
2011-02-20 14:28:14.870 Cannot load language en_us for module mythweather
2011-02-20 14:28:14.872 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-20 14:28:14.936 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-02-20 14:28:14.938 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-20 14:28:16.214 MythContext: Connecting to backend server: 192.168.1.68:6543 (try 1 of 1)
2011-02-20 14:28:16.215 Using protocol version 56
2011-02-20 14:28:36.668 TV: Attempting to change from None to WatchingLiveTV
2011-02-20 14:28:36.668 MythContext: Connecting to backend server: 192.168.1.68:6543 (try 1 of 1)
2011-02-20 14:28:36.668 Using protocol version 56
2011-02-20 14:28:36.688 Spawning LiveTV Recorder -- begin
2011-02-20 14:28:37.056 Spawning LiveTV Recorder -- end
2011-02-20 14:28:37.058 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.061 We have a playbackURL(/var/lib/mythtv/livetv/1004_20110220142836.mpg) & cardtype(DUMMY)
2011-02-20 14:28:37.061 We have a RingBuffer
2011-02-20 14:28:37.187 NVP(0): Disabling Audio, params(-1,2,44100)
2011-02-20 14:28:37.207 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-02-20 14:28:37.239 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.241 OSD Theme Dimensions W: 1280 H: 720
2011-02-20 14:28:37.291 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.344 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.397 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.449 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.502 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.555 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.608 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.660 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.713 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.766 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.819 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.872 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.925 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:37.978 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:38.031 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:38.083 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142836.mpg'
2011-02-20 14:28:38.097 TV: Changing from None to WatchingLiveTV
2011-02-20 14:28:38.098 Realtime priority would require SUID as root.
2011-02-20 14:28:38.098 TV: State is LiveTV & mctx == ctx
2011-02-20 14:28:38.099 TV: UpdateOSDInput done
2011-02-20 14:28:38.099 TV: UpdateLCD done
2011-02-20 14:28:38.099 TV: ITVRestart done
2011-02-20 14:28:38.134 Video timing method: DRM
2011-02-20 14:28:38.342 ProgramInfo(): Updated pathname '':'' -> '1004_20110220142838.mpg'
2011-02-20 14:28:43.871 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-02-20 14:28:44.141 AFD: Opened codec 0xb55e9ea0, id(MPEG2VIDEO) type(Video)
2011-02-20 14:28:44.141 AFD: codec MP2 has 2 channels
2011-02-20 14:28:44.141 AFD: Opened codec 0xb559b440, id(MP2) type(Audio)
2011-02-20 14:28:44.142 AFD: codec MP3 has 0 channels
2011-02-20 14:28:44.142 AFD: Opened codec 0xb55e2bf0, id(MP3) type(Audio)
2011-02-20 14:28:44.142 AFD: Opened codec 0xb55a9380, id(DVB_SUBTITLE) type(Subtitle)
2011-02-20 14:28:44.277 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2011-02-20 14:28:44.277 Opening ALSA audio device 'default'.
2011-02-20 14:28:44.343 mixer unable to find control Master 1
2011-02-20 14:28:44.344 NVP(0): Enabling Audio
2011-02-20 14:29:53.392 AFD: Setting channels to 2
2011-02-20 14:40:21.880 TV: Attempting to change from WatchingLiveTV to None
2011-02-20 14:40:22.378 TV: Changing from WatchingLiveTV to None
2011-02-20 14:40:31.108 Deleting UPnP client...
```

Any help greatfully received!  If I can't overcome this problem, it might be new TV time.:(

---

### Post by heyho on 2011-02-22
And back up...

Anybody any idea why the myth internal playback is getting this wrong, when other players are OK?

My best guess is that despite the desktop resolution being 1920x1080 (16:9), for some reason it thinks that it is 1440x900 (16:10), as the OS does upon 1st boot, until I specify the correct settings.

---

### Post by BicyclerBoy on 2011-02-24
Myth may have the aspect/size wrong because you have set it to a video playback resolution the display does not support (VGA).
Try setting it to auto ?

Common/normal for new TVs to not support the same resolution & not native over VGA.
The VGA video mode can have a diff pixel aspect ratio.

The green colour with HDMI could be wrong colour-space: HDMI video defaults to YUV (YCbCr). VGA is RGB (video RGB is diff to PC VGA).
Some video drivers allow YUV or RGB & colour-space settings..(nvidia).
Most HDMI TVs can be set to use RGB (could be called PC input mode).

Post your /var/log/Xorg.0.log files for the 2 display connector setups..

---

### Post by heyho on 2011-02-24
> **BicyclerBoy said:**
> Myth may have the aspect/size wrong because you have set it to a video playback resolution the display does not support (VGA).
Try setting it to auto ?

Common/normal for new TVs to not support the same resolution & not native over VGA.
The VGA video mode can have a diff pixel aspect ratio.

The green colour with HDMI could be wrong colour-space: HDMI video defaults to YUV (YCbCr). VGA is RGB (video RGB is diff to PC VGA).
Some video drivers allow YUV or RGB & colour-space settings..(nvidia).
Most HDMI TVs can be set to use RGB (could be called PC input mode).

Post your /var/log/Xorg.0.log files for the 2 display connector setups..

Many thanks for your reply.  

I'm pretty sure that everything in myth relating to playback resolution is set to auto.  Is there a specific setting you have in mind that I should be looking at?

As for the colour space issue, yes, I believe that you are describing the problem exactly, it's just that I didn't quite know where to dig for the info I need.  I'm just getting used to using logs, so as soon as I have some time, I'll post up those that you've requested.

My graphics chip is intel G41, and the TV is a bit of a "no-name" tesco special, but if I can get the HDMI connection working, I would be over the moon!

---

### Post by BicyclerBoy on 2011-02-25
I just thought it was possible you were forcing a resolution that had a different aspect ratio to the actual video mode.

I think you should post the /var/log/Xorg.0.log with the VGA & HDMI connection..

The G41 chipset is the X4500 graphics engine..Are you using an intel driver ?
Should be possible to set the video output to YUV..but can't find how to so far..

---

### Post by heyho on 2011-02-25
Thanks BicyclerBoy.

As far as I know, I'm using the correct drivers as supplied with lucid.  

Here is the log for VGA:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux myth-desktop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=72f88c87-1e5b-4690-98ce-17e65379394a ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 25 19:12:28 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2e32:1458:d000 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xf5000000/4194304, 0xe0000000/268435456, I/O @ 0x0000e400/8
(--) PCI: (0:0:2:1) 8086:2e33:1458:d000 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xf5400000/1048576
(--) PCI: (0:1:0:0) 14f1:8800:0070:9002 Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder rev 5, Mem @ 0xf0000000/16777216
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G41
(--) intel(0): Chipset: "G41"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: CVT  Model: 4668  Serial#: 0
(II) intel(0): Year: 2002  Week: 35
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:
(II) intel(0): Max Image Size [cm]: horiz.: 36  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): GTF timings supported
(II) intel(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) intel(0): blueX: 0.155 blueY: 0.070   whiteX: 0.281 whiteY: 0.311
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 107.0 MHz   Image Size:  360 x 290 mm
(II) intel(0): h_active: 1440  h_sync: 1450  h_sync_end 1602 h_blank_end 1904 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) intel(0):  M216H1
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  708 x 398 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 137.0 MHz   Image Size:  360 x 290 mm
(II) intel(0): h_active: 1440  h_sync: 1452  h_sync_end 1604 h_blank_end 1936 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 942 v_border: 0
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000ed4684600000000
(II) intel(0): 	230c010300241d78ef0dc2a057479827
(II) intel(0): 	12484fbfef0001010101010101010101
(II) intel(0): 	818001010101cc29a0d0518422300a98
(II) intel(0): 	360068221100001e000000fe004d3231
(II) intel(0): 	3648310a0a0a0a0a0a0a023a80187138
(II) intel(0): 	2d40582c4500c48e2100001e8435a0f0
(II) intel(0): 	51842a300c98360068221100001e005a
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1440x900"x60.2  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1680x1050"x69.9  174.00  1680 1800 1976 2272  1050 1053 1059 1096 -hsync +vsync (76.6 kHz)
(II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x75.1  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA1 using initial mode 1440x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(**) intel(0): Display dimensions: (360, 290) mm
(**) intel(0): DPI set to (101, 78)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 380 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HID 05a4:9881 (/dev/input/event4)
(**) HID 05a4:9881: Applying InputClass "evdev keyboard catchall"
(**) HID 05a4:9881: always reports core events
(**) HID 05a4:9881: Device: "/dev/input/event4"
(II) HID 05a4:9881: Found keys
(II) HID 05a4:9881: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 05a4:9881" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HID 05a4:9881 (/dev/input/event5)
(**) HID 05a4:9881: Applying InputClass "evdev pointer catchall"
(**) HID 05a4:9881: Applying InputClass "evdev keyboard catchall"
(**) HID 05a4:9881: always reports core events
(**) HID 05a4:9881: Device: "/dev/input/event5"
(II) HID 05a4:9881: Found 9 mouse buttons
(II) HID 05a4:9881: Found scroll wheel(s)
(II) HID 05a4:9881: Found relative axes
(II) HID 05a4:9881: Found x and y relative axes
(II) HID 05a4:9881: Found keys
(II) HID 05a4:9881: Configuring as mouse
(II) HID 05a4:9881: Configuring as keyboard
(**) HID 05a4:9881: YAxisMapping: buttons 4 and 5
(**) HID 05a4:9881: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 05a4:9881" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) HID 05a4:9881: initialized for relative axes.
(II) config/udev: Adding input device HID 05a4:9881 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device cx88 IR (Hauppauge Nova-T DVB-T (/dev/input/event6)
(**) cx88 IR (Hauppauge Nova-T DVB-T: Applying InputClass "evdev keyboard catchall"
(**) cx88 IR (Hauppauge Nova-T DVB-T: always reports core events
(**) cx88 IR (Hauppauge Nova-T DVB-T: Device: "/dev/input/event6"
(II) cx88 IR (Hauppauge Nova-T DVB-T: Found keys
(II) cx88 IR (Hauppauge Nova-T DVB-T: Configuring as keyboard
(II) XINPUT: Adding extended input device "cx88 IR (Hauppauge Nova-T DVB-T" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event8)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event8"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device IR-receiver inside an USB DVB receiver (/dev/input/event9)
(**) IR-receiver inside an USB DVB receiver: Applying InputClass "evdev keyboard catchall"
(**) IR-receiver inside an USB DVB receiver: always reports core events
(**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event9"
(II) IR-receiver inside an USB DVB receiver: Found keys
(II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Allocate new frame buffer 1920x1080 stride 1920
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "CVT", prod id 18024
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  107.00  1440 1450 1602 1904  900 903 909 934 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  137.00  1440 1452 1604 1936  900 903 909 942 +hsync +vsync (70.8 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)

```

And for HDMI:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux myth-desktop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=72f88c87-1e5b-4690-98ce-17e65379394a ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 25 19:05:29 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2e32:1458:d000 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xf5000000/4194304, 0xe0000000/268435456, I/O @ 0x0000e400/8
(--) PCI: (0:0:2:1) 8086:2e33:1458:d000 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xf5400000/1048576
(--) PCI: (0:1:0:0) 14f1:8800:0070:9002 Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder rev 5, Mem @ 0xf0000000/16777216
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G41
(--) intel(0): Chipset: "G41"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): Manufacturer: CVT  Model: 1080  Serial#: 20070707
(II) intel(0): Year: 2007  Week: 32
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 70  vert.: 40
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  735 x 420 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 27.0 MHz   Image Size:  735 x 420 mm
(II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) intel(0): Monitor name: CVTE TV
(II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 70 kHz, PixClock max 150 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000ed4801033413201
(II) intel(0): 	20110103804628780aee91a3544c9926
(II) intel(0): 	0f505400000001010101010101010101
(II) intel(0): 	010101010101023a80d072382d40102c
(II) intel(0): 	4580dfa42100001e8c0ad08a20e02d10
(II) intel(0): 	103e9600dfa421000018000000fc0043
(II) intel(0): 	5654452054560a2020202020000000fd
(II) intel(0): 	00303e0e460f000a2020202020200196
(II) intel(0): Printing probed modes for output HDMI2
(II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
(II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
(II) intel(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
(II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 connected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output HDMI2 using initial mode 1920x1080
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 507 x 285
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HID 05a4:9881 (/dev/input/event4)
(**) HID 05a4:9881: Applying InputClass "evdev keyboard catchall"
(**) HID 05a4:9881: always reports core events
(**) HID 05a4:9881: Device: "/dev/input/event4"
(II) HID 05a4:9881: Found keys
(II) HID 05a4:9881: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 05a4:9881" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HID 05a4:9881 (/dev/input/event5)
(**) HID 05a4:9881: Applying InputClass "evdev pointer catchall"
(**) HID 05a4:9881: Applying InputClass "evdev keyboard catchall"
(**) HID 05a4:9881: always reports core events
(**) HID 05a4:9881: Device: "/dev/input/event5"
(II) HID 05a4:9881: Found 9 mouse buttons
(II) HID 05a4:9881: Found scroll wheel(s)
(II) HID 05a4:9881: Found relative axes
(II) HID 05a4:9881: Found x and y relative axes
(II) HID 05a4:9881: Found keys
(II) HID 05a4:9881: Configuring as mouse
(II) HID 05a4:9881: Configuring as keyboard
(**) HID 05a4:9881: YAxisMapping: buttons 4 and 5
(**) HID 05a4:9881: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 05a4:9881" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) HID 05a4:9881: initialized for relative axes.
(II) config/udev: Adding input device HID 05a4:9881 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device cx88 IR (Hauppauge Nova-T DVB-T (/dev/input/event6)
(**) cx88 IR (Hauppauge Nova-T DVB-T: Applying InputClass "evdev keyboard catchall"
(**) cx88 IR (Hauppauge Nova-T DVB-T: always reports core events
(**) cx88 IR (Hauppauge Nova-T DVB-T: Device: "/dev/input/event6"
(II) cx88 IR (Hauppauge Nova-T DVB-T: Found keys
(II) cx88 IR (Hauppauge Nova-T DVB-T: Configuring as keyboard
(II) XINPUT: Adding extended input device "cx88 IR (Hauppauge Nova-T DVB-T" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device IR-receiver inside an USB DVB receiver (/dev/input/event9)
(**) IR-receiver inside an USB DVB receiver: Applying InputClass "evdev keyboard catchall"
(**) IR-receiver inside an USB DVB receiver: always reports core events
(**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event9"
(II) IR-receiver inside an USB DVB receiver: Found keys
(II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event7)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event7"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): EDID vendor "CVT", prod id 4224
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID vendor "CVT", prod id 4224
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID vendor "CVT", prod id 4224
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID vendor "CVT", prod id 4224
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID vendor "CVT", prod id 4224
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)

```

Quite a bit of info, pick the bones out of that little lot!

Thanks again for steering me, hopefully I will learn something even if I can't resolve this issue.

---

### Post by BicyclerBoy on 2011-02-25
Well my intel GPU experience only goes as far as a netbook but..

I think that:
- The display EDID supports HDMI 1920x1080p at 50Hz but not 60Hz..okay for UK, not so good for 60Hz material.
- the display EDID indicates support VGA 1920x1080 at 60Hz only
- You don't have an /etc/X11/xorg.conf files..that's okay easy to make one.
- xorg is loading the intel driver, I think it is the right one ??
- the VGA defaults to 1440x900 because the display does support 1920x1080 but not with DFP reduced vertical blanking timings.
"Not using default mode "1920x1080" (monitor doesn't support reduced blanking)"
This can be over come with a custom modeline in xorg.conf AFAIK.
VGA (1440x900):
intel(0): Display dimensions: (360, 290) mm
(**) intel(0): DPI set to (101, 78 )
HDMI
(==) intel(0): DPI set to (96, 96)
This is why the pixel aspect ratio is diff from VGA to HDMI.. 

- the driver seems to support YUV & RGB over HDMI, I do not know how to set this in intel driver.

I think the VGA can be made to work at 1920x1080 at 50Hz by custom modeline.
That YUV must be selectable somehow..

So I would make a default /etc/X11/xorg.conf file
**Xorg -configure**
[http://www.x.org/wiki/ConfigurationHelp#Xorg-configure](http://www.x.org/wiki/ConfigurationHelp#Xorg-configure)
or better to reset your xorg.conf to default..
sudo dpkg-reconfigure xserver-xorg
& then check this does not make things worse before adding anything new..

Check the intel driver by terminal cmd:
lsmod 
Look for i915 or similar..
The correct driver may allow  "intel(0): Intel XvMC decoder disabled" to be enabled for h/w decode of MPEG2..
Driver &#8220;intel&#8221;
Option &#8220;AccelMethod&#8221; &#8220;UXA&#8221; or
Option "AccelMethod" "EXA"
You may need to upgrade to 10.04 to get a more up to date kernel & intel driver..You may need to allocate more RAM (512MB) to the GPU (BIOS setting ?)

This ppa has xorg updates for 9.04 ..
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/?field.series_filter=jaunty](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/?field.series_filter=jaunty)

---

### Post by heyho on 2011-02-26
Thanks, the info you have extracted makes perfect sense.

I'm actually using 10.04 (must update my info), and last night I followed these instructions:

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

To update to the latest intel driver and kernel.  I will now start work on creating the xorg.conf file, and see where we go from there!

---

