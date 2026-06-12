---
title: "No UPnP"
date: 2011-12-05
forum: Mythbuntu
---

### Post by Camw on 2011-12-05
Hi,

First off I will apologies if this question has been asked already. I have had a good hunt around via google but am unable to find an answer.

I will also admit I am a complete novice when it comes to linux. My current mythbuntu setup (about 1 month old) is my first ever experience with any linux distribution.

The set up I have is 1 master backend with 2 X Frontend. The issue I have is every time I restart either front end I enter a setup screen asking for location and language. I enter the appropriate settings. Next screen is a database settings screen as far as i know all settings in this screen are correct.  next screen says no UpNP I click ok.

After completing the above sequence mythtv front end opens. When it opens it is not opening with my defult Skin. Sorry I don't know the name of the skin that it is opening with but it has a light brown back ground with large icons running horizontally through the middle. The icons are a CD a group of tools and an old style tv set. I exit out of mythtv frontend and reopen the frontend. This time it opens with my default skin and everything works as it should.

So the question is how do I set it up so I don't have to go through the location and language etc set up every time i restart the PC.

Please remember I am a complete novice if some one is able to give me very basic step by step instructions it would be very appreciated.

Thanks in advance.

---

### Post by klc5555 on 2011-12-07
Right after such a defective frontend startup, check the end of the frontend log in the log viewer (or similar) for clues, and post the output to the group.

What I suspect is happening is that Ubuntu, unlike more conservative distros, starts up networking only when the graphical desktop opens, rather than earlier in the boot sequence. This is also when Mythfrontend is starting up. I suspect that Mythfrontend may be attempting to find the remote master backend (and the mythconverg database) before there is any network connection is available, so you get the config screen when no backend is found. By the time you're able to click through the correct information, networking is ready to go and the frontend connects.

So as a guess it may be just a timing thing. But we'll need to see the frontend log output to be sure.

---

### Post by Camw on 2011-12-08
Thanks very much for the help.

Is this the correct logs bellow?


Starting mythfrontend.real..
2011-11-12 17:57:56.956 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2011-11-12 17:57:56.956 Using runtime prefix = /usr
2011-11-12 17:57:56.956 Using configuration directory = /home/cam01/.mythtv
2011-11-12 17:57:56.964 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-12 17:57:56.968 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2011-11-12 17:57:56.969 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2011-11-12 17:57:56.972 Empty LocalHostName.
2011-11-12 17:57:56.972 Using localhost value of cam01-System-Product-Name
2011-11-12 17:57:56.990 New DB connection, total: 1
2011-11-12 17:57:56.990 Unable to connect to database!
2011-11-12 17:57:56.990 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

SSDP::PerformSearch - did not write entire buffer.
2011-11-12 17:57:57.079 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
................................................................................
2011-11-12 17:57:59.174 UPnPautoconf() - No UPnP backends found
2011-11-12 17:57:59.174 No UPnP backends found
2011-11-12 17:57:59.179 Could not find theme:  - Switching to Terra
2011-11-12 17:57:59.189 Desktop video mode: 1920x1080 60.000 Hz
2011-11-12 17:57:59.950 get_ip: No address associated with hostname
2011-11-12 17:57:59.950 LIRC, Error: Failed to parse IP address ''
2011-11-12 17:57:59.950 JoystickMenuThread: Joystick disabled - Failed to read /home/cam01/.mythtv/joystickmenurc
2011-11-12 17:57:59.961 Using Frameless Window
2011-11-12 17:57:59.962 Using Full Screen Window
2011-11-12 17:57:59.965 Using the Qt painter
2011-11-12 17:58:00.695 No locale defaults file for en_NZ, skipping
2011-11-12 17:58:00.695 System Locale (en_NZ), Country (NZ), Language (en)
2011-11-12 17:58:04.391 Loading en_gb translation for module mythfrontend
2011-11-12 17:58:53.792 Writing settings file /home/cam01/.mythtv/mysql.txt
2011-11-12 17:58:53.792 Closing DB connection named 'DBManager0'
2011-11-12 17:58:53.794 Testing network connectivity to '192.168.42.9'
2011-11-12 17:58:53.895 Closing DB connection named 'DBManager0'
2011-11-12 17:58:59.109 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:58:59.112 New DB connection, total: 2
2011-11-12 17:59:04.314 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:59:04.314 New DB connection, total: 3
2011-11-12 17:59:09.531 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:59:09.541 Closing DB connection named 'DBManager0'
2011-11-12 17:59:09.541 Closing DB connection named 'DBManager1'
2011-11-12 17:59:09.541 Closing DB connection named 'DBManager2'
2011-11-12 17:59:09.541 Current locale en_NZ
2011-11-12 17:59:09.542 No locale defaults file for en_NZ, skipping
2011-11-12 17:59:09.709 ScreenSaverX11Private: XScreenSaver support enabled
2011-11-12 17:59:09.710 DPMS is disabled.
2011-11-12 17:59:14.834 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:59:20.051 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:59:25.263 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:59:25.285 Enabled verbose msgs:  important general
2011-11-12 17:59:25.293 Loading en_gb translation for module mythfrontend
2011-11-12 17:59:25.319 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2011-11-12 17:59:25.319 JoystickMenuThread: Joystick disabled - Failed to read /home/cam01/.mythtv/joystickmenurc
2011-11-12 17:59:25.436 Using Frameless Window
2011-11-12 17:59:25.436 Using Full Screen Window
2011-11-12 17:59:25.439 Using the Qt painter
2011-11-12 17:59:25.464 MythFontProperties, Warning: Attempting to define 'basesmall'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 6
			Name: 'basesmall'	Type: 'fontdef'
2011-11-12 17:59:25.465 MythFontProperties, Warning: Attempting to define 'basemedium'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 11
			Name: 'basemedium'	Type: 'fontdef'
2011-11-12 17:59:25.465 MythFontProperties, Warning: Attempting to define 'baselarge'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 15
			Name: 'baselarge'	Type: 'fontdef'
2011-11-12 17:59:25.465 MythFontProperties, Warning: Attempting to define 'baseextralarge'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 19
			Name: 'baseextralarge'	Type: 'fontdef'
2011-11-12 17:59:25.465 MythFontProperties, Warning: Attempting to define 'basesmallbrown'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 28
			Name: 'basesmallbrown'	Type: 'fontdef'
2011-11-12 17:59:25.465 MythFontProperties, Warning: Attempting to define 'basesmallgrey'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 32
			Name: 'basesmallgrey'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basesmallpurple'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 36
			Name: 'basesmallpurple'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basesmallblack'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 40
			Name: 'basesmallblack'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basesmallyellow'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 44
			Name: 'basesmallyellow'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basesmallgreen'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 48
			Name: 'basesmallgreen'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basesmallblue'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 52
			Name: 'basesmallblue'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basesmallred'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 56
			Name: 'basesmallred'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basemediumgrey'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 60
			Name: 'basemediumgrey'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basemediumgreen'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 64
			Name: 'basemediumgreen'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basemediumred'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 68
			Name: 'basemediumred'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basemediumpurple'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 72
			Name: 'basemediumpurple'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'basemediumbrown'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 76
			Name: 'basemediumbrown'	Type: 'fontdef'
2011-11-12 17:59:25.466 MythFontProperties, Warning: Attempting to define 'baselargebrown'
			with face 'Liberation Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 80
			Name: 'baselargebrown'	Type: 'fontdef'
2011-11-12 17:59:25.482 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-12 17:59:25.808 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-12 17:59:25.808 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-12 17:59:25.811 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-12 17:59:25.811 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-12 17:59:26.487 Registering Internal as a media playback plugin.
2011-11-12 17:59:26.563 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-12 17:59:26.563 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-12 17:59:26.563 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-12 17:59:26.564 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-11-12 17:59:26.565 Loading en_gb translation for module mythgallery
2011-11-12 17:59:26.603 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-11-12 17:59:26.718 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-11-12 17:59:26.737 Loading en_gb translation for module mythmusic
2011-11-12 17:59:26.758 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-11-12 17:59:26.815 Loading en_gb translation for module mythvideo
2011-11-12 17:59:26.834 Loading en_gb translation for module mythweather
2011-11-12 17:59:27.012 Found mainmenu.xml for theme 'Terra'
2011-11-12 17:59:27.032 MythCoreContext: Connecting to backend server: 192.168.42.9:6543 (try 1 of 1)
2011-11-12 17:59:27.033 Using protocol version 63
2011-11-12 17:59:36.048 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-12 17:59:36.048 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-12 17:59:36.048 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-12 17:59:36.048 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-12 17:59:36.050 Received a remote 'Clear Cache' request
2011-11-12 17:59:38.810 Using Frameless Window
2011-11-12 17:59:38.810 Using Full Screen Window
2011-11-12 17:59:38.823 Using the Qt painter
2011-11-12 17:59:39.042 Found mainmenu.xml for theme 'Terra'
2011-11-12 17:59:44.323 Deleting UPnP client...
Starting mythfrontend.real..
2011-11-12 17:59:51.875 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2011-11-12 17:59:51.875 Using runtime prefix = /usr
2011-11-12 17:59:51.875 Using configuration directory = /home/cam01/.mythtv
2011-11-12 17:59:51.876 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-12 17:59:52.820 Empty LocalHostName.
2011-11-12 17:59:52.820 Using localhost value of cam01-System-Product-Name
2011-11-12 17:59:52.821 Testing network connectivity to '192.168.42.9'
2011-11-12 17:59:52.927 New DB connection, total: 1
2011-11-12 17:59:58.138 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 17:59:58.141 Closing DB connection named 'DBManager0'
2011-11-12 18:00:03.345 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 18:00:03.349 Current locale en_NZ
2011-11-12 18:00:03.349 No locale defaults file for en_NZ, skipping
2011-11-12 18:00:03.532 ScreenSaverX11Private: XScreenSaver support enabled
2011-11-12 18:00:03.534 DPMS is disabled.
2011-11-12 18:00:03.557 Desktop video mode: 1920x1080 60.000 Hz
2011-11-12 18:00:04.268 Enabled verbose msgs:  important general
2011-11-12 18:00:04.276 Loading en_gb translation for module mythfrontend
2011-11-12 18:00:04.303 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2011-11-12 18:00:04.303 JoystickMenuThread: Joystick disabled - Failed to read /home/cam01/.mythtv/joystickmenurc
2011-11-12 18:00:04.413 Using Frameless Window
2011-11-12 18:00:04.413 Using Full Screen Window
2011-11-12 18:00:04.497 Using the Qt painter
2011-11-12 18:00:04.651 New DB connection, total: 2
2011-11-12 18:00:04.651 New DB connection, total: 3
2011-11-12 18:00:04.651 New DB connection, total: 4
2011-11-12 18:00:04.652 New DB connection, total: 5
2011-11-12 18:00:04.656 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-12 18:00:04.935 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-12 18:00:04.935 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-12 18:00:04.936 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-12 18:00:04.936 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-12 18:00:05.574 Registering Internal as a media playback plugin.
2011-11-12 18:00:05.643 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-12 18:00:05.643 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-12 18:00:05.644 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-12 18:00:05.644 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-11-12 18:00:05.644 Loading en_gb translation for module mythgallery
2011-11-12 18:00:05.659 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-11-12 18:00:05.767 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-11-12 18:00:05.784 Loading en_gb translation for module mythmusic
2011-11-12 18:00:05.800 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-11-12 18:00:05.855 Loading en_gb translation for module mythvideo
2011-11-12 18:00:05.870 Loading en_gb translation for module mythweather
2011-11-12 18:00:09.853 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 18:00:15.060 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 18:00:20.271 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 18:00:25.477 Connected to database 'mythconverg' at host: 192.168.42.9
2011-11-12 18:00:25.532 Found mainmenu.xml for theme 'Mythbuntu'
2011-11-12 18:00:25.577 MythCoreContext: Connecting to backend server: 192.168.42.9:6543 (try 1 of 1)
2011-11-12 18:00:25.578 Using protocol version 63
2011-11-12 18:00:33.765 TV: Attempting to change from None to WatchingLiveTV
2011-11-12 18:00:33.765 MythCoreContext: Connecting to backend server: 192.168.42.9:6543 (try 1 of 1)
2011-11-12 18:00:33.767 Using protocol version 63
2011-11-12 18:00:33.865 Spawning LiveTV Recorder -- begin
2011-11-12 18:00:34.394 Spawning LiveTV Recorder -- end
2011-11-12 18:00:34.422 We have a playbackURL(myth://192.168.42.9:6543/1002_20111112180034.mpg) & cardtype(DUMMY)
2011-11-12 18:00:34.423 We have a RingBuffer
2011-11-12 18:00:34.649 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-11-12 18:00:34.682 OSD: Base theme size: 1280x720
2011-11-12 18:00:34.682 OSD: Scaling factors: 0.5625x0.8
2011-11-12 18:00:34.703 OSD: Base theme size: 1280x720
2011-11-12 18:00:34.703 OSD: Scaling factors: 0.5625x0.8
2011-11-12 18:00:34.731 Player(0): Video timing method: DRM
2011-11-12 18:00:34.747 TV: Changing from None to WatchingLiveTV
2011-11-12 18:00:34.747 TV: State is LiveTV & mctx == ctx
2011-11-12 18:00:34.752 TV: UpdateOSDInput done
2011-11-12 18:00:34.752 TV: UpdateLCD done
2011-11-12 18:00:34.752 TV: ITVRestart done
2011-11-12 18:00:34.848 VideoOutput: Created YV12 OSD.
2011-11-12 18:00:36.247 [h264 @ 0x7f2907ce2700]non-existing PPS referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS 0 referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]decode_slice_header error
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]no frame!
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS 0 referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]decode_slice_header error
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]no frame!
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS 0 referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]decode_slice_header error
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]no frame!
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS referenced
2011-11-12 18:00:36.248 [h264 @ 0x7f2907ce2700]non-existing PPS 0 referenced

---

### Post by klc5555 on 2011-12-08
Well, the frontend does appear to be unable to negotiate IP at the start, and attempts to connect to a local mysql database --this would be when it complains that it can't connect to the local MySQL server through mysql.sock.

It looks like it's nearly a minute after the initial attempt to start the frontend before Mythfrontend is able successfully to negotiate the IP address 192.168.42.9 and connect to the master backend's database. So it does appear to be timing. Usually (in Ubuntu) this is handled by putting a delay of several seconds in the script /usr/bin/mythfrontend (which script starts the actual program that Ubuntu chooses to call 'mythfrontend.real')

There are various descriptions out there of how to insert this delay. One such is found in ian dobson's January 6th, 2011, 02:30 PM message in this archived discussion thread here: [http://ubuntuforums.org/archive/index.php/t-1660492.html](http://ubuntuforums.org/archive/index.php/t-1660492.html)

In your case I'd recommend trying a 30 sec delay at first. If that works, either leave it or fine-tune it down, as you prefer. If it doesn't work, try a full 60 secs. If 60 secs. doesn't work, then maybe I've got the wrong end of the stick and we'll need to rethink this from the beginning.

Ancillary considerations would include making sure the master backend starts up every time on a fixed IP address (easy to set up on your home router), and that the frontends are configured to go for this IP address directly (i.e. '192.168.42.9'), rather than having to resolve the backend server's hostname.

---

### Post by Camw on 2011-12-11
Thanks again for the help.

I found an easy temporary solution was to disable mythtv frontend from starting automatically on reboot.

My 2 frontends are very fast booting machines they both have solid state hard drives. I am guessing this could be a contributing factor to the timing issue.

---

### Post by jr3us on 2012-10-02
I had a similar problem on a new nettop frontend that is using an SSD to boot. I wound up setting the network configuration with a static ip address, and also made it NOT available to all users.

This insures that the network connection is up prior to the automatic login, and also to the mythfrontend autostart.

Works fine for me now.

---

### Post by tgm4883 on 2012-10-03
Please check the date of the thread you are replying to. Old thread is old.

---

