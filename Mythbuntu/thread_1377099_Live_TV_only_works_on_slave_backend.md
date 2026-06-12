---
title: "Live TV only works on slave backend"
date: 2010-01-09
forum: Mythbuntu
---

### Post by whein on 2010-01-09
So this is weird.  I have two Myth(buntu) boxes as follows:
Box 1 (Primary Backend)
pcHDTV 5500 tuner card connected to an antenna for DTV over the air

Box 2 (Secondary Backend)
Hauppauge PVR-150 connected to an analog cable signal from Comcast
Hauppauge PVR-150 connected to an analog cable signal from Comcast
Hauppauge PVR-350 connected to an analog cable signal from Comcast

Due to repeated corruption in databases, I uninstalled and reinstalled MythTV, mysql, and anything that looked even remotely related.  Clean slate or as close as I could get without wiping the entire Ubuntu install.  Everything seemed to go OK until I went to go watch LiveTV on box 1.  It keeps flashing to the "Please Wait..." screen and then dumping me back to the menu.  Even weirder is that box 2 can watch LiveTV without a problem.  I thought it was a tuner problem, but box 2 can watch any channel on any tuner including the pcHDTV that is on box 1 without a problem.  Box 1 gets nothing.

Logs from the Mythbuntu log grabber are appended below and it seems the key sections are:

```
==> /var/log/mythtv/mythbackend.log <==
2010-01-09 21:37:10.686 MainServer::ANN Playback
2010-01-09 21:37:10.689 adding: HappyDrive02 as a client (events: 0)
2010-01-09 21:37:10.694 MainServer::HandleAnnounce FileTransfer
2010-01-09 21:37:10.699 adding: HappyDrive02 as a remote file transfer
2010-01-09 21:37:15.534 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(74,9223372036854775807,#4) out of 10
2010-01-09 21:37:15.598 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(74,9223372036854775807,#4) out of 10
2010-01-09 21:37:21.999 TVRec(1): Changing from Watching WatchingLiveTV to None
2010-01-09 21:37:22.003 Recording designated 1080i/p because width was 1920
2010-01-09 21:37:22.359 Finished recording Legend of the Seeker: channel 1191
2010-01-09 21:37:33.737 MainServer::ANN Playback
2010-01-09 21:37:33.739 adding: HappyDrive03 as a client (events: 0)
2010-01-09 21:37:33.743 Should be local only query: SpawnLiveTV

==> /var/log/mythtv/mythfrontend.log <==
2010-01-09 21:33:28.399 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-09 21:33:28.401 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-09 21:33:28.402 Using protocol version 50
2010-01-09 21:33:28.406 Spawning LiveTV Recorder -- begin
2010-01-09 21:33:28.415 Spawning LiveTV Recorder -- end
2010-01-09 21:33:28.416 GetEntryAt(-1) failed.
2010-01-09 21:33:28.417 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-01-09 21:33:28.418 TV Error: HandleStateChange(): LiveTV not successfully started
2010-01-09 21:33:28.418 We have a RingBuffer
2010-01-09 21:33:28.468 TV Error: LiveTV not successfully started
```

Two other questions while I'm here.  I seem to recall you used to be able to change how channels were displayed, e.g. 2_1 or 2-1 or 2.1 but I can't seem to find the screen for choosing this.  Does it still exist and if so where?  Also, I thought you could change the priority of the various tuners so that for example you could have the PVR-350 take preference over the PVR-150 to record a show even if they both had the same channel available.  Same thing for channel priorities, setting 4_1 (DTV) to have priority over 4 (analog cable).  Where are the setup screens for these?


Complete logs from Mythbunbtu log grabber:
```
==> /var/log/mythtv/jamu.log <==

! Warning - Creating an instance caused and error for one of: MythTV, MythVideo or MythDB


-----Scheduled & Recorded Statistics-------
Number of Scheduled & Recorded ......(    2)
Number of Fanart graphics found .....(    0)
Number of Poster graphics found .....(    0)
Number of Banner graphics found .....(    0)
Number of Fanart graphics downloaded (    1)
Number of Poster graphics downloaded (    2)
Number of Banner graphics downloaded (    0)
Number of Miro TV Shows ............ (    0)
Number of Miro Movie Trailers ...... (    0)

-------------Scheduled & Recorded----------
Ghost Whisperer
Unknown (0000)

==> /var/log/mythtv/mtd.log <==
mtd started at Sat Jan 9 21:08:18 2010
mtd is running on a host called HappyDrive03
21:08:18: Waiting for connections/jobs
21:08:18: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2010-01-09 21:29:37.237 MainServer, Warning: Unknown socket closing MythSocket(0x8d69870)
2010-01-09 21:29:37.240 MainServer, Warning: Unknown socket closing MythSocket(0x8db7940)
2010-01-09 21:29:37.243 MythSocket(8db7940:-1): writeStringList: Error, socket went unconnected.
			We wrote 0 of 10 bytes with 1 errors
2010-01-09 21:32:22.989 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-09 21:32:22.992 Using runtime prefix = /usr
2010-01-09 21:32:22.994 Using configuration directory = /home/mythtv/.mythtv
2010-01-09 21:32:22.996 Empty LocalHostName.
2010-01-09 21:32:22.998 Using localhost value of HappyDrive03
2010-01-09 21:32:23.000 Testing network connectivity to '192.168.0.3'
2010-01-09 21:32:23.010 New DB connection, total: 1
2010-01-09 21:32:23.033 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:32:23.035 Closing DB connection named 'DBManager0'
2010-01-09 21:32:23.039 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:32:23.043 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-09 21:32:23.056 MythBackend: Starting up as the master server.
2010-01-09 21:32:23.061 New DB connection, total: 2
2010-01-09 21:32:23.066 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:32:23.085 New DB connection, total: 3
2010-01-09 21:32:23.088 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:32:23.150 New DB scheduler connection
2010-01-09 21:32:23.152 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:32:23.181 Enabling Upnpmedia rebuild thread.
2010-01-09 21:32:24.640 Main::Registering HttpStatus Extension
2010-01-09 21:32:24.642 Enabled verbose msgs:  important general
2010-01-09 21:32:24.647 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-09 21:32:25.346 adding: HappyDrive02 as a slave backend server
2010-01-09 21:32:26.167 Reschedule requested for id -1.
2010-01-09 21:32:26.532 Scheduled 114 items in 0.4 = 0.02 match + 0.34 place
2010-01-09 21:32:26.537 Seem to be woken up by USER
2010-01-09 21:32:31.362 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-09 21:32:33.184 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-01-09 21:32:43.164 Expiring 11 MBytes for 2002 @ Sat Jan 9 21:00:00 2010 => NUMB3RS "Cover Me"
2010-01-09 21:32:43.167 Expiring 0 MBytes for 1021 @ Sat Jan 9 21:00:00 2010 => NUMB3RS
2010-01-09 21:33:03.016 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-09 21:33:03.026 Using runtime prefix = /usr
2010-01-09 21:33:03.036 Using configuration directory = /home/mythtv/.mythtv
2010-01-09 21:33:03.061 Empty LocalHostName.
2010-01-09 21:33:03.083 Using localhost value of HappyDrive03
2010-01-09 21:33:03.086 Testing network connectivity to '192.168.0.3'
2010-01-09 21:33:03.097 New DB connection, total: 1
2010-01-09 21:33:03.108 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:03.111 Closing DB connection named 'DBManager0'
2010-01-09 21:33:03.115 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:03.131 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-09 21:33:03.135 MythBackend: Starting up as the master server.
2010-01-09 21:33:03.140 New DB connection, total: 2
2010-01-09 21:33:03.142 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:03.151 New DB connection, total: 3
2010-01-09 21:33:03.156 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:03.242 New DB scheduler connection
2010-01-09 21:33:03.244 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:03.274 Enabling Upnpmedia rebuild thread.
2010-01-09 21:33:04.735 Main::Registering HttpStatus Extension
2010-01-09 21:33:04.736 Enabled verbose msgs:  important general
2010-01-09 21:33:04.741 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-09 21:33:05.279 adding: HappyDrive02 as a slave backend server
2010-01-09 21:33:06.253 Reschedule requested for id -1.
2010-01-09 21:33:06.555 Scheduled 114 items in 0.3 = 0.01 match + 0.28 place
2010-01-09 21:33:06.560 Seem to be woken up by USER
2010-01-09 21:33:11.290 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-09 21:33:13.278 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-01-09 21:33:25.488 MainServer::ANN Monitor
2010-01-09 21:33:25.490 adding: HappyDrive03 as a client (events: 0)
2010-01-09 21:33:25.492 MainServer::ANN Monitor
2010-01-09 21:33:25.497 adding: HappyDrive03 as a client (events: 1)
2010-01-09 21:33:28.402 MainServer::ANN Playback
2010-01-09 21:33:28.404 adding: HappyDrive03 as a client (events: 0)
2010-01-09 21:33:28.408 Should be local only query: SpawnLiveTV
2010-01-09 21:34:23.276 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-01-09 21:35:33.223 Reschedule requested for id -1.
2010-01-09 21:35:33.503 Scheduled 114 items in 0.3 = 0.01 match + 0.26 place
2010-01-09 21:36:44.319 MainServer::ANN Monitor
2010-01-09 21:36:44.321 adding: HappyDrive02 as a client (events: 0)
2010-01-09 21:36:44.323 MainServer::ANN Monitor
2010-01-09 21:36:44.326 adding: HappyDrive02 as a client (events: 1)
2010-01-09 21:36:47.734 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-01-09 21:37:01.276 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-01-09 21:37:01.282 MainServer::ANN Monitor
2010-01-09 21:37:01.286 adding: tzcheck as a client (events: 0)
2010-01-09 21:37:09.057 MainServer::ANN Playback
2010-01-09 21:37:09.059 adding: HappyDrive02 as a client (events: 0)
2010-01-09 21:37:09.064 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-01-09 21:37:09.076 TVRec(1): HW Tuner: 1->1
2010-01-09 21:37:09.579 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-01-09 21:37:10.545 Finished recording Legend of the Seeker: channel 1191
2010-01-09 21:37:10.589 Finished recording Legend of the Seeker: channel 1191
2010-01-09 21:37:10.671 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-01-09 21:37:10.686 MainServer::ANN Playback
2010-01-09 21:37:10.689 adding: HappyDrive02 as a client (events: 0)
2010-01-09 21:37:10.694 MainServer::HandleAnnounce FileTransfer
2010-01-09 21:37:10.699 adding: HappyDrive02 as a remote file transfer
2010-01-09 21:37:15.534 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(74,9223372036854775807,#4) out of 10
2010-01-09 21:37:15.598 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(74,9223372036854775807,#4) out of 10
2010-01-09 21:37:21.999 TVRec(1): Changing from Watching WatchingLiveTV to None
2010-01-09 21:37:22.003 Recording designated 1080i/p because width was 1920
2010-01-09 21:37:22.359 Finished recording Legend of the Seeker: channel 1191
2010-01-09 21:37:33.737 MainServer::ANN Playback
2010-01-09 21:37:33.739 adding: HappyDrive03 as a client (events: 0)
2010-01-09 21:37:33.743 Should be local only query: SpawnLiveTV

==> /var/log/mythtv/mythfrontend.log <==
2010-01-09 21:26:37.442 New DB connection, total: 3
2010-01-09 21:26:37.445 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:26:37.450 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:26:37.652 Desktop video mode: 1024x768 60.006 Hz
2010-01-09 21:26:37.840 Registering Internal as a media playback plugin.
2010-01-09 21:26:37.865 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 21:26:37.869 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 21:26:37.872 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 21:26:37.879 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-01-09 21:26:38.003 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2010-01-09 21:26:38.007 Found mainmenu.xml for theme 'MythCenter'
2010-01-09 21:26:38.300 MythContext: Connecting to backend server: 192.168.0.3:6543 (try 1 of 1)
2010-01-09 21:26:38.301 Using protocol version 50
2010-01-09 21:26:40.401 Loading menu theme from /usr/share/mythtv/themes/classic//tvmenu.xml
2010-01-09 21:26:41.124 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-09 21:26:41.126 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-09 21:26:41.133 Using protocol version 50
2010-01-09 21:26:41.137 Spawning LiveTV Recorder -- begin
2010-01-09 21:26:41.140 Spawning LiveTV Recorder -- end
2010-01-09 21:26:41.142 GetEntryAt(-1) failed.
2010-01-09 21:26:41.143 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-01-09 21:26:41.143 TV Error: HandleStateChange(): LiveTV not successfully started
2010-01-09 21:26:41.144 We have a RingBuffer
2010-01-09 21:26:41.194 TV Error: LiveTV not successfully started
2010-01-09 21:26:41.218 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-09 21:26:41.219 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-09 21:26:59.170 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
Starting mythfrontend.real..
2010-01-09 21:33:23.535 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-09 21:33:23.536 Using runtime prefix = /usr
2010-01-09 21:33:23.536 Using configuration directory = /home/whein/.mythtv
2010-01-09 21:33:24.228 Empty LocalHostName.
2010-01-09 21:33:24.228 Using localhost value of HappyDrive03
2010-01-09 21:33:24.229 Testing network connectivity to '192.168.0.3'
2010-01-09 21:33:24.248 New DB connection, total: 1
2010-01-09 21:33:24.255 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:24.256 Closing DB connection named 'DBManager0'
2010-01-09 21:33:24.279 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-09 21:33:24.281 DPMS is active.
2010-01-09 21:33:24.284 Primary screen: 0.
2010-01-09 21:33:24.285 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:24.287 Using screen 0, 1024x768 at 0,0
2010-01-09 21:33:24.314 MythUI Image Cache size set to 20971520 bytes
2010-01-09 21:33:24.315 Enabled verbose msgs:  important general
2010-01-09 21:33:24.324 Primary screen: 0.
2010-01-09 21:33:24.325 Using screen 0, 1024x768 at 0,0
2010-01-09 21:33:24.327 Using theme base resolution of 800x600
2010-01-09 21:33:24.341 LIRC: Successfully initialized '/dev/lircd' using '/home/whein/.mythtv/lircrc' config
2010-01-09 21:33:24.342 JoystickMenuThread Error: Joystick disabled - Failed to read /home/whein/.mythtv/joystickmenurc
2010-01-09 21:33:24.554 Using the Qt painter
2010-01-09 21:33:24.557 Loaded base theme from /usr/share/mythtv/themes/MythCenter/base.xml
2010-01-09 21:33:24.669 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-09 21:33:24.672 New DB connection, total: 2
2010-01-09 21:33:24.673 New DB connection, total: 3
2010-01-09 21:33:24.674 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-09 21:33:24.690 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:24.725 Connected to database 'mythconverg' at host: 192.168.0.3
2010-01-09 21:33:24.884 Desktop video mode: 1024x768 60.006 Hz
2010-01-09 21:33:25.055 Registering Internal as a media playback plugin.
2010-01-09 21:33:25.080 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-09 21:33:25.084 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-09 21:33:25.087 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-09 21:33:25.095 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-01-09 21:33:25.178 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2010-01-09 21:33:25.181 Found mainmenu.xml for theme 'MythCenter'
2010-01-09 21:33:25.487 MythContext: Connecting to backend server: 192.168.0.3:6543 (try 1 of 1)
2010-01-09 21:33:25.488 Using protocol version 50
2010-01-09 21:33:27.629 Loading menu theme from /usr/share/mythtv/themes/classic//tvmenu.xml
2010-01-09 21:33:28.399 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-09 21:33:28.401 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-09 21:33:28.402 Using protocol version 50
2010-01-09 21:33:28.406 Spawning LiveTV Recorder -- begin
2010-01-09 21:33:28.415 Spawning LiveTV Recorder -- end
2010-01-09 21:33:28.416 GetEntryAt(-1) failed.
2010-01-09 21:33:28.417 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-01-09 21:33:28.418 TV Error: HandleStateChange(): LiveTV not successfully started
2010-01-09 21:33:28.418 We have a RingBuffer
2010-01-09 21:33:28.468 TV Error: LiveTV not successfully started
2010-01-09 21:33:28.491 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-09 21:33:28.493 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-09 21:37:33.733 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-09 21:37:33.735 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-09 21:37:33.736 Using protocol version 50
2010-01-09 21:37:33.741 Spawning LiveTV Recorder -- begin
2010-01-09 21:37:33.746 Spawning LiveTV Recorder -- end
2010-01-09 21:37:33.748 GetEntryAt(-1) failed.
2010-01-09 21:37:33.749 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-01-09 21:37:33.750 TV Error: HandleStateChange(): LiveTV not successfully started
2010-01-09 21:37:33.750 We have a RingBuffer
2010-01-09 21:37:33.800 TV Error: LiveTV not successfully started
2010-01-09 21:37:33.822 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-09 21:37:33.822 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-09 21:37:43.176 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Jan  9 21:07:40 HappyDrive03 init: apport post-stop process (1230) terminated with status 1
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187214] nvidia 0000:00:12.0: enabling device (0000 -> 0002)
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187516] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187521] nvidia 0000:00:12.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187527] nvidia 0000:00:12.0: setting latency timer to 64
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187991] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187995]   alloc irq_desc for 16 on node -1
Jan  9 21:07:40 HappyDrive03 kernel: [   21.187997]   alloc kstat_irqs on node -1
Jan  9 21:07:40 HappyDrive03 kernel: [   21.188006] nvidia 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
Jan  9 21:07:40 HappyDrive03 kernel: [   21.188010] nvidia 0000:02:00.0: setting latency timer to 64
Jan  9 21:07:40 HappyDrive03 kernel: [   21.188214] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
Jan  9 21:07:40 HappyDrive03 acpid: client connected from 1536[114:122]
Jan  9 21:07:40 HappyDrive03 avahi-daemon[912]: Server startup complete. Host name is HappyDrive03.local. Local service cookie is 70015915.
Jan  9 21:07:40 HappyDrive03 gdm-binary[1425]: WARNING: Unable to find users: no seat-id found
Jan  9 21:07:40 HappyDrive03 acpid: client connected from 1617[0:0]
Jan  9 21:07:40 HappyDrive03 ntpd[1132]: Listening on interface #6 eth0, fe80::250:8dff:feb6:a38#123 Enabled
Jan  9 21:07:41 HappyDrive03 mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Jan  9 21:07:41 HappyDrive03 mysqld: 100109 21:07:41 [Note] Plugin 'FEDERATED' is disabled.
Jan  9 21:07:44 HappyDrive03 mysqld: 100109 21:07:44  InnoDB: Started; log sequence number 0 76530
Jan  9 21:07:44 HappyDrive03 mysqld: 100109 21:07:44 [Note] Event Scheduler: Loaded 0 events
Jan  9 21:07:44 HappyDrive03 mysqld: 100109 21:07:44 [Note] /usr/sbin/mysqld: ready for connections.
Jan  9 21:07:44 HappyDrive03 mysqld: Version: '5.1.37-1ubuntu5'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Jan  9 21:07:44 HappyDrive03 acpid: client connected from 1617[0:0]
Jan  9 21:07:45 HappyDrive03 init: mythtv-backend main process (876) terminated with status 254
Jan  9 21:07:45 HappyDrive03 init: mythtv-backend main process ended, respawning
Jan  9 21:07:45 HappyDrive03 kernel: [   26.591998] __ratelimit: 15 callbacks suppressed
Jan  9 21:07:45 HappyDrive03 kernel: [   26.592001] type=1503 audit(1263089265.512:28): operation="open" pid=1893 parent=1892 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  9 21:07:45 HappyDrive03 kernel: [   26.646760] type=1503 audit(1263089265.568:29): operation="open" pid=1904 parent=1903 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan  9 21:07:45 HappyDrive03 /etc/mysql/debian-start[1916]: Upgrading MySQL tables if necessary.
Jan  9 21:07:45 HappyDrive03 /etc/mysql/debian-start[1919]: Looking for 'mysql' as: /usr/bin/mysql
Jan  9 21:07:45 HappyDrive03 /etc/mysql/debian-start[1919]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan  9 21:07:45 HappyDrive03 /etc/mysql/debian-start[1919]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Jan  9 21:07:45 HappyDrive03 /etc/mysql/debian-start[1934]: Checking for insecure root accounts.
Jan  9 21:07:45 HappyDrive03 /etc/mysql/debian-start[1938]: Triggering myisam-recover for all MyISAM tables
Jan  9 21:07:45 HappyDrive03 kernel: [   26.830144] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan  9 21:07:45 HappyDrive03 kernel: [   26.837515] NFSD: starting 90-second grace period
Jan  9 21:07:45 HappyDrive03 console-kit-daemon[931]: WARNING: Couldn't read /proc/919/environ: Failed to open file '/proc/919/environ': No such file or directory
Jan  9 21:07:46 HappyDrive03 gnome-session[2046]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:46 HappyDrive03 gnome-session[2046]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jan  9 21:07:46 HappyDrive03 gnome-session[2046]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jan  9 21:07:46 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:46 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:46 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:47 HappyDrive03 /sbin/upsd: main: v2.6 startup complete
Jan  9 21:07:47 HappyDrive03 kernel: [   28.223673] ppdev: user-space parallel port driver
Jan  9 21:07:47 HappyDrive03 kernel: [   28.480079] bttv: driver version 0.9.18 loaded
Jan  9 21:07:47 HappyDrive03 kernel: [   28.480083] bttv: using 8 buffers with 2080k (520 pages) each for capture
Jan  9 21:07:47 HappyDrive03 kernel: [   28.490147] ivtv: Start initialization, version 1.4.1
Jan  9 21:07:47 HappyDrive03 kernel: [   28.490186] ivtv: End initialization
Jan  9 21:07:47 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:47 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:47 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:47 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:47 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:47 HappyDrive03 gdm-simple-greeter[2095]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:07:49 HappyDrive03 kernel: [   30.504010] eth0: no IPv6 routers present
Jan  9 21:08:17 HappyDrive03 /sbin/upsd: log: UPS_ERROR
Jan  9 21:08:22 HappyDrive03 acpid: client 1617[0:0] has disconnected
Jan  9 21:08:22 HappyDrive03 acpid: client 1617[0:0] has disconnected
Jan  9 21:08:22 HappyDrive03 acpid: client connected from 2556[0:0]
Jan  9 21:08:23 HappyDrive03 acpid: client connected from 2556[0:0]
Jan  9 21:08:24 HappyDrive03 gnome-session[2594]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gnome-session[2594]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jan  9 21:08:24 HappyDrive03 gnome-session[2594]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:24 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:08:47 HappyDrive03 kernel: [   89.000025] Clocksource tsc unstable (delta = -149815554 ns)
Jan  9 21:09:02 HappyDrive03 CRON[2943]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  9 21:11:58 HappyDrive03 ntpd[1132]: synchronized to 91.189.94.4, stratum 2
Jan  9 21:11:58 HappyDrive03 ntpd[1132]: kernel time sync status change 2001
Jan  9 21:12:37 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:12:37 HappyDrive03 gdm-simple-greeter[2606]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan  9 21:13:36 HappyDrive03 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  9 21:13:36 HappyDrive03 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  9 21:13:38 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:14:00 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:15:54 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:16:29 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:17:01 HappyDrive03 CRON[3680]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  9 21:20:48 HappyDrive03 init: mythtv-backend main process (1871) terminated with status 255
Jan  9 21:20:49 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:21:26 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:21:45 HappyDrive03 init: mythtv-backend main process (3756) terminated with status 255
Jan  9 21:21:45 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:25:32 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:26:37 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:26:59 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:30:30 HappyDrive03 init: mythtv-backend main process (3845) terminated with status 255
Jan  9 21:30:31 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:32:22 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:32:59 HappyDrive03 init: mythtv-backend main process (4016) terminated with status 255
Jan  9 21:32:59 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:33:02 HappyDrive03 lircd-0.8.6[1036]: removed client
Jan  9 21:33:24 HappyDrive03 lircd-0.8.6[1036]: accepted new client on /var/run/lirc/lircd
Jan  9 21:37:43 HappyDrive03 lircd-0.8.6[1036]: removed client

==> /var/log/Xorg.0.log <==
(--) NVIDIA(GPU-1):     at PCI:0:18:0:
(--) NVIDIA(GPU-1):     CRT-0
(--) NVIDIA(GPU-1): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1024x768+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
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
(II) Initializing extension GLX
(II) config/hal: Adding input device HOLTEK Wireless TackBall Keyboard(2.4G)
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) HOLTEK Wireless TackBall Keyboard(2.4G): always reports core events
(**) HOLTEK Wireless TackBall Keyboard(2.4G): Device: "/dev/input/event4"
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Found 8 mouse buttons
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Found x and y relative axes
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Found scroll wheel(s)
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Found keys
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Configuring as mouse
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Configuring as keyboard
(**) HOLTEK Wireless TackBall Keyboard(2.4G): YAxisMapping: buttons 4 and 5
(**) HOLTEK Wireless TackBall Keyboard(2.4G): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HOLTEK Wireless TackBall Keyboard(2.4G)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) HOLTEK Wireless TackBall Keyboard(2.4G): (accel) keeping acceleration scheme 1
(**) HOLTEK Wireless TackBall Keyboard(2.4G): (accel) filter chain progression: 2.00
(**) HOLTEK Wireless TackBall Keyboard(2.4G): (accel) filter stage 0: 20.00 ms
(**) HOLTEK Wireless TackBall Keyboard(2.4G): (accel) set acceleration profile 0
(II) HOLTEK Wireless TackBall Keyboard(2.4G): initialized for relative axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device HOLTEK Wireless TackBall Keyboard(2.4G)
(**) HOLTEK Wireless TackBall Keyboard(2.4G): always reports core events
(**) HOLTEK Wireless TackBall Keyboard(2.4G): Device: "/dev/input/event3"
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Found keys
(II) HOLTEK Wireless TackBall Keyboard(2.4G): Configuring as keyboard
(II) XINPUT: Adding extended input device "HOLTEK Wireless TackBall Keyboard(2.4G)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.

==> /home/whein/.xsession-errors <==
xfdesktop[3411] is already running; assuming --reload
xfdesktop[3410] is already running; assuming --reload
xfdesktop[3410]: starting up
xfdesktop[3411]: starting up
Failed to init the UI: Unknown option --sm-config-prefix
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

(polkit-gnome-authentication-agent-1:3422): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3422): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
2010-01-09 21:13:37.127 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
** (nm-applet:3440): DEBUG: foo_client_state_changed_cb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
** (gdmsetup:3556): DEBUG: init delay=30
** (gdmsetup:3556): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:3556): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:3556): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:3556): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3556): DEBUG: adding monitor for '/home/whein/.face'
** (gdmsetup:3556): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:3556): DEBUG: Found 1 sessions for user whein
** (gdmsetup:3556): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session4
** (gdmsetup:3556): DEBUG: GdmUserManager: sessions changed user=whein num=1
** (gdmsetup:3556): DEBUG: GdmUserManager: added session for user: whein
** (gdmsetup:3556): DEBUG: GdmUserManager: history output: whein    77

** (gdmsetup:3556): DEBUG: init user='whein' auto=True
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2010-01-09 21:15:53.212 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/patches': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 3756
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 3845
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2010-01-09 21:26:36.312 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/patches': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 4016

(xfce4-terminal:4049): Terminal-WARNING **: Unable to load terminal preferences.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2010-01-09 21:33:23.498 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             458G  277G  158G  64% /
udev                  880M  268K  880M   1% /dev
none                  880M     0  880M   0% /dev/shm
none                  880M  344K  880M   1% /var/run
none                  880M     0  880M   0% /var/lock
none                  880M     0  880M   0% /lib/init/rw
192.168.0.1:/home/whein/Pictures
                      197G   42G  145G  23% /mnt/192.168.0.1/Pictures
192.168.0.1:/home/whein/Music
                      197G   42G  145G  23% /mnt/192.168.0.1/Music
192.168.0.1:/home/whein/Videos
                      197G   42G  145G  23% /mnt/192.168.0.1/Videos

==> uname -a <==
Linux HappyDrive03 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:09.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:09.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)

==> lsusb <==
Bus 004 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1241:f768 Belkin 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/patches <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 44
DeviceFileMode: 432
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RmNvclkIdleGraphics: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
GCC version:  gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

==> /proc/driver/nvidia/warnings <==
==> /proc/driver/nvidia/cards/0 <==
Model: 		 GeForce 7050 PV / nForce 630a
IRQ:   		 20
Video BIOS: 	 05.67.32.24.03
Card Type: 	 PCI
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 00.12.0

==> /proc/driver/nvidia/cards/1 <==
Model: 		 GeForce 7300 SE/7200 GS
IRQ:   		 16
Video BIOS: 	 05.72.22.81.00
Card Type: 	 PCI-E
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 02.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1759MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: 15.11.2
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02d000-fe02dfff
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02c000-fe02c0ff
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:fe020000-fe023fff
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
          resources: ioport:c000(size=4096) memory:ec000000-efffffff memory:fd300000-fd3fffff(prefetchable)
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=68 maxlatency=4 mingnt=2
             resources: irq:19 memory:effff000-effff7ff memory:efff8000-efffbfff
        *-multimedia:0
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=cx8800 latency=20 maxlatency=55 mingnt=20
             resources: irq:17 memory:ee000000-eeffffff
        *-multimedia:1
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
             vendor: Conexant Systems, Inc.
             physical id: 9.2
             bus info: pci@0000:01:09.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6
             resources: irq:17 memory:ed000000-edffffff
        *-multimedia:2 UNCLAIMED
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [IR Port]
             vendor: Conexant Systems, Inc.
             physical id: 9.4
             bus info: pci@0000:01:09.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=6 maxlatency=255 mingnt=6
             resources: memory:ec000000-ecffffff
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:31 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fe026000-fe027fff
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: [REMOVED]
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=[REMOVED] latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:32 memory:fe02b000-fe02bfff ioport:d800(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:b000(size=4096) memory:fa000000-fcffffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G72 [GeForce 7300 SE/7200 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:fb000000-fbffffff memory:fc000000-fc01ffff(prefetchable)
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:a000(size=4096) memory:fdf00000-fdffffff ioport:fde00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26 ioport:9000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-pci:4
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:27 ioport:8000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)
     *-pci:5
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:28 ioport:7000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
     *-pci:6
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:29 ioport:6000(size=4096) memory:fd700000-fd7fffff ioport:fd600000(size=1048576)
     *-pci:7
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 11
          bus info: pci@0000:00:11.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:30 ioport:5000(size=4096) memory:fd500000-fd5fffff ioport:fd400000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C68 [GeForce 7050 PV / nForce 630a]
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:20 memory:f9000000-f9ffffff memory:c0000000-cfffffff(prefetchable) memory:f8000000-f8ffffff memory:80000000-8001ffff(prefetchable)
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

```

---

### Post by singedwings on 2010-01-12
You are getting the "2010-01-09 21:33:28.416 GetEntryAt(-1) failed" in your mythfrontend.log.

This is usually a permissions error. Have you changed the default storage directories in the backend? If you have myth probably does not have permission to write to the new directory.

---

### Post by dannyboy79 on 2010-04-13
your frontend.log shows this: MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
that's not good since your backend is at 192.168.0.3

---

