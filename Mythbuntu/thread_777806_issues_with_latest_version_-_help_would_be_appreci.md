---
title: "issues with latest version - help would be appreciated"
date: 2008-05-01
forum: Mythbuntu
---

### Post by callagga on 2008-05-01
Hi - I would love to help/advice re the following issues I see.  These are the logs after rebooting and then watching live tv on one channel, change to another channel, and then escape.  There was no sound.  TV picture was not too bad, however I had to change previously to CPU-- mode (as in the normal mode it was jerky - due to "VideoOutputXv Error: XvMC output requested, but is not supported by display.Xlib" - refer to [http://ubuntuforums.org/showpost.php?p=4851151&postcount=8](http://ubuntuforums.org/showpost.php?p=4851151&postcount=8)).

BACKEND
```
/home/greg
greg@mythtv:~$ cd /var/log/mythtv/
greg@mythtv:/var/log/mythtv$ vi gregsnotes.txt 
greg@mythtv:/var/log/mythtv$ cat gregsnotes.txt 
2008-05-02 06:09:40.979 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-02 06:09:41.162 Empty LocalHostName.
2008-05-02 06:09:41.236 Using localhost value of mythtv
2008-05-02 06:09:41.454 New DB connection, total: 1
2008-05-02 06:09:41.488 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:09:41.744 Closing DB connection named 'DBManager0'
2008-05-02 06:09:41.825 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:09:41.838 New DB connection, total: 2
2008-05-02 06:09:41.839 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:09:41.889 Current Schema Version: 1214
Starting up as the master server.
2008-05-02 06:09:42.185 New DB connection, total: 3
2008-05-02 06:09:42.282 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:09:42.397 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-05-02 06:09:42.563 New DB scheduler connection
2008-05-02 06:09:42.741 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-05-02 06:09:43.074 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-02 06:09:43.075 Main::Registering HttpStatus Extension
2008-05-02 06:09:43.076 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-05-02 06:09:43.077 Enabled verbose msgs:  important general
2008-05-02 06:09:43.131 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-02 06:09:46.003 Reschedule requested for id -1.
2008-05-02 06:09:46.158 Scheduled 0 items in 0.2 = 0.01 match + 0.14 place
2008-05-02 06:09:46.355 Seem to be woken up by USER
2008-05-02 06:11:03.004 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-02 06:14:27.637 MainServer::HandleAnnounce Monitor
2008-05-02 06:14:27.645 adding: mythtv as a client (events: 0)
2008-05-02 06:14:27.738 MainServer::HandleAnnounce Monitor
2008-05-02 06:14:27.739 adding: mythtv as a client (events: 1)
2008-05-02 06:14:30.758 MainServer::HandleAnnounce Playback
2008-05-02 06:14:30.772 adding: mythtv as a client (events: 0)
2008-05-02 06:14:30.840 TVRec(1): Changing from None to WatchingLiveTV
2008-05-02 06:14:30.953 TVRec(1): HW Tuner: 1->1
[B]2008-05-02 06:14:30.965 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-05-02 06:14:32.314 DVBSM(0), Warning: Can not measure Bit Error Rate
			eno: Operation not supported (95)
2008-05-02 06:14:32.317 DVBSM(0), Warning: Can not count Uncorrected Blocks
			eno: Operation not supported (95)
2008-05-02 06:14:32.517 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min[/B]
2008-05-02 06:14:33.159 Finished recording Unknown: channel 2012
2008-05-02 06:14:34.260 Finished recording Unknown: channel 2012
**2008-05-02 06:14:34.714 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min**
2008-05-02 06:14:34.740 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-02 06:14:35.277 Empty LocalHostName.
2008-05-02 06:14:35.285 Using localhost value of mythtv
2008-05-02 06:14:35.476 New DB connection, total: 1
2008-05-02 06:14:35.587 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:14:35.588 Closing DB connection named 'DBManager0'
2008-05-02 06:14:35.590 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:14:35.592 New DB connection, total: 2
2008-05-02 06:14:35.593 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:14:35.597 Current Schema Version: 1214
[B]2008-05-02 06:14:35.610 Preview Error: Previewer file '/var/lib/mythtv/recordings/2012_20080502061431.mpg' is not valid.
2008-05-02 06:14:35.615 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2012_20080502061431.mpg'
2008-05-02 06:14:36.629 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings[/B]/2012_20080502061431.mpg.png) exists: 0 readable: 0 size: 0
2008-05-02 06:15:33.453 TVRec(1): HW Tuner: 1->1
2008-05-02 06:15:33.609 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-05-02 06:15:35.451 Finished recording Unknown: channel 2012
[B]2008-05-02 06:15:36.086 DVBSM(0), Warning: Can not measure Bit Error Rate
			eno: Operation not supported (95)
2008-05-02 06:15:36.404 DVBSM(0), Warning: Can not count Uncorrected Blocks
			eno: Operation not supported (95)[/B]
2008-05-02 06:15:36.651 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
[B]2008-05-02 06:15:36.735 DTVSM(0) Error: Wrong PMT; pmt->pn(1025) desired(1152)
2008-05-02 06:15:37.558 DTVSM(0) Error: Wrong PMT; pmt->pn(1030) desired(1152)[/B]
2008-05-02 06:15:38.193 Finished recording Unknown: channel 2090
2008-05-02 06:15:39.190 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-02 06:15:39.213 Empty LocalHostName.
2008-05-02 06:15:39.217 Using localhost value of mythtv
2008-05-02 06:15:39.425 New DB connection, total: 1
2008-05-02 06:15:39.474 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:15:39.478 Closing DB connection named 'DBManager0'
2008-05-02 06:15:39.480 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:15:39.534 Finished recording Unknown: channel 2090
2008-05-02 06:15:39.594 New DB connection, total: 2
2008-05-02 06:15:39.729 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:15:39.739 Current Schema Version: 1214
2008-05-02 06:15:39.808 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-02 06:15:39.856 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-02 06:15:39.962 Empty LocalHostName.
2008-05-02 06:15:40.017 Using localhost value of mythtv
2008-05-02 06:15:40.042 New DB connection, total: 1
2008-05-02 06:15:40.067 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:15:40.072 Closing DB connection named 'DBManager0'
2008-05-02 06:15:40.076 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:15:40.088 New DB connection, total: 2
2008-05-02 06:15:40.094 Connected to database 'mythconverg' at host: localhost
2008-05-02 06:15:40.099 Current Schema Version: 1214
[B]2008-05-02 06:15:40.124 Preview Error: Previewer file '/var/lib/mythtv/recordings/2090_20080502061533.mpg' is not valid.
2008-05-02 06:15:40.132 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2090_20080502061533.mpg'
2008-05-02 06:15:40.660 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/2090_20080502061533.mpg.png) exists: 0 readable: 0 size: 0[/B]
2008-05-02 06:15:42.919 AFD: Opened codec 0x82a87e0, id(MPEG2VIDEO) type(Video)
2008-05-02 06:15:42.940 AFD: codec AC3 has 2 channels
2008-05-02 06:15:42.942 AFD: Opened codec 0x82a8dd0, id(AC3) type(Audio)
[B]2008-05-02 06:15:45.456 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(5839)
2008-05-02 06:15:50.433 TFW, Error: Write() -- IOBOUND end
2008-05-02 06:15:51.031 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(3207)
2008-05-02 06:15:51.235 TFW, Error: Write() -- IOBOUND end
2008-05-02 06:15:51.965 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(6967)
2008-05-02 06:15:52.440 TFW, Error: Write() -- IOBOUND end
2008-05-02 06:15:52.951 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(1515)
2008-05-02 06:15:54.424 TFW, Error: Write() -- IOBOUND end
2008-05-02 06:15:54.621 Preview: Grabbed preview '/var/lib/mythtv/recordings/2012_20080502061433.mpg' 1920x1088@64s[/B]
2008-05-02 06:16:03.410 Expiring 0 MBytes for 2012 @ Fri May 2 06:14:30 2008 => Unknown
2008-05-02 06:16:06.046 TVRec(1): Changing from WatchingLiveTV to None
2008-05-02 06:16:06.508 Finished recording Unknown: channel 2090
2008-05-02 06:18:03.422 Expiring 111 MBytes for 2012 @ Fri May 2 06:14:33 2008 => Unknown
2008-05-02 06:18:03.426 Expiring 0 MBytes for 2090 @ Fri May 2 06:15:33 2008 => Unknown
2008-05-02 06:18:03.430 Expiring 42 MBytes for 2090 @ Fri May 2 06:15:38 2008 => Unknown


```

FRONTEND
```
(g[B]ksudo:17572): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[/B]
(gksudo:17572): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17572): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17572): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17572): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:17572): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]mythbuntu-control-centre: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
 theme engine in module_path: "pixmap",
mythfrontend.real: Fatal IO error: client killed[/B]
Starting mythfrontend.real..
2008-05-02 06:09:57.407 New DB connection, total: 2
2008-05-02 06:09:57.408 Connected to database 'mythconverg' at host: 127.0.0.1
2008-05-02 06:09:57.410 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-02 06:09:57.411 Enabled verbose msgs:  important general
2008-05-02 06:09:59.836 Primary screen 0.
2008-05-02 06:09:59.837 Using screen 0, 1152x864 at 0,0
2008-05-02 06:09:59.838 Switching to square mode (Mythbuntu)
2008-05-02 06:09:59.987 Using the Qt painter
[B]mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-02 06:09:59.988 lirc_init failed for mythtv, see preceding messages[/B]
2008-05-02 06:09:59.988 JoystickMenuClient Error: Joystick disabled - Failed to read /home/greg/.mythtv/joystickmenurc
2008-05-02 06:10:01.659 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-05-02 06:10:01.969 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-02 06:10:02.101 Registering Internal as a media playback plugin.
2008-05-02 06:10:02.329 MonitorRegisterExtensions(0x100, gif,jpg,png)
[B]2008-05-02 06:10:02.897 Failed to run 'cdrecord --scanbus'
2008-05-02 06:10:02.900 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-02 06:10:02.903 Failed to run 'cdrecord --scanbus -dev=ATAPI'[/B]
2008-05-02 06:10:02.954 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-05-02 06:10:03.300 MythThemedMenuPrivate: Unknown tag image in background
2008-05-02 06:14:27.616 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-02 06:14:27.637 Using protocol version 40
2008-05-02 06:14:28.579 MythThemedMenuPrivate: Unknown tag image in background
2008-05-02 06:14:30.757 TV: Attempting to change from None to WatchingLiveTV
2008-05-02 06:14:30.758 Using protocol version 40
2008-05-02 06:14:32.579 DPMS Deactivated 
2008-05-02 06:14:32.711 New DB connection, total: 3
2008-05-02 06:14:32.711 Connected to database 'mythconverg' at host: 127.0.0.1
2008-05-02 06:14:32.748 NVP: Disabling Audio, params(-1,2,44100)
2008-05-02 06:14:32.852 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-05-02 06:14:32.857 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-05-02 06:14:32.997 OSD Theme Dimensions W: 640 H: 480
2008-05-02 06:14:33.602 TV: Changing from None to WatchingLiveTV
2008-05-02 06:14:33.606 Realtime priority would require SUID as root.
2008-05-02 06:14:33.611 FilterManager: failed to load filter 'none', no such filter exists
**2008-05-02 06:14:33.611 Couldn't load deinterlace filter none**
[B]2008-05-02 06:14:36.635 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext[/B]
2008-05-02 06:14:36.673 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-05-02 06:14:36.677 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-05-02 06:14:37.017 Video timing method: USleep with busy wait
2008-05-02 06:14:42.920 AFD: Opened codec 0xb3c1d260, id(MPEG2VIDEO) type(Video)
2008-05-02 06:14:43.005 AFD: codec AC3 has 2 channels
2008-05-02 06:14:43.163 AFD: Opened codec 0xb3c24bb0, id(AC3) type(Audio)
2008-05-02 06:14:45.070 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-02 06:14:45.221 Opening ALSA audio device 'default'.
2008-05-02 06:14:45.824 NVP: Prebuffer wait timed out 10 times.
[B]2008-05-02 06:14:46.353 Mixer unable to find control Master
2008-05-02 06:14:46.353 Mixer unable to find control Master
2008-05-02 06:14:46.361 Mixer unable to find control PCM
2008-05-02 06:14:46.361 Mixer unable to find control PCM
2008-05-02 06:14:46.361 Mixer unable to find control PCM[/B]
2008-05-02 06:14:46.363 NVP: Enabling Audio
2008-05-02 06:14:47.744 NVP: Prebuffer wait timed out 10 times.
2008-05-02 06:14:50.093 NVP: prebuffering pause
2008-05-02 06:15:33.092 Mixer unable to find control PCM
2008-05-02 06:15:33.115 Mixer unable to find control PCM
2008-05-02 06:15:34.288 NVP: prebuffering pause
2008-05-02 06:15:36.416 NVP: Prebuffer wait timed out 10 times.
2008-05-02 06:15:37.762 New DB connection, total: 4
2008-05-02 06:15:38.316 Connected to database 'mythconverg' at host: 127.0.0.1
2008-05-02 06:15:38.430 Mixer unable to find control PCM
2008-05-02 06:15:38.430 Mixer unable to find control PCM
2008-05-02 06:15:41.183 NVP: Prebuffer wait timed out 10 times.
[B]2008-05-02 06:15:41.504 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".[/B]
2008-05-02 06:15:41.504 AFD: Opened codec 0x8347d60, id(MPEG2VIDEO) type(Video)
2008-05-02 06:15:41.505 AFD: codec AC3 has 6 channels
2008-05-02 06:15:41.505 AFD: Opened codec 0x83480e0, id(AC3) type(Audio)
2008-05-02 06:15:44.887 NVP: prebuffering pause
2008-05-02 06:15:45.133 WriteAudio: buffer underrun
[B]2008-05-02 06:15:46.603 NVP: Prebuffer wait timed out 10 times.
2008-05-02 06:15:48.204 NVP: Prebuffer wait timed out 10 times.
2008-05-02 06:15:49.766 WriteAudio: buffer underrun
2008-05-02 06:15:50.282 WriteAudio: buffer underrun
2008-05-02 06:15:50.531 WriteAudio: buffer underrun[/B]
2008-05-02 06:15:51.480 NVP: prebuffering pause
2008-05-02 06:15:52.864 WriteAudio: buffer underrun
2008-05-02 06:15:53.153 WriteAudio: buffer underrun
2008-05-02 06:15:53.581 WriteAudio: buffer underrun
2008-05-02 06:15:53.806 WriteAudio: buffer underrun
2008-05-02 06:15:54.298 WriteAudio: buffer underrun
2008-05-02 06:16:05.929 TV: Attempting to change from WatchingLiveTV to None
2008-05-02 06:16:07.425 TV: Changing from WatchingLiveTV to None
2008-05-02 06:16:07.576 DPMS Reactivated.

(gksudo:5926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5926): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

