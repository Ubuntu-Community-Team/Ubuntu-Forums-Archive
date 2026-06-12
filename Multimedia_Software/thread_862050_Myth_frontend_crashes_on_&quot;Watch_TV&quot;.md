---
title: "Myth frontend crashes on &quot;Watch TV&quot;"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Hayesio on 2008-07-17
Hi Guys,

I'm setting up a mythbuntu box and having trouble getting tv to work.  I have a ASUS U3000 mini dongle and have configured it to work as instructed at mythtv.org.  I setup the mythbuntu backend and found all the local channel - so the backend seems ok.

The trouble is that when i start the frontend and sellect "Watch Tv", the screen goes black for about 5 seconds then the frontend crashes and i'm left looking at my desktop.

Here is the mythfrontend log:
```
Starting mythfrontend.real..
2008-07-17 19:53:08.799 New DB connection, total: 2
2008-07-17 19:53:08.802 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:53:08.814 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:53:08.815 Enabled verbose msgs:  important general
2008-07-17 19:53:09.262 Unable to parse themeinfo.xml for glass-wide
2008-07-17 19:53:09.263 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-17 19:53:09.871 Unable to parse themeinfo.xml for glass-wide
2008-07-17 19:53:09.872 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-17 19:53:11.491 Primary screen 0.
2008-07-17 19:53:11.492 Using screen 0, 800x600 at 0,0
2008-07-17 19:53:11.496 Switching to square mode (Mythbuntu-8.04)
2008-07-17 19:53:11.543 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-17 19:53:11.545 lirc_init failed for mythtv, see preceding messages
2008-07-17 19:53:11.548 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jack/.mythtv/joystickmenurc
2008-07-17 19:53:12.631 Specified base font 'medium' does not exist for font clock
2008-07-17 19:53:12.632 Specified base font 'medium' does not exist for font small
2008-07-17 19:53:12.632 Specified base font 'medium' does not exist for font medium
2008-07-17 19:53:12.632 Specified base font 'medium' does not exist for font large
2008-07-17 19:53:12.634 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-17 19:53:12.719 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-17 19:53:12.829 Registering Internal as a media playback plugin.
2008-07-17 19:53:12.964 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-07-17 19:53:13.282 MythMusic adding CD-Writer: 1,0,0 -- CD-224E         
2008-07-17 19:53:13.282 MythMusic adding CD-Writer: 2,0,0 -- DVD-ROM GDR8162B
2008-07-17 19:53:13.479 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.2:5060 NAT address 192.168.0.2
SIP: Cannot register; proxy, username or password not set
2008-07-17 19:53:23.755 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 19:53:23.756 Using protocol version 40
2008-07-17 19:53:23.791 TV: Attempting to change from None to WatchingLiveTV
2008-07-17 19:53:23.793 Using protocol version 40
2008-07-17 19:53:25.404 DPMS Deactivated 
2008-07-17 19:53:25.492 New DB connection, total: 3
2008-07-17 19:53:25.496 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:53:25.563 NVP: Disabling Audio, params(-1,2,44100)
```

...and thats it!

Does anybody know what the problem might be?

One other thing. The tv works fine in Metv, so the tuner is ok.

Any help would be greatly appreciated!

---

### Post by Hayesio on 2008-07-18
Ok, this is the backend log:
```
2008-07-18 18:23:02.622 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-18 18:23:02.735 Empty LocalHostName.
2008-07-18 18:23:02.797 Using localhost value of Media-Ubuntu
2008-07-18 18:23:03.163 New DB connection, total: 1
2008-07-18 18:23:03.325 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:23:03.341 Closing DB connection named 'DBManager0'
2008-07-18 18:23:03.351 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:23:03.528 New DB connection, total: 2
2008-07-18 18:23:03.604 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:23:03.644 Current Schema Version: 1214
Starting up as the master server.
2008-07-18 18:23:03.717 mythbackend: MythBackend started as master server
2008-07-18 18:23:03.791 New DB connection, total: 3
2008-07-18 18:23:03.794 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:23:04.473 New DB scheduler connection
2008-07-18 18:23:04.479 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:23:04.596 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-18 18:23:04.597 Main::Registering HttpStatus Extension
2008-07-18 18:23:04.598 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-18 18:23:04.599 Enabled verbose msgs:  important general
2008-07-18 18:23:04.721 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-18 18:23:07.512 Reschedule requested for id -1.
2008-07-18 18:23:08.067 Scheduled 0 items in 0.6 = 0.22 match + 0.33 place
2008-07-18 18:23:08.383 scheduler: Scheduled items: Scheduled 0 items in 0.6 = 0.22 match + 0.33 place
2008-07-18 18:23:08.423 Seem to be woken up by USER
2008-07-18 18:23:14.256 mythbackend: Running housekeeping thread
2008-07-18 18:24:24.687 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-18 18:24:25.317 Expiring 0 MBytes for 1001 @ Fri Jul 18 17:30:00 2008 => TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN "
2008-07-18 18:24:25.449 autoexpire: Expiring Program: Expiring 0 MBytes for 1001 @ Fri Jul 18 17:30:00 2008 => TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN "
2008-07-18 18:24:25.491 Expiring 0 MBytes for 1001 @ Fri Jul 18 17:30:00 2008 => TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN "
2008-07-18 18:24:39.279 New DB connection, total: 4
2008-07-18 18:24:41.488 New DB connection, total: 5
2008-07-18 18:24:41.552 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:24:41.578 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:27:51.574 MainServer::HandleAnnounce Monitor
2008-07-18 18:27:51.579 adding: Media-Ubuntu as a client (events: 0)
2008-07-18 18:27:51.582 MainServer::HandleAnnounce Monitor
2008-07-18 18:27:51.583 adding: Media-Ubuntu as a client (events: 1)
2008-07-18 18:27:51.710 MainServer::HandleAnnounce Playback
2008-07-18 18:27:51.765 adding: Media-Ubuntu as a client (events: 0)
2008-07-18 18:27:51.967 TVRec(2): Changing from None to WatchingLiveTV
2008-07-18 18:27:52.054 TVRec(2): HW Tuner: 2->2
2008-07-18 18:27:54.055 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-07-18 18:27:54.396 Finished recording TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN ": channel 1001
2008-07-18 18:27:54.941 scheduler: Finished recording: TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN ": channel 1001
2008-07-18 18:27:56.186 Finished recording TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN ": channel 1001
2008-07-18 18:27:56.820 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-07-18 18:27:57.015 TVRec(2): Changing from WatchingLiveTV to None
2008-07-18 18:27:58.217 Finished recording TEN News At Five "Comprehensive coverage of local stories that impact your lives. As well as big national and international news information. TEN ": channel 1001
2008-07-18 18:27:59.311 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-18 18:27:59.417 Empty LocalHostName.
2008-07-18 18:27:59.425 Using localhost value of Media-Ubuntu
2008-07-18 18:27:59.680 New DB connection, total: 1
2008-07-18 18:27:59.838 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:27:59.841 Closing DB connection named 'DBManager0'
2008-07-18 18:27:59.843 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:27:59.891 New DB connection, total: 2
2008-07-18 18:27:59.895 Connected to database 'mythconverg' at host: localhost
2008-07-18 18:27:59.949 Current Schema Version: 1214
2008-07-18 18:27:59.982 Preview Error: Previewer file '/var/lib/mythtv/recordings/1001_20080718182752.mpg' is not valid.
2008-07-18 18:27:59.986 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1001_20080718182752.mpg'
2008-07-18 18:28:00.120 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1001_20080718182752.mpg.png) exists: 0 readable: 0 size: 0
```

Any ideas? Really need some help here!

---

### Post by Hayesio on 2008-07-31
Ok. It seems the problem is a little more in depth.

Bit of an Update: 

I can get the programming guide and record programs.  The programs are recorded to /var/lib/mythtv/recordings along with a png image (presumably to present as a thumbnail).  I can play this recording with Totem.  When i try to play it from the myth frontend, the frontend crashes - the same as when i try to watch tv!  The frontend log produced when trying to play recordings is:
```
Starting mythfrontend.real..
2008-07-31 21:51:30.614 New DB connection, total: 2
2008-07-31 21:51:30.617 Connected to database 'mythconverg' at host: localhost
2008-07-31 21:51:30.624 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-31 21:51:30.625 Enabled verbose msgs:  important general
2008-07-31 21:51:31.361 Unable to parse themeinfo.xml for glass-wide
2008-07-31 21:51:31.362 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-31 21:51:32.197 Unable to parse themeinfo.xml for glass-wide
2008-07-31 21:51:32.203 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-31 21:51:34.352 Primary screen 0.
2008-07-31 21:51:34.356 Using screen 0, 800x600 at 0,0
2008-07-31 21:51:34.360 Switching to square mode (Mythbuntu-8.04)
2008-07-31 21:51:34.433 Using the Qt painter
2008-07-31 21:51:34.437 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jack/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-31 21:51:34.541 lirc_init failed for mythtv, see preceding messages
2008-07-31 21:51:38.206 Specified base font 'medium' does not exist for font clock
2008-07-31 21:51:38.206 Specified base font 'medium' does not exist for font small
2008-07-31 21:51:38.207 Specified base font 'medium' does not exist for font medium
2008-07-31 21:51:38.207 Specified base font 'medium' does not exist for font large
2008-07-31 21:51:38.223 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-31 21:51:38.422 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-31 21:51:38.722 Registering Internal as a media playback plugin.
2008-07-31 21:51:39.320 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-07-31 21:51:40.331 MythMusic adding CD-Writer: 1,0,0 -- CD-224E         
2008-07-31 21:51:40.349 MythMusic adding CD-Writer: 2,0,0 -- DVD-ROM GDR8162B
2008-07-31 21:51:40.507 Key Shift+Ctrl+?,Ctrl+Shift+? is bound to multiple actions in context Music.
2008-07-31 21:51:40.535 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.2:5060 NAT address 192.168.0.2
SIP: Cannot register; proxy, username or password not set
2008-07-31 21:51:41.115 Key Ctrl+? is already bound to a jump point.
2008-07-31 21:51:56.554 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-07-31 21:51:57.027 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-31 21:51:57.029 Using protocol version 40
2008-07-31 21:52:00.547 AFD: Opened codec 0x84c09b0, id(MPEG2VIDEO) type(Video)
2008-07-31 21:52:00.547 AFD: codec MP3 has 2 channels
2008-07-31 21:52:00.548 AFD: Opened codec 0x84c0ef0, id(MP3) type(Audio)
2008-07-31 21:52:00.548 AFD: codec AC3 has 2 channels
2008-07-31 21:52:00.568 AFD: Opened codec 0x84c1530, id(AC3) type(Audio)
2008-07-31 21:52:06.091 TV: Attempting to change from None to WatchingPreRecorded
2008-07-31 21:52:06.681 AFD: Opened codec 0x857b390, id(MPEG2VIDEO) type(Video)
2008-07-31 21:52:06.681 AFD: codec MP3 has 2 channels
2008-07-31 21:52:06.681 AFD: Opened codec 0x8658580, id(MP3) type(Audio)
2008-07-31 21:52:06.681 AFD: codec AC3 has 2 channels
2008-07-31 21:52:06.682 AFD: Opened codec 0x85e6d50, id(AC3) type(Audio)
2008-07-31 21:52:06.708 Opening audio device 'default'. ch 2(2) sr 48000
2008-07-31 21:52:06.716 Opening ALSA audio device 'default'.
2008-07-31 21:52:07.002 Opening audio device 'default'. ch 2(2) sr 48000
2008-07-31 21:52:07.003 Opening ALSA audio device 'default'.

```

The backend log is doing this:
```
/1002_20080724214035.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-31 21:59:41.128 mythbackend: Last message repeated 2 times: Delete Recording: File /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg does not exist for chanid 1002 at Thu Jul 24 21:40:35 2008 when trying to delete recording.
2008-07-31 21:59:41.140 mythbackend: Running housekeeping thread
2008-07-31 22:00:35.437 Expiring 0 MBytes for 1002 @ Thu Jul 24 21:32:00 2008 => Q And A
2008-07-31 22:00:35.445 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-31 22:00:35.456 mythbackend: Delete Recording: File /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg does not exist for chanid 1002 at Thu Jul 24 21:40:35 2008 when trying to delete recording.
2008-07-31 22:02:35.447 Expiring 0 MBytes for 1002 @ Thu Jul 24 21:32:00 2008 => Q And A
2008-07-31 22:02:35.458 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-31 22:04:35.457 Expiring 0 MBytes for 1002 @ Thu Jul 24 21:32:00 2008 => Q And A
2008-07-31 22:04:35.466 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-31 22:04:43.154 mythbackend: Last message repeated 2 times: Delete Recording: File /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg does not exist for chanid 1002 at Thu Jul 24 21:40:35 2008 when trying to delete recording.
2008-07-31 22:04:43.193 mythbackend: Running housekeeping thread
2008-07-31 22:05:35.495 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-31 22:05:35.503 Expiring 0 MBytes for 1002 @ Thu Jul 24 21:32:00 2008 => Q And A
2008-07-31 22:05:35.514 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-31 22:05:35.523 mythbackend: Delete Recording: File /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Media-Ubuntu/1002_20080724214035.mpg does not exist for chanid 1002 at Thu Jul 24 21:40:35 2008 when trying to delete recording.
```

Has anyone got any suggestions? Or any advise on how to better troubleshoot the problem?

---

### Post by Hayesio on 2008-07-31
This is a snippet from running strace -o /output mythfrontend:
```
eep({0, 100000000}, NULL)         = 0
ioctl(5, FIONREAD, [0])                 = 0
write(6, "\0", 1)                       = 1
gettimeofday({1217506780, 328534}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 328673}, NULL) = 0
select(22, [3 4 5 7 21], [], [], {0, 0}) = 1 (in [5], left {0, 0})
read(5, "\0", 1)                        = 1
gettimeofday({1217506780, 328859}, NULL) = 0
gettimeofday({1217506780, 328937}, NULL) = 0
gettimeofday({1217506780, 328980}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 329084}, NULL) = 0
select(22, [3 4 5 7 21], [], [], {0, 0}) = 0 (Timeout)
gettimeofday({1217506780, 329188}, NULL) = 0
nanosleep({0, 100000000}, NULL)         = 0
ioctl(5, FIONREAD, [1])                 = 0
gettimeofday({1217506780, 429440}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 429577}, NULL) = 0
select(27, [3 4 5 7 21 26], [], [], {0, 0}) = 1 (in [5], left {0, 0})
read(5, "\0", 1)                        = 1
gettimeofday({1217506780, 429772}, NULL) = 0
gettimeofday({1217506780, 429849}, NULL) = 0
gettimeofday({1217506780, 429894}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 430001}, NULL) = 0
select(27, [3 4 5 7 21 26], [], [], {0, 0}) = 0 (Timeout)
gettimeofday({1217506780, 430165}, NULL) = 0
nanosleep({0, 100000000}, NULL)         = 0
ioctl(5, FIONREAD, [0])                 = 0
write(6, "\0", 1)                       = 1
gettimeofday({1217506780, 530496}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 530632}, NULL) = 0
select(27, [3 4 5 7 21 26], [], [], {0, 0}) = 1 (in [5], left {0, 0})
read(5, "\0", 1)                        = 1
gettimeofday({1217506780, 530822}, NULL) = 0
gettimeofday({1217506780, 530898}, NULL) = 0
gettimeofday({1217506780, 530943}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 531049}, NULL) = 0
select(27, [3 4 5 7 21 26], [], [], {0, 0}) = 0 (Timeout)
gettimeofday({1217506780, 531157}, NULL) = 0
nanosleep({0, 100000000}, NULL)         = 0
ioctl(5, FIONREAD, [0])                 = 0
write(6, "\0", 1)                       = 1
gettimeofday({1217506780, 631484}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 631620}, NULL) = 0
select(27, [3 4 5 7 21 26], [], [], {0, 0}) = 1 (in [5], left {0, 0})
read(5, "\0", 1)                        = 1
gettimeofday({1217506780, 631812}, NULL) = 0
gettimeofday({1217506780, 631893}, NULL) = 0
gettimeofday({1217506780, 631937}, NULL) = 0
read(3, 0x82861d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1217506780, 632042}, NULL) = 0
select(27, [3 4 5 7 21 26], [], [], {0, 0}) = 0 (Timeout)
gettimeofday({1217506780, 632149}, NULL) = 0
nanosleep({0, 100000000}, 0)            = ? ERESTART_RESTARTBLOCK (To be restarted)
+++ killed by SIGSEGV +++
```

---

### Post by wyliecoyoteuk on 2008-08-04
I am pretty new to MythTV, but I think that the 3 errors you have highlighted are to do with the lirc deamon not being able to find the /home/username/lircd.rc file, and are unrelated to the TV issue.


The TV problem is further down in the log. What does it say after "TV: attempting to change from none to watching LiveTV "?

Edit: most common cause is wrong permissions on the /share/lib/mythtv folder
are you in the mythtv group?
Does mythtv have read/write access to that folder?

---

### Post by Hayesio on 2008-08-11
Well, i made a fresh install from the Mythbuntu cd and everything is working fine.  

I was never able to figure out what was causing this problem, despite spending weeks on it!

---

### Post by epidemiks on 2008-08-14
> **Hayesio said:**
> Well, i made a fresh install from the Mythbuntu cd and everything is working fine.  

I was never able to figure out what was causing this problem, despite spending weeks on it!

This is good news!

---

