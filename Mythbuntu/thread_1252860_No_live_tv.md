---
title: "No live tv"
date: 2009-08-29
forum: Mythbuntu
---

### Post by benlyboy on 2009-08-29
I am getting ready to build my first myth box

I haven't yet got all the parts, but had enough to build a test rig out of an old pc I had laying about
I think I have the back end set up right and my new pvr500 tuner seems to be working fine (though I am just using one of it's two tuners). 
Did have problem with the tunner only being able to get the first 13 channels of my cable, but found a thread that helped with that.
The thing I can't work out is this. I can't watch live tv or recorded tv. When I click on the watch tv button the screen goes blank for maybe a minute or so then returns to the menu. the same thing happend when I try to watch recorded tv 

DVDs play fine

---

### Post by lessfield on 2009-08-29
Run mythfrontend from a terminal and post the output when you try to watch tv and/or recorded file. Also, can you watch the recorded files via mplayer or VLC

---

### Post by benlyboy on 2009-08-29
thanks for the reply

```
2009-08-29 14:04:38.207 Using runtime prefix = /usr
2009-08-29 14:04:38.766 XScreenSaver support enabled
2009-08-29 14:04:38.767 DPMS is active.
2009-08-29 14:04:38.769 Empty LocalHostName.
2009-08-29 14:04:38.769 Using localhost value of mythbox
2009-08-29 14:04:38.789 New DB connection, total: 1
2009-08-29 14:04:38.819 Connected to database 'mythconverg' at host: localhost
2009-08-29 14:04:38.822 Closing DB connection named 'DBManager0'
2009-08-29 14:04:38.838 Primary screen 0.
2009-08-29 14:04:38.839 Connected to database 'mythconverg' at host: localhost
2009-08-29 14:04:38.842 Using screen 0, 800x600 at 0,0
2009-08-29 14:04:38.875 New DB connection, total: 2
2009-08-29 14:04:38.877 Connected to database 'mythconverg' at host: localhost
2009-08-29 14:04:38.883 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-29 14:04:38.893 Enabled verbose msgs:  important general
2009-08-29 14:04:40.251 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
2009-08-29 14:04:40.255 Primary screen 0.
2009-08-29 14:04:40.256 Using screen 0, 800x600 at 0,0
2009-08-29 14:04:40.257 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
2009-08-29 14:04:40.259 Switching to square mode (Mythbuntu-8.04)
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode:  154
  Minor opcode:  3
  Resource id:  0x7d
X Error: GLXBadContext 168
  Major opcode:  154
  Minor opcode:  6
  Resource id:  0x2200007
2009-08-29 14:04:40.381 Using the Qt painter
2009-08-29 14:04:40.385 lirc init success using configuration file: /home/graham/.mythtv/lircrc
2009-08-29 14:04:40.395 JoystickMenuClient Error: Joystick disabled - Failed to read /home/graham/.mythtv/joystickmenurc
X Error: GLXBadContext 168
  Major opcode:  154
  Minor opcode:  5
  Resource id:  0x2200007
QGLContext::makeCurrent(): Failed.
X Error: GLXBadContext 168
  Major opcode:  154
  Minor opcode:  5
  Resource id:  0x2200007
QGLContext::makeCurrent(): Failed.
2009-08-29 14:04:41.030 Specified base font 'medium' does not exist for font clock
2009-08-29 14:04:41.030 Specified base font 'medium' does not exist for font small
2009-08-29 14:04:41.031 Specified base font 'medium' does not exist for font medium
2009-08-29 14:04:41.031 Specified base font 'medium' does not exist for font large
2009-08-29 14:04:41.034 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-29 14:04:41.284 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-29 14:04:41.430 Registering Internal as a media playback plugin.
2009-08-29 14:04:41.626 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-29 14:04:41.725 Failed to run 'cdrecord --scanbus'
2009-08-29 14:04:41.743 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-29 14:04:41.787 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-29 14:04:41.923 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-29 14:04:42.118 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
2009-08-29 14:04:51.904 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-29 14:04:51.906 Using protocol version 40
2009-08-29 14:04:51.985 TV: Attempting to change from None to WatchingLiveTV
2009-08-29 14:04:51.987 Using protocol version 40
2009-08-29 14:04:53.565 GetEntryAt(-1) failed.
2009-08-29 14:04:53.568 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-08-29 14:04:53.569 TV Error: LiveTV not successfully started
2009-08-29 14:04:53.569 TV Error: LiveTV not successfully started
2009-08-29 14:04:53.625 TV: Deleting TV Chain in destructor
2009-08-29 14:04:53.645 DPMS Deactivated 
2009-08-29 14:04:53.647 DPMS Reactivated.
2009-08-29 14:05:12.801 Deleting UPnP client...
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  2567
  Current serial number in output stream:  2600
graham@mythbox:~$ 

```

---

### Post by tgm4883 on 2009-08-29
Post your backend logs
```
/var/log/mythtv/mythbackend.log
```

---

### Post by benlyboy on 2009-08-29
hi tried to look at the log but was told permission denied.
When I try to use su I get a authentication failure.


what do I need to do?

---

### Post by tgm4883 on 2009-08-29
> **benlyboy said:**
> hi tried to look at the log but was told permission denied.
When I try to use su I get a authentication failure.


what do I need to do?

use sudo

---

### Post by benlyboy on 2009-08-30
Hi

Got this off mythbuntu logs, is it what you need...?


```
==> /var/log/mythtv/mtd.log <==
mtd started at Sat Aug 29 19:34:41 2009
mtd is running on a host called mythbox
19:34:41: Waiting for connections/jobs
19:34:41: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-08-29 19:34:28.343 Using runtime prefix = /usr
2009-08-29 19:34:28.452 Empty LocalHostName.
2009-08-29 19:34:28.482 Using localhost value of mythbox
2009-08-29 19:34:28.678 New DB connection, total: 1
2009-08-29 19:34:28.965 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:29.153 Closing DB connection named 'DBManager0'
2009-08-29 19:34:29.158 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:29.163 New DB connection, total: 2
2009-08-29 19:34:29.166 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:29.197 Current Schema Version: 1214
Starting up as the master server.
2009-08-29 19:34:30.103 New DB connection, total: 3
2009-08-29 19:34:30.183 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:30.617 New DB scheduler connection
2009-08-29 19:34:30.678 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:31.022 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-08-29 19:34:31.025 Main::Registering HttpStatus Extension
2009-08-29 19:34:31.026 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-08-29 19:34:31.027 Enabled verbose msgs:  important general
2009-08-29 19:34:31.072 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-29 19:34:33.872 Reschedule requested for id -1.
2009-08-29 19:34:34.098 Scheduled 0 items in 0.2 = 0.17 match + 0.04 place
2009-08-29 19:34:34.225 Seem to be woken up by USER
2009-08-29 19:34:40.966 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-08-29 23:34:51.310 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-29 23:39:23.446 MainServer::HandleAnnounce Monitor
2009-08-29 23:39:23.451 adding: mythbox as a client (events: 0)
2009-08-29 23:39:23.453 MainServer::HandleAnnounce Monitor
2009-08-29 23:39:23.454 adding: mythbox as a client (events: 1)
2009-08-29 23:39:23.466 MainServer::HandleAnnounce Playback
2009-08-29 23:39:23.489 adding: mythbox as a client (events: 0)
2009-08-29 23:39:23.493 TVRec(1): Changing from None to WatchingLiveTV
2009-08-29 23:39:23.511 TVRec(1): HW Tuner: 1->1
2009-08-29 23:39:25.060 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-08-29 23:39:25.061 NVR(/dev/video0) Error: Unknown audio codec
2009-08-29 23:39:25.113 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-08-29 23:39:25.116 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-08-29 23:40:05.124 TVRec(1): Changing from WatchingLiveTV to None
2009-08-29 23:40:05.142 Finished recording Unknown: channel 1002
2009-08-29 23:42:51.523 Expiring 0 MBytes for 1002 @ Sat Aug 29 23:39:23 2009 => Unknown
2009-08-29 23:49:51.556 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-29 23:56:26.943 Using runtime prefix = /usr
2009-08-29 23:56:26.993 Empty LocalHostName.
2009-08-29 23:56:26.994 Using localhost value of mythbox
2009-08-29 23:56:27.113 New DB connection, total: 1
2009-08-29 23:56:27.129 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:56:27.132 Closing DB connection named 'DBManager0'
2009-08-29 23:56:27.146 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:56:27.150 New DB connection, total: 2
2009-08-29 23:56:27.152 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:56:27.159 Current Schema Version: 1214
Starting up as the master server.
2009-08-29 23:56:27.265 New DB connection, total: 3
2009-08-29 23:56:27.269 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:56:27.633 New DB scheduler connection
2009-08-29 23:56:27.640 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:56:27.788 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-08-29 23:56:27.790 Main::Registering HttpStatus Extension
2009-08-29 23:56:27.792 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-08-29 23:56:27.798 Enabled verbose msgs:  important general
2009-08-29 23:56:27.811 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-29 23:56:30.664 Reschedule requested for id -1.
2009-08-29 23:56:30.730 Scheduled 0 items in 0.1 = 0.03 match + 0.04 place
2009-08-29 23:56:30.746 Seem to be woken up by USER
2009-08-29 23:57:47.676 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-29 23:58:53.834 MainServer::HandleAnnounce Monitor
2009-08-29 23:58:53.839 adding: mythbox as a client (events: 0)
2009-08-29 23:58:53.842 MainServer::HandleAnnounce Monitor
2009-08-29 23:58:53.843 adding: mythbox as a client (events: 1)
2009-08-29 23:59:35.893 MainServer::HandleAnnounce Playback
2009-08-29 23:59:35.894 adding: mythbox as a client (events: 0)
2009-08-29 23:59:35.899 TVRec(1): Changing from None to WatchingLiveTV
2009-08-29 23:59:35.911 TVRec(1): HW Tuner: 1->1
2009-08-29 23:59:37.247 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-08-29 23:59:37.249 NVR(/dev/video0) Error: Unknown audio codec
2009-08-29 23:59:37.286 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-08-29 23:59:37.300 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-08-30 00:00:17.348 TVRec(1): Changing from WatchingLiveTV to None
2009-08-30 00:00:17.362 Finished recording Saturday Night Live: channel 1002
2009-08-30 00:02:47.731 Expiring 0 MBytes for 1002 @ Sat Aug 29 23:29:00 2009 => Saturday Night Live

==> /var/log/mythtv/mythfrontend.log <==
Starting mythfrontend.real..
2009-08-29 23:34:57.786 New DB connection, total: 2
2009-08-29 23:34:57.794 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:34:57.829 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-29 23:34:57.830 Enabled verbose msgs:  important general
2009-08-29 23:35:05.087 Writing settings file /home/graham/.mythtv/mysql.txt
2009-08-29 23:35:05.088 Closing DB connection named 'DBManager1'
2009-08-29 23:35:05.088 Closing DB connection named 'DBManager0'
2009-08-29 23:35:05.101 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:35:05.191 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
2009-08-29 23:35:05.195 Primary screen 0.
2009-08-29 23:35:05.197 Using screen 0, 800x600 at 0,0
2009-08-29 23:35:05.199 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
2009-08-29 23:35:05.201 Switching to square mode (Mythbuntu-8.04)
X Error: BadAlloc (insufficient resources for operation) 11
  Major opcode:  154
  Minor opcode:  3
  Resource id:  0x7d
X Error: GLXBadContext 168
  Major opcode:  154
  Minor opcode:  6
  Resource id:  0x1c00007
2009-08-29 23:35:05.480 Using the Qt painter
2009-08-29 23:35:05.484 lirc init success using configuration file: /home/graham/.mythtv/lircrc
2009-08-29 23:35:05.507 JoystickMenuClient Error: Joystick disabled - Failed to read /home/graham/.mythtv/joystickmenurc
X Error: GLXBadContext 168
  Major opcode:  154
  Minor opcode:  5
  Resource id:  0x1c00007
QGLContext::makeCurrent(): Failed.
X Error: GLXBadContext 168
  Major opcode:  154
  Minor opcode:  5
  Resource id:  0x1c00007
QGLContext::makeCurrent(): Failed.
2009-08-29 23:35:06.561 Specified base font 'medium' does not exist for font clock
2009-08-29 23:35:06.563 Specified base font 'medium' does not exist for font small
2009-08-29 23:35:06.564 Specified base font 'medium' does not exist for font medium
2009-08-29 23:35:06.565 Specified base font 'medium' does not exist for font large
2009-08-29 23:35:06.590 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-29 23:35:07.165 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-29 23:35:07.677 Registering Internal as a media playback plugin.
2009-08-29 23:35:07.801 Upgrading to MythArchive schema version 1001
2009-08-29 23:35:07.850 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:35:08.299 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-29 23:35:08.317 Setting Up MythMovies Database Tables
2009-08-29 23:35:08.462 MythMovies Database Setup Complete
2009-08-29 23:35:08.877 Upgrading to MythMusic schema version 1007
2009-08-29 23:35:08.950 Upgrading to MythMusic schema version 1008
2009-08-29 23:35:09.139 Upgrading to MythMusic schema version 1009
2009-08-29 23:35:09.192 Upgrading to MythMusic schema version 1010
2009-08-29 23:35:09.239 Updating music_albumart image types
2009-08-29 23:35:09.244 Upgrading to MythMusic schema version 1011
2009-08-29 23:35:09.247 Upgrading to MythMusic schema version 1012
2009-08-29 23:35:09.308 Upgrading to MythMusic schema version 1013
2009-08-29 23:35:09.595 Failed to run 'cdrecord --scanbus'
2009-08-29 23:35:09.653 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-29 23:35:09.689 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-29 23:35:09.933 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-29 23:35:10.317 Inserting MythWeather initial database information.
2009-08-29 23:35:10.318 Upgrading to MythWeather schema version 1000
2009-08-29 23:35:10.699 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
2009-08-29 23:39:23.426 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-29 23:39:23.429 Using protocol version 40
2009-08-29 23:39:23.463 TV: Attempting to change from None to WatchingLiveTV
2009-08-29 23:39:23.465 Using protocol version 40
2009-08-29 23:39:25.127 DPMS Deactivated 
2009-08-29 23:40:05.115 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-29 23:40:05.116 TV Error: LiveTV not successfully started
2009-08-29 23:40:05.144 TV: Deleting TV Chain in destructor
2009-08-29 23:40:05.146 DPMS Reactivated.
2009-08-29 23:40:40.656 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2009-08-29 23:41:25.394 No theme dir: /home/graham/.mythtv/themes/Mythbuntu-8.04
/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/changer.py:48: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import Popen3
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree... 94%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done


(mythbuntu-control-centre:4869): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(mythbuntu-control-centre:4869): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 * Stopping MythTV server: mythbackend 
2009-08-29 23:52:00.039 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-08-29 23:58:53.549 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2009-08-29 23:58:53.831 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-29 23:58:53.833 Using protocol version 40
2009-08-29 23:59:35.891 TV: Attempting to change from None to WatchingLiveTV
2009-08-29 23:59:35.892 Using protocol version 40
2009-08-29 23:59:37.339 DPMS Deactivated 
2009-08-30 00:00:17.336 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-30 00:00:17.340 TV Error: LiveTV not successfully started
2009-08-30 00:00:17.411 TV: Deleting TV Chain in destructor
2009-08-30 00:00:17.413 DPMS Reactivated.
No LSB modules are available.
WARNING: you should run this program as super-user.

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Aug 29 19:34:36 mythbox NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 29 19:34:36 mythbox NetworkManager: <info>  (eth0): bringing up device. 
Aug 29 19:34:36 mythbox NetworkManager: <info>  (eth0): preparing device. 
Aug 29 19:34:36 mythbox NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 29 19:34:36 mythbox NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Aug 29 19:34:36 mythbox NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Aug 29 19:34:36 mythbox kernel: [   53.280626] eth0:  setting full-duplex.
Aug 29 19:34:36 mythbox console-kit-daemon[2829]: WARNING: Couldn't read /proc/2823/environ: Failed to open file '/proc/2823/environ': No such file or directory 
Aug 29 19:34:37 mythbox nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_01_03_20_b6_9a
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Aug 29 19:34:37 mythbox NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug 29 19:34:37 mythbox NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Aug 29 19:34:37 mythbox NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Aug 29 19:34:37 mythbox NetworkManager: <info>  dhclient started with pid 3363 
Aug 29 19:34:37 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 29 19:34:37 mythbox dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 29 19:34:37 mythbox dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 29 19:34:37 mythbox dhclient: All rights reserved.
Aug 29 19:34:37 mythbox dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 29 19:34:37 mythbox dhclient: 
Aug 29 19:34:37 mythbox NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Aug 29 19:34:37 mythbox dhclient: Listening on LPF/eth0/00:01:03:20:b6:9a
Aug 29 19:34:37 mythbox dhclient: Sending on   LPF/eth0/00:01:03:20:b6:9a
Aug 29 19:34:37 mythbox dhclient: Sending on   Socket/fallback
Aug 29 19:34:37 mythbox avahi-daemon[3182]: Registering new address record for fe80::201:3ff:fe20:b69a on eth0.*.
Aug 29 19:34:39 mythbox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 29 19:34:39 mythbox dhclient: DHCPOFFER of 192.168.10.104 from 192.168.10.1
Aug 29 19:34:39 mythbox dhclient: DHCPREQUEST of 192.168.10.104 on eth0 to 255.255.255.255 port 67
Aug 29 19:34:39 mythbox dhclient: DHCPACK of 192.168.10.104 from 192.168.10.1
Aug 29 19:34:39 mythbox NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Aug 29 19:34:39 mythbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 29 19:34:39 mythbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Aug 29 19:34:39 mythbox NetworkManager: <info>    address 192.168.10.104 
Aug 29 19:34:39 mythbox NetworkManager: <info>    prefix 24 (255.255.255.0) 
Aug 29 19:34:39 mythbox NetworkManager: <info>    gateway 192.168.10.1 
Aug 29 19:34:39 mythbox NetworkManager: <info>    nameserver '192.168.10.1' 
Aug 29 19:34:39 mythbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 29 19:34:39 mythbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 29 19:34:39 mythbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 29 19:34:39 mythbox avahi-daemon[3182]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.10.104.
Aug 29 19:34:39 mythbox avahi-daemon[3182]: New relevant interface eth0.IPv4 for mDNS.
Aug 29 19:34:39 mythbox avahi-daemon[3182]: Registering new address record for 192.168.10.104 on eth0.IPv4.
Aug 29 19:34:39 mythbox dhclient: bound to 192.168.10.104 -- renewal in 5344 seconds.
Aug 29 19:34:39 mythbox mysqld_safe[3616]: Number of processes running now: 1
Aug 29 19:34:39 mythbox mysqld_safe[3624]: mysqld process hanging, pid 2601 - killed
Aug 29 19:34:39 mythbox mysqld_safe[3627]: restarted
Aug 29 19:34:40 mythbox NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Aug 29 19:34:40 mythbox NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 29 19:34:40 mythbox NetworkManager: <info>  Activation (eth0) successful, device activated. 
Aug 29 19:34:40 mythbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 29 19:34:40 mythbox mysqld[3631]: 090829 19:34:40  InnoDB: Started; log sequence number 0 43655
Aug 29 19:34:40 mythbox mysqld[3631]: 090829 19:34:40 [Note] /usr/sbin/mysqld: ready for connections.
Aug 29 19:34:40 mythbox mysqld[3631]: Version: '5.0.75-0ubuntu10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Aug 29 19:34:41 mythbox ntpd[2763]: ntpd exiting on signal 15
Aug 29 23:34:42 mythbox ntpdate[3748]: step time server 91.189.94.4 offset 14400.212637 sec
Aug 29 23:34:42 mythbox ntpd[3790]: ntpd 4.2.4p4@1.1520-o Sat Mar 21 00:50:18 UTC 2009 (1)
Aug 29 23:34:42 mythbox ntpd[3791]: precision = 1.000 usec
Aug 29 23:34:42 mythbox ntpd[3791]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 29 23:34:42 mythbox ntpd[3791]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 29 23:34:42 mythbox ntpd[3791]: Listening on interface #2 lo, ::1#123 Enabled
Aug 29 23:34:42 mythbox ntpd[3791]: Listening on interface #3 eth0, fe80::201:3ff:fe20:b69a#123 Enabled
Aug 29 23:34:42 mythbox ntpd[3791]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 29 23:34:42 mythbox ntpd[3791]: Listening on interface #5 eth0, 192.168.10.104#123 Enabled
Aug 29 23:34:42 mythbox ntpd[3791]: kernel time sync status 0040
Aug 29 23:34:42 mythbox ntpd[3791]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Aug 29 23:34:46 mythbox kernel: [   63.972044] eth0: no IPv6 routers present
Aug 29 23:35:05 mythbox lircd-0.8.4a[1442]: accepted new client on /dev/lircd
Aug 29 23:39:01 mythbox ntpd[3791]: synchronized to 91.189.94.4, stratum 2
Aug 29 23:39:01 mythbox ntpd[3791]: kernel time sync status change 0001
Aug 29 23:39:01 mythbox /USR/SBIN/CRON[3932]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 29 23:40:01 mythbox /USR/SBIN/CRON[4175]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 29 23:49:11 mythbox NetworkManager: <info>  DHCP: device eth0 state changed bound -> expire 
Aug 29 23:49:11 mythbox NetworkManager: <info>  DHCP: device eth0 state changed expire -> preinit 
Aug 29 23:49:11 mythbox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 29 23:49:11 mythbox dhclient: DHCPOFFER of 192.168.10.104 from 192.168.10.1
Aug 29 23:49:11 mythbox dhclient: DHCPREQUEST of 192.168.10.104 on eth0 to 255.255.255.255 port 67
Aug 29 23:49:11 mythbox dhclient: DHCPACK of 192.168.10.104 from 192.168.10.1
Aug 29 23:49:11 mythbox NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Aug 29 23:49:11 mythbox NetworkManager: <info>    address 192.168.10.104 
Aug 29 23:49:11 mythbox NetworkManager: <info>    prefix 24 (255.255.255.0) 
Aug 29 23:49:11 mythbox NetworkManager: <info>    gateway 192.168.10.1 
Aug 29 23:49:11 mythbox NetworkManager: <info>    nameserver '192.168.10.1' 
Aug 29 23:49:11 mythbox dhclient: bound to 192.168.10.104 -- renewal in 4391 seconds.
Aug 29 23:50:01 mythbox /USR/SBIN/CRON[4567]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 29 23:52:01 mythbox lircd-0.8.4a[1442]: accepted new client on /dev/lircd
Aug 29 23:56:23 mythbox lircd-0.8.4a[1442]: removed client
Aug 30 00:00:02 mythbox /USR/SBIN/CRON[5365]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd weekly 2>/dev/null)
Aug 30 00:00:02 mythbox /USR/SBIN/CRON[5368]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 30 00:00:02 mythbox /USR/SBIN/CRON[5371]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd daily 2>/dev/null)
Aug 30 00:00:02 mythbox /USR/SBIN/CRON[5374]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)

==> /var/log/Xorg.0.log <==
drmGetBusid returned ''
(II) [drm] loaded kernel module for "tdfx" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) TDFX(0): [drm] Using the DRM lock SAREA also for drawables.
(II) TDFX(0): [drm] framebuffer handle = 0xf0000000
(II) TDFX(0): [drm] added 1 reserved context for kernel
(II) TDFX(0): X context handle = 0x1
(II) TDFX(0): [drm] installed DRM signal handler
(II) TDFX(0): [drm] Registers = 0xfc000000
(II) TDFX(0): visual configs initialized
(II) TDFX(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Driver provided NonTEGlyphRenderer replacement
	Setting up tile and stipple cache:
		32 128x128 slots
		8 256x256 slots
(==) TDFX(0): Backing store disabled
(==) TDFX(0): Silken mouse enabled
(II) TDFX(0): DPMS enabled
(II) TDFX(0): [DRI] installation complete
(II) TDFX(0): Direct rendering enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:03:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:03:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: Loaded and initialized /usr/lib/dri/tdfx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(EE) TDFX(0): DRIUnlock called when not locked.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
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
(II) config/hal: Adding input device Dell Dell USB Mouse
(**) Dell Dell USB Mouse: always reports core events
(**) Dell Dell USB Mouse: Device: "/dev/input/event4"
(II) Dell Dell USB Mouse: Found 3 mouse buttons
(II) Dell Dell USB Mouse: Found x and y relative axes
(II) Dell Dell USB Mouse: Configuring as mouse
(**) Dell Dell USB Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Mouse" (type: MOUSE)
(**) Dell Dell USB Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Dell USB Mouse: (accel) set acceleration profile 0

==> /home/graham/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2009-08-29 19:34:40.942 Using runtime prefix = /usr
2009-08-29 19:34:40.951 Empty LocalHostName.
2009-08-29 19:34:40.951 Using localhost value of mythbox
2009-08-29 19:34:41.009 New DB connection, total: 1
2009-08-29 19:34:41.056 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:41.058 Closing DB connection named 'DBManager0'
2009-08-29 19:34:41.060 Connected to database 'mythconverg' at host: localhost
2009-08-29 19:34:41.088 Upgrading to MythVideo schema version 1011
2009-08-29 19:34:41.093 New DB connection, total: 2
2009-08-29 19:34:41.095 Connected to database 'mythconverg' at host: localhost
/usr/bin/startxfce4: X server already running on display :0
2009-08-29 19:34:41.100 Updated from old MythDVD/MythVideo schema to combined version: 1011.
2009-08-29 19:34:41.103 Upgrading to MythVideo schema version 1012
2009-08-29 19:34:41.236 Upgrading to MythVideo schema version 1013
2009-08-29 19:34:41.238 Upgrading to MythVideo schema version 1014
2009-08-29 19:34:41.355 Upgrading to MythVideo schema version 1015
/etc/xdg/xfce4/xinitrc: 59: source: not found
2009-08-29 19:34:41.560 Upgrading to MythVideo schema version 1016
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[3805]: starting up
xfce4-settings-helper is already running
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

MCS->Xfconf settings migration complete

** (nm-applet:3829): DEBUG: applet_common_device_state_changed
2009-08-29 23:34:56.470 Using runtime prefix = /usr
2009-08-29 23:34:57.362 XScreenSaver support enabled
2009-08-29 23:34:57.363 DPMS is active.
2009-08-29 23:34:57.364 Empty LocalHostName.
2009-08-29 23:34:57.365 Using localhost value of mythbox
2009-08-29 23:34:57.382 New DB connection, total: 1
2009-08-29 23:34:57.446 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:34:57.449 Closing DB connection named 'DBManager0'
2009-08-29 23:34:57.453 Primary screen 0.
2009-08-29 23:34:57.492 Connected to database 'mythconverg' at host: localhost
2009-08-29 23:34:57.495 Using screen 0, 800x600 at 0,0
** (update-notifier:3845): DEBUG: /usr/lib/update-notifier/apt-check returned 150 (security: 144)
** (update-notifier:3845): DEBUG: crashreport_check

Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".

** (xfwm4:3799): WARNING **: Last user time set back to 1092463 (was 1366353)

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.3G  1.6G  6.3G  20% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  348K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  180K  249M   1% /dev
tmpfs                 249M     0  249M   0% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6             9.9G  174M  9.7G   2% /var/lib

==> uname -a <==
Linux mythbox 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 01)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 01)
01:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:0b.0 Modem: ALi Corporation SmartLink SmartPCI563 56K Modem
01:0c.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
01:0d.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

==> lsusb <==
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp. Mouse
Bus 001 Device 002: ID 0e9c:0000 Streamzap, Inc. Streamzap Remote Control
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MiB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82815 815 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: Voodoo 3
                vendor: 3Dfx Interactive, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: driver=voodoo3_smbus latency=0 module=i2c_voodoo3
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: a
                bus info: pci@0000:01:0a.0
                logical name: eth0
                version: 78
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=[REMOVED] latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
           *-communication
                description: Modem
                product: SmartLink SmartPCI563 56K Modem
                vendor: ALi Corporation
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=serial latency=64
           *-multimedia
                description: Multimedia audio controller
                product: ES1370 [AudioPCI]
                vendor: Ensoniq
                physical id: c
                bus info: pci@0000:01:0c.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=ENS1370 latency=64 maxlatency=128 mingnt=12 module=snd_ens1370
           *-pci
                description: PCI bridge
                product: HB6 Universal PCI-PCI bridge (non-transparent mode)
                vendor: Hint Corp
                physical id: d
                bus info: pci@0000:01:0d.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: pci bus_master cap_list
              *-multimedia:0
                   description: Multimedia video controller
                   product: iTVC16 (CX23416) MPEG-2 Encoder
                   vendor: Internext Compression Inc
                   physical id: 8
                   bus info: pci@0000:02:08.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list
                   configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
              *-multimedia:1
                   description: Multimedia video controller
                   product: iTVC16 (CX23416) MPEG-2 Encoder
                   vendor: Internext Compression Inc
                   physical id: 9
                   bus info: pci@0000:02:09.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list
                   configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-usb
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by tgm4883 on 2009-08-30
Yep, it's not setup right. What type of card did you set it up as in mythtv-setup?  It needs to be setup as an MPEG encoder card (might be called an IVTV card)

---

### Post by benlyboy on 2009-08-30
thanks alot:P that did the trick

seems to be working fine now

---

