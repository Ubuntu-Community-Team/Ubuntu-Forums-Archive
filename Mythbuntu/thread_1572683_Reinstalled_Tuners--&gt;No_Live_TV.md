---
title: "Reinstalled Tuners--&gt;No Live TV"
date: 2010-09-11
forum: Mythbuntu
---

### Post by Jim_Rogers on 2010-09-11
Hello--

I had my mythbuntu system up and running for all of 2010 with no problems.

A couple of weeks ago, my tuners seemed to be going crazy-- they only recorded the programming on channel 12. (I.e., it recorded something I had scheduled, it was labeled correctly, but when it was played back the recording was of whatever was on channel 12 at that time.)

Anyway, I went to the mythbackend-setup, deleted all the tuners and reinstalled them. The recording problem was solved, but now I can't watch live tv.

When I first installed the tuners, they were video0, video1, video2, and video3. When I reinstalled them, video1 was not in the options, so I chose video0, video2, video3, and video32 (there was no video4 option). Tuners are PVR-500, btw.

Searching around the forums, I think the fact that I have some of the numbers different might be the problem. But I'm not sure of that and I really couldn't find a fix (that I could perform) even if it was the problem.

The strange thing is that this morning I did an update of the system, rebooted, and --surprise!-- live tv worked! I watched about 10 min on different channels without issue so I figured something in the update fixed it.

However, I came back about an hour later and tried to watch live tv and it was back to the same problem. I've rebooted the backend several times to see if I could bring it back again, but no luck.

As I said before, I can record and watch recordings just fine-- just no live tv on either the frontend or the backend.

Here is the frontend log when trying to watch on the backend (with about 40mb of that invalid file descriptor error snipped out of the middle):

> Starting mythfrontend.real..
2010-09-11 12:44:01.869 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-11 12:44:01.870 Using runtime prefix = /usr
2010-09-11 12:44:01.870 Using configuration directory = /home/mythtv110/.mythtv
2010-09-11 12:44:02.581 Empty LocalHostName.
2010-09-11 12:44:02.583 Using localhost value of mythtv110-desktop
2010-09-11 12:44:02.693 New DB connection, total: 1
2010-09-11 12:44:02.729 Connected to database 'mythconverg' at host: localhost
2010-09-11 12:44:02.737 Closing DB connection named 'DBManager0'
2010-09-11 12:44:02.798 ScreenSaverX11Private: XScreenSaver support enabled
2010-09-11 12:44:02.798 ScreenSaverX11Private: Gnome screen saver support enabled
2010-09-11 12:44:02.801 DPMS is disabled.
2010-09-11 12:44:02.804 Primary screen: 0.
2010-09-11 12:44:02.806 Connected to database 'mythconverg' at host: localhost
2010-09-11 12:44:02.808 Using screen 0, 1024x768 at 0,0
2010-09-11 12:44:02.849 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
2010-09-11 12:44:02.849 Desktop video mode: 0x0 0 Hz
2010-09-11 12:44:02.878 MythUI Image Cache size set to 20971520 bytes
2010-09-11 12:44:02.954 Enabled verbose msgs:  important general
2010-09-11 12:44:02.966 Primary screen: 0.
2010-09-11 12:44:02.967 Using screen 0, 1024x768 at 0,0
2010-09-11 12:44:02.985 Using theme base resolution of 1280x720
2010-09-11 12:44:03.011 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-09-11 12:44:03.012 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mythtv110/.mythtv/joystickmenurc
2010-09-11 12:44:03.099 Using Frameless Window
2010-09-11 12:44:03.099 Using Full Screen Window
2010-09-11 12:44:03.517 Using the Qt painter
2010-09-11 12:44:03.702 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-09-11 12:44:03.728 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-09-11 12:44:03.756 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-09-11 12:44:03.759 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-09-11 12:44:03.823 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-11 12:44:04.458 Registering Internal as a media playback plugin.
2010-09-11 12:44:04.526 Cannot load language en_us for module mytharchive
2010-09-11 12:44:04.630 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-11 12:44:04.631 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-11 12:44:04.631 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-11 12:44:04.632 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-11 12:44:04.633 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-11 12:44:04.633 MediaMonitorUnix::AddDevice() - empty device path.
2010-09-11 12:44:04.633 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-09-11 12:44:04.634 Cannot load language en_us for module mythgallery
2010-09-11 12:44:04.638 Cannot load language en_us for module mythmovies
2010-09-11 12:44:04.800 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-09-11 12:44:04.876 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-09-11 12:44:04.889 Cannot load language en_us for module mythmusic
2010-09-11 12:44:04.925 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-09-11 12:44:04.977 Cannot load language en_us for module mythvideo
2010-09-11 12:44:05.005 Cannot load language en_us for module mythweather
2010-09-11 12:44:05.010 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-09-11 12:44:05.178 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-09-11 12:44:05.182 Found mainmenu.xml for theme 'Mythbuntu'
2010-09-11 12:44:05.908 MythContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2010-09-11 12:44:05.919 Using protocol version 56
2010-09-11 12:44:09.483 TV: Attempting to change from None to WatchingLiveTV
2010-09-11 12:44:09.483 MythContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2010-09-11 12:44:09.485 Using protocol version 56
2010-09-11 12:44:09.515 Spawning LiveTV Recorder -- begin
2010-09-11 12:44:09.950 Spawning LiveTV Recorder -- end
2010-09-11 12:44:09.959 ProgramInfo(): Updated pathname '':'' -> '1008_20100911124409.mpg'
2010-09-11 12:44:09.968 We have a playbackURL(/var/lib/mythtv/livetv/1008_20100911124409.mpg) & cardtype(MPEG)
2010-09-11 12:44:16.475 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/livetv/1008_20100911124409.mpg'.
2010-09-11 12:44:16.477 We have a RingBuffer
2010-09-11 12:44:16.639 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.639 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.639 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.639 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.639 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.639 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.640 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:16.640 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'

<snipped>

2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Error: Waited 16 seconds for data, aborting.
2010-09-11 12:44:32.649 RingBuf(/var/lib/mythtv/livetv/1008_20100911124409.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2010-09-11 12:44:32.649 NVP::OpenFile(): Error, couldn't read file: /var/lib/mythtv/livetv/1008_20100911124409.mpg
2010-09-11 12:44:32.649 TV Error: LiveTV not successfully started
2010-09-11 12:44:42.328 Deleting UPnP client...

The file it is looking for does not appear to be there.

Thanks for any help,

--Jim

---

