---
title: "Myth 8.10 x64 watch tv issue"
date: 2009-02-06
forum: Mythbuntu
---

### Post by zf3636 on 2009-02-06
Hello i have installed and configured my mythbackend and created default recording directories with read and write permisions , when i run mythfrontend i press watch tv i get no visible display and it just returns back to the main menu, my wintv 150 pvr card is working I have used this card with 8.10 i386 just recently with no problems.

---

### Post by tgm4883 on 2009-02-06
post your backend log from /var/log/mythtv/mythbackend.log

---

### Post by zf3636 on 2009-02-06
Hello tgm4883 this install is on a new pc TA690G AM2 motherboard this is my log

mtd started at Fri Feb 6 18:08:26 2009
mtd is running on a host called goldrock-desktop
18:08:26: Waiting for connections/jobs
18:08:26: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-02-06 17:36:47.919 Using runtime prefix = /usr
2009-02-06 17:36:47.960 Empty LocalHostName.
2009-02-06 17:36:47.961 Using localhost value of goldrock-desktop
2009-02-06 17:36:47.980 New DB connection, total: 1
2009-02-06 17:36:47.984 Connected to database 'mythconverg' at host: localhost
2009-02-06 17:36:47.985 Closing DB connection named 'DBManager0'
2009-02-06 17:36:47.988 Connected to database 'mythconverg' at host: localhost
2009-02-06 17:36:47.993 New DB connection, total: 2
2009-02-06 17:36:47.996 Connected to database 'mythconverg' at host: localhost
2009-02-06 17:36:48.001 Current Schema Version: 1214
Starting up as the master server.
2009-02-06 17:36:48.012 New DB connection, total: 3
2009-02-06 17:36:48.014 Connected to database 'mythconverg' at host: localhost
2009-02-06 17:36:48.020 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-02-06 17:36:48.021 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-02-06 17:36:48.130 New DB scheduler connection
2009-02-06 17:36:48.134 Connected to database 'mythconverg' at host: localhost
2009-02-06 17:36:48.148 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-02-06 17:36:48.148 Main::Registering HttpStatus Extension
2009-02-06 17:36:48.156 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-02-06 17:36:48.163 Enabled verbose msgs:  important general
2009-02-06 17:36:48.173 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 17:36:51.141 Reschedule requested for id -1.
2009-02-06 17:36:51.163 Scheduled 1 items in 0.0 = 0.01 match + 0.01 place
2009-02-06 17:36:51.166 Seem to be woken up by USER
2009-02-06 17:37:32.366 MainServer::HandleAnnounce Monitor
2009-02-06 17:37:32.368 adding: goldrock-desktop as a client (events: 0)
2009-02-06 17:37:32.369 MainServer::HandleAnnounce Monitor
2009-02-06 17:37:32.369 adding: goldrock-desktop as a client (events: 1)
2009-02-06 17:37:32.372 Reschedule requested for id -1.
2009-02-06 17:37:32.398 Scheduled 1 items in 0.0 = 0.01 match + 0.01 place
2009-02-06 17:37:55.559 MainServer::HandleAnnounce Monitor
2009-02-06 17:37:55.564 adding: goldrock-desktop as a client (events: 0)
2009-02-06 17:37:55.565 MainServer::HandleAnnounce Monitor
2009-02-06 17:37:55.565 adding: goldrock-desktop as a client (events: 1)
2009-02-06 17:37:55.571 MainServer::HandleAnnounce Playback
2009-02-06 17:37:55.572 adding: goldrock-desktop as a client (events: 0)
2009-02-06 17:37:55.576 TVRec(1): Changing from None to WatchingLiveTV
2009-02-06 17:37:55.581 TVRec(1): HW Tuner: 1->1
2009-02-06 17:37:55.587 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-02-06 17:37:55.588 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-02-06 17:37:55.592 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-02-06 17:37:55.596 TVRec(1): Changing from WatchingLiveTV to None
2009-02-06 17:38:08.142 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 18:04:02.756 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 18:04:02.876 TVRec(1): ASK_RECORDING 1 0 0 0
2009-02-06 18:07:58.331 Using runtime prefix = /usr
2009-02-06 18:07:58.464 Empty LocalHostName.
2009-02-06 18:07:58.632 Using localhost value of goldrock-desktop
2009-02-06 18:07:58.717 New DB connection, total: 1
2009-02-06 18:07:58.796 Connected to database 'mythconverg' at host: localhost
2009-02-06 18:07:58.838 Closing DB connection named 'DBManager0'
2009-02-06 18:07:59.034 Connected to database 'mythconverg' at host: localhost
2009-02-06 18:07:59.037 New DB connection, total: 2
2009-02-06 18:07:59.171 Connected to database 'mythconverg' at host: localhost
2009-02-06 18:07:59.479 Current Schema Version: 1214
Starting up as the master server.
2009-02-06 18:08:01.158 New DB connection, total: 3
2009-02-06 18:08:01.163 Connected to database 'mythconverg' at host: localhost
2009-02-06 18:08:01.234 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-02-06 18:08:01.236 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-02-06 18:08:01.306 New DB scheduler connection
2009-02-06 18:08:01.329 Connected to database 'mythconverg' at host: localhost
2009-02-06 18:08:01.404 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-02-06 18:08:01.408 Main::Registering HttpStatus Extension
2009-02-06 18:08:01.411 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-02-06 18:08:01.413 Enabled verbose msgs:  important general
2009-02-06 18:08:01.443 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 18:08:04.364 Reschedule requested for id -1.
2009-02-06 18:08:05.192 Scheduled 1 items in 0.8 = 0.74 match + 0.09 place
2009-02-06 18:08:05.219 AUTO-Startup assumed
2009-02-06 18:08:05.228 TVRec(1): ASK_RECORDING 1 0 0 0
2009-02-06 18:08:05.485 TVRec(1): Changing from None to RecordingOnly
2009-02-06 18:08:05.491 TVRec(1): HW Tuner: 1->1
2009-02-06 18:08:05.497 Channel(/dev/video0) Error: GetCurrentChannelNum(4): Failed to find Channel
2009-02-06 18:08:05.532 Channel(/dev/video0)::TuneTo(4): Error, failed to find channel.
2009-02-06 18:08:05.532 TVRec(1) Error: Failed to set channel to 4. Reverting to kState_None
2009-02-06 18:08:05.533 TVRec(1): Changing from RecordingOnly to None
2009-02-06 18:08:05.568 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 18:08:05.572 Canceled recording (Recorder Failed): The Simpsons "Realty Bites": channel 1031 on cardid 1, sourceid 1
2009-02-06 18:08:06.599 Reschedule requested for id 0.
2009-02-06 18:08:06.888 Scheduled 1 items in 0.3 = 0.28 match + 0.01 place
2009-02-06 18:08:08.611 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/goldrock-desktop/1031_20090206180800.mpg' could not open 
			eno: No such file or directory (2)
2009-02-06 18:08:08.671 Delete Error '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/goldrock-desktop/1031_20090206180800.mpg'
			eno: No such file or directory (2)
2009-02-06 18:08:13.006 Reschedule requested for id 0.
2009-02-06 18:08:13.233 Scheduled 1 items in 0.2 = 0.22 match + 0.01 place
2009-02-06 18:08:48.466 MainServer::HandleAnnounce Monitor
2009-02-06 18:08:48.471 adding: goldrock-desktop as a client (events: 0)
2009-02-06 18:08:48.472 MainServer::HandleAnnounce Monitor
2009-02-06 18:08:48.472 adding: goldrock-desktop as a client (events: 1)
2009-02-06 18:08:48.478 MainServer::HandleAnnounce Playback
2009-02-06 18:08:48.479 adding: goldrock-desktop as a client (events: 0)
2009-02-06 18:08:48.484 TVRec(1): Changing from None to WatchingLiveTV
2009-02-06 18:08:48.489 TVRec(1): HW Tuner: 1->1
2009-02-06 18:08:48.495 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-02-06 18:08:48.495 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-02-06 18:08:48.499 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-02-06 18:08:48.503 TVRec(1): Changing from WatchingLiveTV to None

==> /var/log/mythtv/mythfrontend.log <==
2009-02-06 18:04:30.167 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-02-06 18:04:30.305 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-06 18:04:30.340 Registering Internal as a media playback plugin.
2009-02-06 18:04:30.679 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-06 18:04:31.268 Failed to run 'cdrecord --scanbus'
2009-02-06 18:04:31.274 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-06 18:04:31.280 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-06 18:04:31.295 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
009-02-06 18:04:31.608 No theme dir: /home/goldrock/.mythtv/themes/Mythbuntu-8.04
2009-02-06 18:04:41.366 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/status-ui.xml
2009-02-06 18:04:41.894 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:04:41.895 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:04:49.562 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:04:49.563 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:04:54.717 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:04:54.718 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:04:57.681 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:04:57.681 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:04:58.132 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:04:58.132 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:04:58.487 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:04:58.487 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:05:06.374 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:05:06.374 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:05:09.177 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:05:09.177 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-06 18:05:18.706 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:05:18.706 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
Destroying SipFsm object 
2009-02-06 18:05:23.448 Deleting UPnP client...
Starting mythfrontend.real..
2009-02-06 18:08:41.033 New DB connection, total: 2
2009-02-06 18:08:41.034 Connected to database 'mythconverg' at host: localhost
2009-02-06 18:08:41.035 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-02-06 18:08:41.035 Enabled verbose msgs:  important general
2009-02-06 18:08:42.793 No theme dir: /home/goldrock/.mythtv/themes/Mythbuntu-8.04
2009-02-06 18:08:42.794 Primary screen 0.
2009-02-06 18:08:42.794 Using screen 0, 1440x900 at 0,0
2009-02-06 18:08:42.794 No theme dir: /home/goldrock/.mythtv/themes/Mythbuntu-8.04
2009-02-06 18:08:42.795 Switching to square mode (Mythbuntu-8.04)
2009-02-06 18:08:42.911 Using the Qt painter
2009-02-06 18:08:42.911 JoystickMenuClient Error: Joystick disabled - Failed to read /home/goldrock/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-02-06 18:08:42.911 lirc_init failed for mythtv, see preceding messages
2009-02-06 18:08:44.039 Specified base font 'medium' does not exist for font clock
2009-02-06 18:08:44.039 Specified base font 'medium' does not exist for font small
2009-02-06 18:08:44.039 Specified base font 'medium' does not exist for font medium
2009-02-06 18:08:44.039 Specified base font 'medium' does not exist for font large
2009-02-06 18:08:44.040 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-02-06 18:08:44.147 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-06 18:08:44.204 Registering Internal as a media playback plugin.
2009-02-06 18:08:44.436 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-06 18:08:44.983 Failed to run 'cdrecord --scanbus'
2009-02-06 18:08:44.989 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-06 18:08:44.994 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-06 18:08:45.014 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.4:5060 NAT address 192.168.2.4
SIP: Cannot register; proxy, username or password not set
2009-02-06 18:08:45.350 No theme dir: /home/goldrock/.mythtv/themes/Mythbuntu-8.04
2009-02-06 18:08:48.465 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-06 18:08:48.466 Using protocol version 40
2009-02-06 18:08:48.477 TV: Attempting to change from None to WatchingLiveTV
2009-02-06 18:08:48.478 Using protocol version 40
2009-02-06 18:08:48.508 GetEntryAt(-1) failed.
2009-02-06 18:08:48.509 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2009-02-06 18:08:48.509 TV Error: LiveTV not successfully started
2009-02-06 18:08:48.509 TV Error: LiveTV not successfully started
2009-02-06 18:08:48.584 TV: Deleting TV Chain in destructor
2009-02-06 18:08:48.595 DPMS Deactivated 
2009-02-06 18:08:48.595 DPMS Reactivated.

---

### Post by movieman on 2009-02-06
Looks like you haven't configured any channels on the tuner?

---

### Post by zf3636 on 2009-02-07
Hi the channel frequencis were not set in channel editor, It is working now.

---

