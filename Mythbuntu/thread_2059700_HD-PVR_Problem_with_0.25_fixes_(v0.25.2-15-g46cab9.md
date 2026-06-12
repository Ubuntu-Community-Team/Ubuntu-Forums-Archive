---
title: "HD-PVR Problem with 0.25 fixes (v0.25.2-15-g46cab93) - database issue?"
date: 2012-09-18
forum: Mythbuntu
---

### Post by yonkiman on 2012-09-18
Finally got around to upgrading Myth system from 10.10 / 0.24 to 12.04 / 0.25.  cx88 tuner works fine, but can't record programs or watch live TV with HD-PVR.

Device is recognized:
[INDENT]$ dmesg | grep video
[    0.241023] pci 0000:01:00.0: Boot video device
[   11.331169] Linux video capture interface: v2.00
[   11.610292] hdpvr 1-5:1.0: device now attached to video0
[   11.764201] cx88[0]/0: registered device video1 [v4l2]
$[/INDENT]

And I can even record and playback video outside MythTV:
[INDENT]/dev/video0 > test.ts[/INDENT]
generates a working, VLC-viewable video file.

Even got the ole 6200ch recompiled and tested that it works as well.

But whenever I try the HD-PVR with Myth, I just get a black screen (Watch TV) or "no file" (when it tries to record something).  

Couldn't find any new/updated log files in /var/log/mythtv, but I did capture everything it spit out after launching mythfrontend -v

```
$ sudo mythfrontend -v
QGtkStyle was unable to detect the current GTK+ theme.
2012-09-17 22:53:30.990626 C  mythfrontend version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
2012-09-17 22:53:30.990652 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-09-17 22:53:30.990656 N  Enabled verbose msgs:  general
2012-09-17 22:53:30.990681 N  Setting Log Level to LOG_INFO
2012-09-17 22:53:30.990727 I  Added logging to the console
2012-09-17 22:53:30.990752 I  Added syslogging to facility local7
2012-09-17 22:53:30.990758 I  Added database logging to table logging
2012-09-17 22:53:30.990852 N  Setting up SIGHUP handler
2012-09-17 22:53:30.990915 N  Using runtime prefix = /usr
2012-09-17 22:53:30.990926 N  Using configuration directory = /home/fred/.mythtv
2012-09-17 22:53:30.991059 I  Assumed character encoding: en_US.UTF-8
2012-09-17 22:53:30.991498 N  Empty LocalHostName.
2012-09-17 22:53:30.991504 I  Using localhost value of mythpc
2012-09-17 22:53:30.991637 I  Testing network connectivity to '192.168.1.100'
2012-09-17 22:53:30.993423 I  Starting process manager
2012-09-17 22:53:30.995448 I  Starting process signal handler
2012-09-17 22:53:30.995544 I  Starting IO manager (write)
2012-09-17 22:53:30.997123 I  Starting IO manager (read)
2012-09-17 22:53:31.119474 N  Setting QT default locale to en_US
2012-09-17 22:53:31.119545 I  Current locale en_US
2012-09-17 22:53:31.119584 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-09-17 22:53:31.197695 I  ScreenSaverX11Private: XScreenSaver support enabled
2012-09-17 22:53:31.203641 I  ScreenSaverX11Private: DPMS is disabled.
2012-09-17 22:53:31.214374 N  Desktop video mode: 1280x720 60.016 Hz
2012-09-17 22:53:31.234783 I  Listening on TCP 127.0.0.1:6547
2012-09-17 22:53:31.234862 I  Listening on TCP 192.168.1.100:6547
2012-09-17 22:53:31.253022 I  Listening on TCP [::1]:6547
2012-09-17 22:53:31.253127 I  Listening on TCP [fe80::21c:c0ff:fe79:8313%eth1]:6547
2012-09-17 22:53:31.957923 I  RAOP Device: Created RAOP device objects.
2012-09-17 22:53:31.959779 I  Loading en_us translation for module mythfrontend
2012-09-17 22:53:31.960111 I  Listening on TCP 127.0.0.1:5000
2012-09-17 22:53:31.960163 I  Listening on TCP 192.168.1.100:5000
2012-09-17 22:53:31.965452 I  LIRC: Successfully initialized '/dev/lircd' using '/home/fred/.mythtv/lircrc' config
2012-09-17 22:53:31.965553 E  JoystickMenuThread: Joystick disabled - Failed to read /home/fred/.mythtv/joystickmenurc
2012-09-17 22:53:31.979438 I  Listening on TCP [::1]:5000
2012-09-17 22:53:31.979537 I  Listening on TCP [fe80::21c:c0ff:fe79:8313%eth1]:5000
2012-09-17 22:53:31.979570 I  RAOP Device: Listening for connections on port 5000
2012-09-17 22:53:31.979609 I  Registering service 224a595f5357@MythTV on mythpc._raop._tcp port 5000 TXT tp=UDsm=falssv=falseek=1et=0,1cn=0,1ch=2ss=1sr=4410pw=falsevn=3    txtvers=md=0,1,2    vs=130.14da=true
2012-09-17 22:53:31.993285 E  CECAdapter: Failed to find any CEC devices.
2012-09-17 22:53:31.993374 I  CECAdapter: Closing down CEC.
2012-09-17 22:53:31.996166 I  Binding to UDP 127.0.0.1:6948
2012-09-17 22:53:31.996216 I  Binding to UDP 192.168.1.100:6948
2012-09-17 22:53:32.004910 I  Binding to UDP [::1]:6948
2012-09-17 22:53:32.005006 I  Binding to UDP [fe80::21c:c0ff:fe79:8313%eth1]:6948
2012-09-17 22:53:32.005069 I  Binding to UDP 192.168.1.255:6948
2012-09-17 22:53:32.049190 I  Using Frameless Window
2012-09-17 22:53:32.133461 I  Using the Qt painter
2012-09-17 22:53:32.381323 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-09-17 22:53:32.730914 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-09-17 22:53:32.730927 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-09-17 22:53:32.731465 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-09-17 22:53:32.731473 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-09-17 22:53:32.832059 I  Bonjour: Service registration complete: name '224a595f5357@MythTV on mythpc' type '_raop._tcp.' domain: 'local.'
2012-09-17 22:53:32.839389 N  Registering Internal as a media playback plugin.
2012-09-17 22:53:32.878613 I  Loading en_us translation for module mythgallery
2012-09-17 22:53:32.882838 I  Current MythMusic Schema Version (MusicDBSchemaVer): 1019
2012-09-17 22:53:32.892982 I  Loading en_us translation for module mythmusic
2012-09-17 22:53:32.893955 I  Listening on TCP 127.0.0.1:6546
2012-09-17 22:53:32.894004 I  Listening on TCP 192.168.1.100:6546
2012-09-17 22:53:32.896186 I  Listening on TCP [::1]:6546
2012-09-17 22:53:32.896266 I  Listening on TCP [fe80::21c:c0ff:fe79:8313%eth1]:6546
2012-09-17 22:53:32.934897 N  Found mainmenu.xml for theme 'Mythbuntu'
2012-09-17 22:53:32.985348 I  MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2012-09-17 22:53:32.989517 I  Using protocol version 72
2012-09-17 22:53:33.032129 I  Bonjour: Service registration complete: name 'Mythfrontend on mythpc' type '_mythfrontend._tcp.' domain: 'local.'
2012-09-17 22:53:38.028696 I  TV: Creating TV object
2012-09-17 22:53:38.039131 N  Resuming idle timer
2012-09-17 22:53:38.039180 N  Suspending idle timer
2012-09-17 22:53:38.041335 I  TV: Created TvPlayWindow.
2012-09-17 22:53:38.056448 I  TV: Attempting to change from None to WatchingLiveTV
2012-09-17 22:53:38.056475 I  MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2012-09-17 22:53:38.056982 I  Using protocol version 72
2012-09-17 22:53:38.062654 N  TV: Spawning LiveTV Recorder -- begin
2012-09-17 22:53:38.494594 N  TV: Spawning LiveTV Recorder -- end
2012-09-17 22:53:38.497757 I  TV: playbackURL(/media/disk0/mythtv/livetv/1221_20120917225338.mpg) cardtype(DUMMY)
2012-09-17 22:53:38.608503 N  AudioPlayer: Enabling Audio
2012-09-17 22:53:38.640630 I  VDPAU: Created 2 output surfaces.
2012-09-17 22:53:38.640661 I  VDPAU: Version 1
2012-09-17 22:53:38.640668 I  VDPAU: Information NVIDIA VDPAU Driver Shared Library  295.40  Thu Apr  5 22:02:06 PDT 2012
2012-09-17 22:53:38.640679 I  VDPAU: Created VDPAU render device 1280x720
2012-09-17 22:53:38.689556 I  Player(0): Video timing method: RTC
2012-09-17 22:53:38.690107 I  TV: Created player.
2012-09-17 22:53:38.690135 I  TV: Changing from None to WatchingLiveTV
2012-09-17 22:53:38.690143 I  TV: State is LiveTV & mctx == ctx
2012-09-17 22:53:38.691286 I  TV: UpdateOSDInput done
2012-09-17 22:53:38.691298 I  TV: UpdateLCD done
2012-09-17 22:53:38.691513 I  TV: ITVRestart done
2012-09-17 22:53:38.698284 I  TV: Main UI disabled.
2012-09-17 22:53:38.698299 I  Using Idle Timer. 61 minutes
2012-09-17 22:53:38.698593 I  TV: Entering main playback loop.
2012-09-17 22:53:38.753991 I  VDPAU: Added 2 output surfaces (total 4, max 4)
2012-09-17 22:53:41.843617 I  VDPAU Painter: Clearing VDPAU painter cache.
2012-09-17 22:53:41.909152 I  VDPAU: Created 2 output surfaces.
2012-09-17 22:53:41.909169 I  VDPAU: Created VDPAU render device 1280x720
2012-09-17 22:53:41.965104 N  Player(0): Forcing decode extra audio option on (Video method requires it).
2012-09-17 22:53:41.965240 I  AFD: Opened codec 0x51b6c50, id(MPEG2VIDEO) type(Video)
2012-09-17 22:53:41.965248 I  AFD: codec AC3 has 2 channels
2012-09-17 22:53:41.965511 I  AFD: Opened codec 0x519e1c0, id(AC3) type(Audio)
2012-09-17 22:53:41.965532 I  AFD: codec AC3 has 2 channels
2012-09-17 22:53:41.965771 I  AFD: Opened codec 0x51d2840, id(AC3) type(Audio)
2012-09-17 22:53:42.201486 I  AO: Opening audio device 'iec958:CARD=Intel,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-09-17 22:53:42.202724 E  ALSA: Setting hardware audio buffer size to 128
2012-09-17 22:53:42.204473 E  Error preparing query: SELECT recordedmarkup.data FROM recordedmarkup WHERE recordedmarkup.chanid    = :CHANID    AND       recordedmarkup.starttime = :STARTTIME AND       recordedmarkup.type      = 33 GROUP BY recordedmarkup.data ORDER BY SUM( ( SELECT IFNULL(rm.mark, recordedmarkup.mark)                FROM recordedmarkup AS rm                 WHERE rm.chanid    = recordedmarkup.chanid    AND                       rm.starttime = recordedmarkup.starttime AND                       rm.type      = recordedmarkup.type      AND                       rm.mark      > recordedmarkup.mark                 ORDER BY rm.mark ASC LIMIT 1               ) - recordedmarkup.mark             ) DESC LIMIT 1
2012-09-17 22:53:42.204487 E  Driver error was [2/1054]:
QMYSQL3: Unable to prepare statement
Database error was:
Unknown column 'recordedmarkup.data' in 'field list'

2012-09-17 22:53:42.204662 E  DB Error (load_markup_datum):
Query was:
SELECT recordedmarkup.data FROM recordedmarkup WHERE recordedmarkup.chanid    = :CHANID    AND       recordedmarkup.starttime = :STARTTIME AND       recordedmarkup.type      = 33 GROUP BY recordedmarkup.data ORDER BY SUM( ( SELECT IFNULL(rm.mark, recordedmarkup.mark)                FROM recordedmarkup AS rm                 WHERE rm.chanid    = recordedmarkup.chanid    AND                       rm.starttime = recordedmarkup.starttime AND                       rm.type      = recordedmarkup.type      AND                       rm.mark      > recordedmarkup.mark                 ORDER BY rm.mark ASC LIMIT 1               ) - recordedmarkup.mark             ) DESC LIMIT 1
Bindings were:
:CHANID=1221, :STARTTIME=2012-09-17T22:53:39
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID    AND       recordedmarkup.starttime = :STARTTIME AND       recordedmar' at line 1

2012-09-17 22:53:42.204834 E  Error preparing query: SELECT recordedmarkup.data FROM recordedmarkup WHERE recordedmarkup.chanid    = :CHANID    AND       recordedmarkup.starttime = :STARTTIME AND       recordedmarkup.type      = 34 GROUP BY recordedmarkup.data ORDER BY SUM( ( SELECT IFNULL(rm.mark, recordedmarkup.mark)                FROM recordedmarkup AS rm                 WHERE rm.chanid    = recordedmarkup.chanid    AND                       rm.starttime = recordedmarkup.starttime AND                       rm.type      = recordedmarkup.type      AND                       rm.mark      > recordedmarkup.mark                 ORDER BY rm.mark ASC LIMIT 1               ) - recordedmarkup.mark             ) DESC LIMIT 1
2012-09-17 22:53:42.204843 E  Driver error was [2/1054]:
QMYSQL3: Unable to prepare statement
Database error was:
Unknown column 'recordedmarkup.data' in 'field list'

2012-09-17 22:53:42.204965 E  DB Error (load_markup_datum):
Query was:
SELECT recordedmarkup.data FROM recordedmarkup WHERE recordedmarkup.chanid    = :CHANID    AND       recordedmarkup.starttime = :STARTTIME AND       recordedmarkup.type      = 34 GROUP BY recordedmarkup.data ORDER BY SUM( ( SELECT IFNULL(rm.mark, recordedmarkup.mark)                FROM recordedmarkup AS rm                 WHERE rm.chanid    = recordedmarkup.chanid    AND                       rm.starttime = recordedmarkup.starttime AND                       rm.type      = recordedmarkup.type      AND                       rm.mark      > recordedmarkup.mark                 ORDER BY rm.mark ASC LIMIT 1               ) - recordedmarkup.mark             ) DESC LIMIT 1
Bindings were:
:CHANID=1221, :STARTTIME=2012-09-17T22:53:39
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID    AND       recordedmarkup.starttime = :STARTTIME AND       recordedmar' at line 1

2012-09-17 22:53:42.208901 N  AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-09-17 22:53:42.541936 I  VDPAU: Added 2 output surfaces (total 4, max 4)
2012-09-17 22:53:42.875378 N  Player(0): Waited 102ms for video buffers AAAAAAAAAADddL
2012-09-17 22:53:42.977413 N  Player(0): Waited 204ms for video buffers AAAAAAAAAADddL
2012-09-17 22:53:43.079776 N  Player(0): Waited 306ms for video buffers AAAAAAAAAADddL
2012-09-17 22:53:43.182108 N  Player(0): Waited 409ms for video buffers ULAAAAAAAADDDL
2012-09-17 22:53:46.676484 E  MythUIHelper: LoadScaleImage(uparrow_alt.png)Unable to find image file
2012-09-17 22:53:46.676564 E  MythUIHelper: LoadScaleImage(downarrow_alt.png)Unable to find image file
2012-09-17 22:53:51.716856 I  VDPAU Painter: Clearing VDPAU painter cache.
2012-09-17 22:53:51.719458 W  MythPainter: 1 images not yet de-allocated.
2012-09-17 22:53:52.204551 I  MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2012-09-17 22:53:52.204975 I  Using protocol version 72
$
```

Any suggestions where to look next?  Looking at the log file above I wonder if something's not misconfigured in my database (I imported and upgraded it from 10.10).  I'm very mysql illiterate - hope it might be obvious to someone who isn't.

Cheers,
Fred

---

### Post by nickrout on 2012-09-18
I suggest you take this to the mailing list, the main database gurus don't hang out here, they do on the users mailing list.

---

