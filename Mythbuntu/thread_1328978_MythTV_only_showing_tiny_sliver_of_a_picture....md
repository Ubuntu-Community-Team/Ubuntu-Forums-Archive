---
title: "MythTV only showing tiny sliver of a picture..."
date: 2009-11-16
forum: Mythbuntu
---

### Post by duker on 2009-11-16
I just installed Mybuntu 9.10
I am running MythTV 0.22.0+fixes22594-0ubuntu1

None of the capture cards worked until I installed IVTV.
Then I could see that the setup was sometimes detecting the card. 
Then after many tries of combinations of setting in the backend for capture cards, I found that I could get it to detect Hauppauge WinTV PVR-250 with IVTV MPEG-2 encoder card as the card type.
When I go to Watch TV in the front end I get a very very thin line of the picture across the centre of the screen, and the audio works, and if I try to play a DVD (I activated libdvdcss2 in the propriety codecs) I  also just get a very thin line across the screen, and I can see things moving in that tiny sliver of a picture, and the audio works too.
I have looked for screen res settings etc. but no luck so far.

here is the last bit of the log for the back end...


[INDENT]
2009-11-16 22:11:23.132 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-16 22:11:26.116 Reschedule requested for id -1.
2009-11-16 22:11:26.156 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2009-11-16 22:11:26.163 Seem to be woken up by USER
2009-11-16 22:12:43.119 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-16 22:17:02.242 MainServer::ANN Monitor
2009-11-16 22:17:02.245 adding: duke-desktop as a client (events: 0)
2009-11-16 22:24:00.859 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-16 22:24:00.874 Using runtime prefix = /usr
2009-11-16 22:24:00.892 Using configuration directory = /home/mythtv/.mythtv
2009-11-16 22:24:00.902 Empty LocalHostName.
2009-11-16 22:24:00.914 Using localhost value of duke-desktop
2009-11-16 22:24:00.942 New DB connection, total: 1
2009-11-16 22:24:00.947 Connected to database 'mythconverg' at host: localhost
2009-11-16 22:24:00.967 Closing DB connection named 'DBManager0'
2009-11-16 22:24:00.970 Connected to database 'mythconverg' at host: localhost
2009-11-16 22:24:00.974 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-16 22:24:00.978 MythBackend: Starting up as the master server.
2009-11-16 22:24:00.992 New DB connection, total: 2
2009-11-16 22:24:00.996 Connected to database 'mythconverg' at host: localhost
2009-11-16 22:24:01.001 New DB connection, total: 3
2009-11-16 22:24:01.008 Connected to database 'mythconverg' at host: localhost
2009-11-16 22:24:01.080 New DB scheduler connection
2009-11-16 22:24:01.082 Connected to database 'mythconverg' at host: localhost
2009-11-16 22:24:01.097 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-11-16 22:24:01.099 Main::Registering HttpStatus Extension
2009-11-16 22:24:01.101 Enabled verbose msgs:  important general
2009-11-16 22:24:01.104 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-16 22:24:04.088 Reschedule requested for id -1.
2009-11-16 22:24:04.129 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2009-11-16 22:24:04.136 Seem to be woken up by USER
2009-11-16 22:25:21.093 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-16 22:25:34.383 MainServer::ANN Monitor
2009-11-16 22:25:34.385 adding: duke-desktop as a client (events: 0)
2009-11-16 22:25:34.387 MainServer::ANN Monitor
2009-11-16 22:25:34.390 adding: duke-desktop as a client (events: 1)
2009-11-16 22:25:38.627 MainServer::ANN Playback
2009-11-16 22:25:38.628 adding: duke-desktop as a client (events: 0)
2009-11-16 22:25:38.631 TVRec(18): Changing from None to Watching WatchingLiveTV
2009-11-16 22:25:38.636 TVRec(18): HW Tuner: 18->18
2009-11-16 22:25:38.741 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2009-11-16 22:25:38.753 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-11-16 22:25:40.432 RecBase(18:/dev/video0): GetKeyframePositions(1,9223372036854775807,#2) out of 3
2009-11-16 22:26:53.719 TVRec(18): Changing from Watching WatchingLiveTV to None
2009-11-16 22:26:53.722 Unknown type, recording width was 0
2009-11-16 22:26:53.894 Finished recording Unknown: channel 1000



and the front end log just before the ring buffer error


			
[INDENT][INDENT]2009-11-16 19:03:43.913 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:03:43.916 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:03:43.919 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:03:43.927 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:03:43.930 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:03:43.934 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:03:43.937 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-16 19:03:43.955 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-16 19:03:43.987 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-16 19:03:43.998 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-16 19:03:44.050 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-16 19:03:44.097 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-16 19:03:44.099 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-16 19:03:44.448 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 19:03:44.450 Using protocol version 50
2009-11-16 19:03:46.758 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-16 19:03:46.759 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 19:03:46.759 Using protocol version 50
2009-11-16 19:03:46.762 Spawning LiveTV Recorder -- begin
2009-11-16 19:03:46.859 Spawning LiveTV Recorder -- end
2009-11-16 19:03:46.876 We have a playbackURL(/var/lib/mythtv/livetv/1000_20091116190346.nuv) & cardtype(V4L)
2009-11-16 19:03:46.877 We have a RingBuffer
2009-11-16 19:04:26.929 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-11-16 19:04:26.929 TV Error: LiveTV not successfully started
2009-11-16 19:04:26.939 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-16 19:04:26.944 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-16 19:04:52.658 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2009-11-16 19:06:28.949 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-16 19:06:28.949 Using runtime prefix = /usr
2009-11-16 19:06:28.949 Using configuration directory = /home/duke/.mythtv
2009-11-16 19:06:29.803 Empty LocalHostName.
2009-11-16 19:06:29.803 Using localhost value of duke-desktop
2009-11-16 19:06:29.813 New DB connection, total: 1
2009-11-16 19:06:29.820 Connected to database 'mythconverg' at host: localhost
2009-11-16 19:06:29.821 Closing DB connection named 'DBManager0'
2009-11-16 19:06:29.838 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-16 19:06:29.840 DPMS is active.
2009-11-16 19:06:29.843 Primary screen: 0.
2009-11-16 19:06:29.844 Connected to database 'mythconverg' at host: localhost
2009-11-16 19:06:29.848 Using screen 0, 832x624 at 0,0
2009-11-16 19:06:29.858 MythUI Image Cache size set to 20971520 bytes
2009-11-16 19:06:29.858 Enabled verbose msgs:  important general
2009-11-16 19:06:29.863 Primary screen: 0.
2009-11-16 19:06:29.864 Using screen 0, 832x624 at 0,0
2009-11-16 19:06:29.865 Using theme base resolution of 1280x720
2009-11-16 19:06:29.869 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2009-11-16 19:06:29.870 JoystickMenuThread Error: Joystick disabled - Failed to read /home/duke/.mythtv/joystickmenurc
2009-11-16 19:06:29.976 Using the Qt painter
2009-11-16 19:06:30.112 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-16 19:06:30.123 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-16 19:06:30.129 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-16 19:06:30.129 Unable to load window 'backgroundwindow' from base
2009-11-16 19:06:30.134 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-16 19:06:30.137 New DB connection, total: 2
2009-11-16 19:06:30.137 Connected to database 'mythconverg' at host: localhost
2009-11-16 19:06:30.310 Desktop video mode: 832x624 74.5545 Hz
2009-11-16 19:06:30.571 Registering Internal as a media playback plugin.
2009-11-16 19:06:30.620 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.623 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.627 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.634 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.637 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.641 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.648 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.652 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.655 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.663 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.666 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.669 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.677 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.681 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.684 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 19:06:30.688 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-16 19:06:30.705 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-16 19:06:30.737 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-16 19:06:30.748 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-16 19:06:30.790 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-16 19:06:30.846 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-16 19:06:30.848 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-16 19:06:31.191 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 19:06:31.193 Using protocol version 50
2009-11-16 19:06:33.708 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-16 19:06:33.709 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 19:06:33.710 Using protocol version 50
2009-11-16 19:06:33.714 Spawning LiveTV Recorder -- begin
2009-11-16 19:06:33.843 Spawning LiveTV Recorder -- end
2009-11-16 19:06:33.867 We have a playbackURL(/var/lib/mythtv/livetv/1000_20091116190633.nuv) & cardtype(V4L)
2009-11-16 19:06:33.868 We have a RingBuffer
2009-11-16 19:07:13.922 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-11-16 19:07:13.922 TV Error: LiveTV not successfully started
2009-11-16 19:07:13.932 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-16 19:07:13.936 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-16 19:07:21.211 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2009-11-16 21:14:00.675 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-16 21:14:00.675 Using runtime prefix = /usr
2009-11-16 21:14:00.675 Using configuration directory = /home/duke/.mythtv
2009-11-16 21:14:01.530 Empty LocalHostName.
2009-11-16 21:14:01.530 Using localhost value of duke-desktop
2009-11-16 21:14:01.540 New DB connection, total: 1
2009-11-16 21:14:01.547 Connected to database 'mythconverg' at host: localhost
2009-11-16 21:14:01.548 Closing DB connection named 'DBManager0'
2009-11-16 21:14:01.565 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-16 21:14:01.566 DPMS is active.
2009-11-16 21:14:01.568 Primary screen: 0.
2009-11-16 21:14:01.569 Connected to database 'mythconverg' at host: localhost
2009-11-16 21:14:01.570 Using screen 0, 832x624 at 0,0
2009-11-16 21:14:01.579 MythUI Image Cache size set to 20971520 bytes
2009-11-16 21:14:01.580 Enabled verbose msgs:  important general
2009-11-16 21:14:01.585 Primary screen: 0.
2009-11-16 21:14:01.586 Using screen 0, 832x624 at 0,0
2009-11-16 21:14:01.586 Using theme base resolution of 1280x720
2009-11-16 21:14:01.591 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2009-11-16 21:14:01.591 JoystickMenuThread Error: Joystick disabled - Failed to read /home/duke/.mythtv/joystickmenurc
2009-11-16 21:14:01.702 Using the Qt painter
2009-11-16 21:14:01.820 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-16 21:14:01.833 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-16 21:14:01.839 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-16 21:14:01.839 Unable to load window 'backgroundwindow' from base
2009-11-16 21:14:01.843 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-16 21:14:01.847 New DB connection, total: 2
2009-11-16 21:14:01.847 Connected to database 'mythconverg' at host: localhost
2009-11-16 21:14:02.016 Desktop video mode: 832x624 74.5545 Hz
2009-11-16 21:14:02.289 Registering Internal as a media playback plugin.
2009-11-16 21:14:02.338 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.341 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.344 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.352 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.355 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.358 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.366 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.369 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.372 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.380 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.383 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.387 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.395 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.398 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.401 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:14:02.405 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-16 21:14:02.422 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-16 21:14:02.455 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-16 21:14:02.467 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-16 21:14:02.511 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-16 21:14:02.546 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-16 21:14:02.556 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-16 21:14:02.920 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 21:14:02.921 Using protocol version 50
2009-11-16 21:14:09.966 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-16 21:14:09.967 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 21:14:09.967 Using protocol version 50
2009-11-16 21:14:09.971 Spawning LiveTV Recorder -- begin
2009-11-16 21:14:10.074 Spawning LiveTV Recorder -- end
2009-11-16 21:14:10.084 We have a playbackURL(/var/lib/mythtv/livetv/1000_20091116211410.mpg) & cardtype(MPEG)
2009-11-16 21:14:10.832 We have a RingBuffer
2009-11-16 21:14:10.883 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-16 21:14:11.627 AFD: Opened codec 0x15e0500, id(MPEG2VIDEO) type(Video)
2009-11-16 21:14:11.627 AFD: codec MP2 has 2 channels
2009-11-16 21:14:11.627 AFD: Opened codec 0x15e0930, id(MP2) type(Audio)
2009-11-16 21:14:11.807 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-16 21:14:11.807 Opening ALSA audio device 'default'.
2009-11-16 21:14:11.886 mixer set channel 0 err -1: Operation not permitted
2009-11-16 21:14:11.890 mixer set channel 1 err -1: Operation not permitted
2009-11-16 21:14:11.970 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2009-11-16 21:14:12.090 OSD Theme Dimensions W: 1280 H: 720
2009-11-16 21:14:12.794 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-11-16 21:14:12.795 TV: Changing from None to Watching WatchingLiveTV
2009-11-16 21:14:12.795 TV: State is LiveTV & mctx == ctx
2009-11-16 21:14:12.796 TV: UpdateOSDInput done
2009-11-16 21:14:12.796 TV: UpdateLCD done
2009-11-16 21:14:12.796 TV: ITVRestart done
2009-11-16 21:14:12.805 Realtime priority would require SUID as root.
2009-11-16 21:14:12.819 Video timing method: DRM
2009-11-16 21:14:12.829 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-16 21:14:44.597 TV: Attempting to change from Watching WatchingLiveTV to None
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    132 (Uknown extension)
  Minor opcode: 13 (Unknown request)
  Resource id:  0x49
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    132 (Uknown extension)
  Minor opcode: 13 (Unknown request)
  Resource id:  0x48
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    132 (Uknown extension)
  Minor opcode: 13 (Unknown request)
  Resource id:  0x4a
2009-11-16 21:14:44.810 TV: Changing from Watching WatchingLiveTV to None
2009-11-16 21:14:44.811 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-16 21:14:52.159 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2009-11-16 21:17:07.673 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-16 21:17:07.673 Using runtime prefix = /usr
2009-11-16 21:17:07.673 Using configuration directory = /home/duke/.mythtv
2009-11-16 21:17:08.527 Empty LocalHostName.
2009-11-16 21:17:08.528 Using localhost value of duke-desktop
2009-11-16 21:17:08.537 New DB connection, total: 1
2009-11-16 21:17:08.544 Connected to database 'mythconverg' at host: localhost
2009-11-16 21:17:08.545 Closing DB connection named 'DBManager0'
2009-11-16 21:17:08.562 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-16 21:17:08.564 DPMS is active.
2009-11-16 21:17:08.566 Primary screen: 0.
2009-11-16 21:17:08.568 Connected to database 'mythconverg' at host: localhost
2009-11-16 21:17:08.569 Using screen 0, 832x624 at 0,0
2009-11-16 21:17:08.597 MythUI Image Cache size set to 20971520 bytes
2009-11-16 21:17:08.598 Enabled verbose msgs:  important general
2009-11-16 21:17:08.608 Primary screen: 0.
2009-11-16 21:17:08.609 Using screen 0, 832x624 at 0,0
2009-11-16 21:17:08.610 Using theme base resolution of 1280x720
2009-11-16 21:17:08.620 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2009-11-16 21:17:08.620 JoystickMenuThread Error: Joystick disabled - Failed to read /home/duke/.mythtv/joystickmenurc
2009-11-16 21:17:08.779 Using the Qt painter
2009-11-16 21:17:08.895 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-16 21:17:08.907 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-16 21:17:08.913 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-16 21:17:08.914 Unable to load window 'backgroundwindow' from base
2009-11-16 21:17:08.939 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-16 21:17:09.099 Desktop video mode: 832x624 74.5545 Hz
2009-11-16 21:17:09.415 Registering Internal as a media playback plugin.
2009-11-16 21:17:09.461 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.464 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.467 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.475 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.478 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.482 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.489 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.492 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.496 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.503 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.507 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.510 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.518 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.521 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.524 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-16 21:17:09.528 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-16 21:17:09.545 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-16 21:17:09.575 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-16 21:17:09.585 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-16 21:17:09.624 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-16 21:17:09.676 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-16 21:17:09.678 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-16 21:17:10.024 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 21:17:10.025 Using protocol version 50
2009-11-16 21:17:15.844 New DB connection, total: 2
2009-11-16 21:17:15.845 Connected to database 'mythconverg' at host: localhost
2009-11-16 21:17:15.938 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-16 21:17:15.939 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-11-16 21:17:15.940 Using protocol version 50
2009-11-16 21:17:16.034 Spawning LiveTV Recorder -- begin
2009-11-16 21:17:16.173 Spawning LiveTV Recorder -- end
2009-11-16 21:17:16.192 We have a playbackURL(/var/lib/mythtv/livetv/1000_20091116211716.mpg) & cardtype(MPEG)
2009-11-16 21:17:22.693 RingBuf(/var/lib/mythtv/livetv/1000_20091116211716.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/livetv/1000_20091116211716.mpg'.
2009-11-16 21:17:22.694 We have a RingBuffer
2009-11-16 21:17:22.745 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-16 21:17:22.775 RingBuf(/var/lib/mythtv/livetv/1000_20091116211716.mpg) Error: Invalid file descriptor in 'safe_read()'
2009-11-16 21:17:22.775 RingBuf(/var/lib/mythtv/livetv/1000_20091116211716.mpg) Error: Invalid file descriptor in 'safe_read()'

---

### Post by duker on 2009-11-16
Oops, I forgot to mention there are probably thousands of the ringbuf errors at at the end of the log file (I couldn't actually get to the end of them all or the end of the file.

---

