---
title: "MythTV reports recording, but never performs it"
date: 2008-07-17
forum: Mythbuntu
---

### Post by jrhaws on 2008-07-17
I cannot seem to get MythTV to record programs.

Here is my setup:

Asus P4P800 MB with Intel P4 3.0GHz, 1GB RAM
Dual pcHDTV HD-5500 cards
Kernel Version:  2.6.24.19-generic

Both the backend and frontend are running off the same machine.

I can setup a recording, have it show up in the upcoming programs list, and even have the MythTV status tell me that the tuner is recording at the time of the recording (both in the frontend and in mythweb).  However, it never actually records anything.  The recordings directory remains empty and the frontend and mythweb both tell me that the file for the recording does not exist.

Here are some relevant portions of the log file:

```
2008-07-16 23:11:40.900 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-07-16 23:12:00.211 TVRec(4): Changing from RecordingOnly to None
2008-07-16 23:12:00.260 Finished recording 2-1 (KUTV-DT) "Wed Jul 16 23:11:00 2008": channel 3021
2008-07-16 23:12:00.262 Reschedule requested for id 0.
2008-07-16 23:12:00.325 Scheduled 21 items in 0.1 = 0.00 match + 0.06 place
2008-07-16 23:12:13.956 MainServer::HandleAnnounce Monitor
2008-07-16 23:12:13.958 adding: kronk as a client (events: 0)
2008-07-16 23:12:14.403 MainServer::HandleAnnounce Monitor
2008-07-16 23:12:14.403 adding: kronk as a client (events: 0)
...
2008-07-16 23:12:23.074 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/3021_20080716231100.mpg'
```

The last log message is when I tried to access the thing via mythweb.

Here is a portion of the frontend log when I try to view the recording from the frontend:

```
2008-07-16 23:17:31.007 Connecting to backend server: 10.0.0.2:6543 (try 1 of 5)
2008-07-16 23:17:31.007 Using protocol version 40
2008-07-16 23:17:31.073 Error: File 'myth://10.0.0.2:6543/3021_20080716231100.mpg' missing.
2008-07-16 23:17:31.524 Error: File 'myth://10.0.0.2:6543/3021_20080716231100.mpg' missing.
2008-07-16 23:17:32.024 Error: File 'myth://10.0.0.2:6543/3021_20080716231100.mpg' missing.
2008-07-16 23:17:32.338 Error: File 'myth://10.0.0.2:6543/3021_20080716231100.mpg' missing.
2008-07-16 23:17:32.526 Error: File 'myth://10.0.0.2:6543/3021_20080716231100.mpg' missing.

```

From what I can tell, the mythfrontend is trying to stream the recording from the backend, which is weird since it is on the local machine.

From searching the forums I tried checking my storagegroup table, but that wasn't the problem (the table was fine, but I dropped it and recreated it anyway just to be sure).

This problem started after I changed the IP address in mythtv-setup for the backend to be 10.0.0.2 in both the local backend and master backend sections of the General section.  I had to do this in order to get the recordings to even show up in the upcoming recordings.  Ever since then, I cannot record.

I also thought that it was a permissions issue, but I checked and the mythtv user has full control over the recordings dir (/data/recordings).  LiveTV will record and work fine, and its directory is a subdirectory to the main recording directory (/data/recordings/live).

Does anyone have any ideas what I can do to get this to work?  This is the last obstacle I have between me and a fully functional MythTV setup.

Thanks!

Jon

---

### Post by jaakan on 2008-07-17
> **jrhaws said:**
> This problem started after I changed the IP address in mythtv-setup for the backend to be 10.0.0.2 in both the local backend and master backend sections of the General section. I had to do this in order to get the recordings to even show up in the upcoming recordings. Ever since then, I cannot record.

Sounds like you just found a bug. you should report it.

I just built a Mythbuntu box this past weekend and it was connected to a Linksys router DHCP. it's ip has changed from 192.168.1.102 to ...100. with no issues.

---

### Post by jrhaws on 2008-08-14
Okay, here we go again.

Just to be sure that there weren't any weird configuration issues, I reloaded Mythbuntu 8.04 from scratch.  I set things up exactly how I wanted them and things are working great, other than this same problem.

I can watch live TV just fine and it stores the files in /data/recordings/live without issues.

However, when I try and record a program, the status shows that the tuner is recording and the database lists the program as recorded once it is finished.  However, when I go into the frontend to watch the recording, it tells me the file does not exist.  So I check and the /data/recordings directory is empty!

Any ideas?  I have tried this through the mythweb interface and the frontend interface - both with the same result.

Here is the exact error message from mythweb:

```
1843_20080814114800.mpg does not exist in any recognized storage group directories for this host.
```

Here are the full frontend and backend logs.  Really only things from 2008-08-14 are relevant, so I cut out the stuff from yesterday:

```
2008-08-14 10:42:44.379 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 10:42:44.426 Empty LocalHostName.
2008-08-14 10:42:44.457 Using localhost value of kronk
2008-08-14 10:42:44.522 New DB connection, total: 1
2008-08-14 10:42:44.561 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:42:44.598 Closing DB connection named 'DBManager0'
2008-08-14 10:42:44.630 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:42:44.665 New DB connection, total: 2
2008-08-14 10:42:44.697 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:42:44.734 Current Schema Version: 1214
Running as a slave backend.
2008-08-14 10:42:44.806 New DB connection, total: 3
2008-08-14 10:42:44.839 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:42:45.113 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-08-14 10:42:45.147 Main::Registering HttpStatus Extension
2008-08-14 10:42:45.181 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-14 10:42:45.214 Enabled verbose msgs:  important general
2008-08-14 10:42:45.266 SG(Default) Error: Group 'Default' wants to use directory '/data/recordings/', but this directory is not writeable.
2008-08-14 10:42:46.270 Connecting to master server: 10.0.0.2:6543
2008-08-14 10:42:46.300 Connected successfully
2008-08-14 10:43:16.344 MythSocket(b1102020:11): readStringList: Error, timeout.
2008-08-14 10:43:16.381 adding: kronk as a slave backend server
2008-08-14 10:43:16.415 MythSocket(b1102fb8:-1): writeStringList: Error, socket went unconnected.
2008-08-14 10:47:46.629 MainServer::HandleAnnounce Monitor
2008-08-14 10:47:46.658 adding: kronk as a client (events: 0)
2008-08-14 10:47:47.382 MainServer::HandleAnnounce Monitor
2008-08-14 10:47:47.410 adding: kronk as a client (events: 0)
2008-08-14 10:47:53.283 MainServer::HandleAnnounce Monitor
2008-08-14 10:47:53.320 adding: kronk as a client (events: 0)
2008-08-14 10:47:53.529 MainServer::HandleAnnounce Monitor
2008-08-14 10:47:53.562 adding: kronk as a client (events: 0)
2008-08-14 10:47:54.933 MainServer::HandleAnnounce Monitor
2008-08-14 10:47:54.965 adding: kronk as a client (events: 0)
2008-08-14 10:47:55.207 MainServer::HandleAnnounce Monitor
2008-08-14 10:47:55.240 adding: kronk as a client (events: 0)
2008-08-14 10:48:02.138 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:02.171 adding: kronk as a client (events: 0)
2008-08-14 10:48:02.585 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:02.622 adding: kronk as a client (events: 0)
2008-08-14 10:48:04.207 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:04.241 adding: kronk as a client (events: 0)
2008-08-14 10:48:04.938 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:04.968 adding: kronk as a client (events: 0)
2008-08-14 10:48:05.402 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:05.435 adding: kronk as a client (events: 0)
2008-08-14 10:48:06.634 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:06.671 adding: kronk as a client (events: 0)
2008-08-14 10:48:06.708 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:06.738 adding: kronk as a client (events: 0)
2008-08-14 10:48:48.975 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:49.014 adding: kronk as a client (events: 0)
2008-08-14 10:48:49.353 MainServer::HandleAnnounce Monitor
2008-08-14 10:48:49.381 adding: kronk as a client (events: 0)
2008-08-14 10:49:03.378 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:03.408 adding: kronk as a client (events: 0)
2008-08-14 10:49:04.580 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:04.610 adding: kronk as a client (events: 0)
2008-08-14 10:49:04.967 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:04.994 adding: kronk as a client (events: 0)
2008-08-14 10:49:06.766 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:06.797 adding: kronk as a client (events: 0)
2008-08-14 10:49:07.096 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:07.123 adding: kronk as a client (events: 0)
2008-08-14 10:49:09.953 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:09.986 adding: kronk as a client (events: 0)
2008-08-14 10:49:10.316 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:10.345 adding: kronk as a client (events: 0)
2008-08-14 10:49:10.784 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:10.821 adding: kronk as a client (events: 0)
2008-08-14 10:49:11.117 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:11.147 adding: kronk as a client (events: 0)
2008-08-14 10:49:13.538 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:13.576 adding: kronk as a client (events: 0)
2008-08-14 10:49:13.846 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:13.877 adding: kronk as a client (events: 0)
2008-08-14 10:49:18.128 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:18.160 adding: kronk as a client (events: 0)
2008-08-14 10:49:18.427 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:18.468 adding: kronk as a client (events: 0)
2008-08-14 10:49:20.292 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:20.322 adding: kronk as a client (events: 0)
2008-08-14 10:49:20.672 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:20.706 adding: kronk as a client (events: 0)
2008-08-14 10:49:21.710 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:21.741 adding: kronk as a client (events: 0)
2008-08-14 10:49:22.022 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:22.058 adding: kronk as a client (events: 0)
2008-08-14 10:49:25.576 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:25.607 adding: kronk as a client (events: 0)
2008-08-14 10:49:26.719 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:26.751 adding: kronk as a client (events: 0)
2008-08-14 10:49:26.954 MainServer::HandleAnnounce Monitor
2008-08-14 10:49:26.984 adding: kronk as a client (events: 0)
2008-08-14 10:55:57.388 MainServer::HandleAnnounce Monitor
2008-08-14 10:55:57.424 adding: kronk as a client (events: 0)
2008-08-14 10:55:57.458 MainServer::HandleAnnounce Monitor
2008-08-14 10:55:57.491 adding: kronk as a client (events: 1)
2008-08-14 10:58:11.345 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 10:58:11.391 Empty LocalHostName.
2008-08-14 10:58:11.453 Using localhost value of kronk
2008-08-14 10:58:11.498 New DB connection, total: 1
2008-08-14 10:58:11.538 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:58:11.569 Closing DB connection named 'DBManager0'
2008-08-14 10:58:11.602 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:58:11.637 New DB connection, total: 2
2008-08-14 10:58:11.668 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:58:11.704 Current Schema Version: 1214
Starting up as the master server.
2008-08-14 10:58:11.779 New DB connection, total: 3
2008-08-14 10:58:11.810 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:58:11.897 New DB scheduler connection
2008-08-14 10:58:11.935 Connected to database 'mythconverg' at host: localhost
2008-08-14 10:58:13.258 Main::Registering HttpStatus Extension
2008-08-14 10:58:13.297 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-14 10:58:13.329 Enabled verbose msgs:  important general
2008-08-14 10:58:13.365 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 10:58:14.982 Reschedule requested for id -1.
2008-08-14 10:58:15.083 Scheduled 0 items in 0.1 = 0.05 match + 0.05 place
2008-08-14 10:58:15.121 Seem to be woken up by USER
2008-08-14 10:58:22.013 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 10:58:22.046 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-14 10:59:31.982 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:00:05.294 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:00:05.333 Empty LocalHostName.
2008-08-14 11:00:05.376 Using localhost value of kronk
2008-08-14 11:00:05.423 New DB connection, total: 1
2008-08-14 11:00:05.455 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:05.484 Closing DB connection named 'DBManager0'
2008-08-14 11:00:05.517 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:05.551 New DB connection, total: 2
2008-08-14 11:00:05.600 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:05.637 Current Schema Version: 1214
Starting up as the master server.
2008-08-14 11:00:05.715 New DB connection, total: 3
2008-08-14 11:00:05.742 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:05.839 New DB scheduler connection
2008-08-14 11:00:05.875 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:07.139 Main::Registering HttpStatus Extension
2008-08-14 11:00:07.169 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-14 11:00:07.202 Enabled verbose msgs:  important general
2008-08-14 11:00:07.238 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:00:08.912 Reschedule requested for id -1.
2008-08-14 11:00:08.970 Scheduled 0 items in 0.1 = 0.04 match + 0.02 place
2008-08-14 11:00:09.003 Seem to be woken up by USER
2008-08-14 11:00:15.938 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 11:00:15.969 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-08-14 11:00:37.014 MainServer::HandleAnnounce Monitor
2008-08-14 11:00:37.048 adding: kronk as a client (events: 0)
2008-08-14 11:00:37.083 MainServer::HandleAnnounce Monitor
2008-08-14 11:00:37.115 adding: kronk as a client (events: 1)
2008-08-14 11:00:37.154 MainServer::HandleAnnounce Playback
2008-08-14 11:00:37.182 adding: kronk as a client (events: 0)
2008-08-14 11:00:37.217 TVRec(1): Changing from None to WatchingLiveTV
2008-08-14 11:00:37.256 TVRec(1): HW Tuner: 1->1
2008-08-14 11:00:38.433 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:00:39.166 Finished recording As the World Turns: channel 1021
2008-08-14 11:00:40.249 Finished recording As the World Turns: channel 1021
2008-08-14 11:00:40.332 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:00:40.486 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:00:40.516 Empty LocalHostName.
2008-08-14 11:00:40.549 Using localhost value of kronk
2008-08-14 11:00:40.592 New DB connection, total: 1
2008-08-14 11:00:40.628 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:40.659 Closing DB connection named 'DBManager0'
2008-08-14 11:00:40.692 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:40.726 New DB connection, total: 2
2008-08-14 11:00:40.758 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:00:40.794 Current Schema Version: 1214
2008-08-14 11:00:40.836 Preview Error: Previewer file '/data/recordings/live/1021_20080814110037.mpg' is not valid.
2008-08-14 11:00:40.867 Preview Error: Run() file not local: '/data/recordings/live/1021_20080814110037.mpg'
2008-08-14 11:00:40.905 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1021_20080814110037.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:01:13.120 TVRec(1): HW Tuner: 1->1
2008-08-14 11:01:14.345 Finished recording As the World Turns: channel 1021
2008-08-14 11:01:14.460 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:01:14.601 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:01:14.630 Empty LocalHostName.
2008-08-14 11:01:14.662 Using localhost value of kronk
2008-08-14 11:01:14.699 New DB connection, total: 1
2008-08-14 11:01:14.738 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:01:14.769 DTVSM(0) Error: Wrong PMT; pmt->pn(99) desired(98)
2008-08-14 11:01:14.780 Closing DB connection named 'DBManager0'
2008-08-14 11:01:14.838 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:01:14.865 New DB connection, total: 2
2008-08-14 11:01:14.897 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:01:14.931 Current Schema Version: 1214
2008-08-14 11:01:15.027 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:01:16.107 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:01:16.172 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:01:16.369 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:01:16.400 Empty LocalHostName.
2008-08-14 11:01:16.424 Using localhost value of kronk
2008-08-14 11:01:16.458 New DB connection, total: 1
2008-08-14 11:01:16.495 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:01:16.526 Closing DB connection named 'DBManager0'
2008-08-14 11:01:16.558 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:01:16.584 New DB connection, total: 2
2008-08-14 11:01:16.617 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:01:16.643 Current Schema Version: 1214
2008-08-14 11:01:16.684 Preview Error: Previewer file '/data/recordings/live/1051_20080814110113.mpg' is not valid.
2008-08-14 11:01:16.717 Preview Error: Run() file not local: '/data/recordings/live/1051_20080814110113.mpg'
2008-08-14 11:01:16.756 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1051_20080814110113.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:01:17.450 AFD: Opened codec 0x82af880, id(MPEG2VIDEO) type(Video)
2008-08-14 11:01:17.476 AFD: codec AC3 has 2 channels
2008-08-14 11:01:17.502 AFD: Opened codec 0x82afe70, id(AC3) type(Audio)
2008-08-14 11:01:18.378 Preview: Grabbed preview '/data/recordings/live/1021_20080814110039.mpg' 1920x1088@64s
2008-08-14 11:01:25.921 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:24.480 TVRec(1): HW Tuner: 1->1
2008-08-14 11:02:25.736 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:02:25.849 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:25.956 DTVSM(0) Error: Wrong PMT; pmt->pn(650) desired(656)
2008-08-14 11:02:25.974 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:02:25.989 Expiring 0 MBytes for 1021 @ Thu Aug 14 11:00:00 2008 => As the World Turns
2008-08-14 11:02:26.050 Expiring 48 MBytes for 1021 @ Thu Aug 14 11:00:00 2008 => As the World Turns
2008-08-14 11:02:26.083 Expiring 0 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:02:26.017 Empty LocalHostName.
2008-08-14 11:02:26.150 Using localhost value of kronk
2008-08-14 11:02:26.176 Finished recording Unknown: channel 1821
2008-08-14 11:02:26.194 New DB connection, total: 1
2008-08-14 11:02:26.254 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:26.288 Closing DB connection named 'DBManager0'
2008-08-14 11:02:26.317 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:26.352 New DB connection, total: 2
2008-08-14 11:02:26.384 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:26.423 Current Schema Version: 1214
2008-08-14 11:02:27.267 Finished recording Unknown: channel 1821
2008-08-14 11:02:27.384 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:27.551 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:02:27.586 Empty LocalHostName.
2008-08-14 11:02:27.619 Using localhost value of kronk
2008-08-14 11:02:27.662 New DB connection, total: 1
2008-08-14 11:02:27.699 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:27.730 Closing DB connection named 'DBManager0'
2008-08-14 11:02:27.762 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:27.796 New DB connection, total: 2
2008-08-14 11:02:27.828 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:27.863 Current Schema Version: 1214
2008-08-14 11:02:27.904 Preview Error: Previewer file '/data/recordings/live/1821_20080814110224.mpg' is not valid.
2008-08-14 11:02:27.937 Preview Error: Run() file not local: '/data/recordings/live/1821_20080814110224.mpg'
2008-08-14 11:02:27.976 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1821_20080814110224.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:02:28.962 AFD: Opened codec 0x82afa70, id(MPEG2VIDEO) type(Video)
2008-08-14 11:02:28.997 AFD: codec AC3 has 6 channels
2008-08-14 11:02:29.031 AFD: Opened codec 0x82b0060, id(AC3) type(Audio)
2008-08-14 11:02:29.798 Preview: Grabbed preview '/data/recordings/live/1051_20080814110115.mpg' 1920x1088@64s
2008-08-14 11:02:38.890 TVRec(1): HW Tuner: 1->1
2008-08-14 11:02:40.136 Finished recording Unknown: channel 1821
2008-08-14 11:02:40.227 New DB connection, total: 4
2008-08-14 11:02:40.259 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:40.323 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:40.357 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:02:40.393 Empty LocalHostName.
2008-08-14 11:02:40.426 Using localhost value of kronk
2008-08-14 11:02:40.490 New DB connection, total: 1
2008-08-14 11:02:40.533 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(9)
2008-08-14 11:02:40.540 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:40.568 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(9)
2008-08-14 11:02:40.603 Closing DB connection named 'DBManager0'
2008-08-14 11:02:40.669 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:40.685 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(9)
2008-08-14 11:02:40.740 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(9)
2008-08-14 11:02:40.703 New DB connection, total: 2
2008-08-14 11:02:40.768 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(9)
2008-08-14 11:02:40.803 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:40.835 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(9)
2008-08-14 11:02:40.902 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(9)
2008-08-14 11:02:40.871 Current Schema Version: 1214
2008-08-14 11:02:40.935 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(9)
2008-08-14 11:02:41.005 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(9)
2008-08-14 11:02:41.253 Finished recording Unknown: channel 1831
2008-08-14 11:02:42.336 Finished recording Unknown: channel 1831
2008-08-14 11:02:42.410 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:42.608 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:02:42.639 Empty LocalHostName.
2008-08-14 11:02:42.672 Using localhost value of kronk
2008-08-14 11:02:42.720 New DB connection, total: 1
2008-08-14 11:02:42.754 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:42.790 Closing DB connection named 'DBManager0'
2008-08-14 11:02:42.823 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:42.857 New DB connection, total: 2
2008-08-14 11:02:42.889 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:42.924 Current Schema Version: 1214
2008-08-14 11:02:42.965 Preview Error: Previewer file '/data/recordings/live/1831_20080814110239.mpg' is not valid.
2008-08-14 11:02:42.999 Preview Error: Run() file not local: '/data/recordings/live/1831_20080814110239.mpg'
2008-08-14 11:02:43.036 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1831_20080814110239.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:02:43.479 AFD: Opened codec 0x82af3a0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:02:43.507 AFD: codec AC3 has 2 channels
2008-08-14 11:02:43.541 AFD: Opened codec 0x82af990, id(AC3) type(Audio)
2008-08-14 11:02:43.946 Preview: Grabbed preview '/data/recordings/live/1821_20080814110226.mpg' 1920x1088@64s
2008-08-14 11:02:51.547 TVRec(1): HW Tuner: 1->1
2008-08-14 11:02:52.773 Finished recording Unknown: channel 1831
2008-08-14 11:02:52.855 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:53.021 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:02:53.051 Empty LocalHostName.
2008-08-14 11:02:53.083 Using localhost value of kronk
2008-08-14 11:02:53.109 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(7)
2008-08-14 11:02:53.126 New DB connection, total: 1
2008-08-14 11:02:53.150 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(7)
2008-08-14 11:02:53.189 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:53.217 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(7)
2008-08-14 11:02:53.284 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(7)
2008-08-14 11:02:53.251 Closing DB connection named 'DBManager0'
2008-08-14 11:02:53.317 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(7)
2008-08-14 11:02:53.351 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:53.384 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(7)
2008-08-14 11:02:53.419 New DB connection, total: 2
2008-08-14 11:02:53.485 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:53.519 Current Schema Version: 1214
2008-08-14 11:02:53.661 Finished recording Unknown: channel 1832
2008-08-14 11:02:54.739 Finished recording Unknown: channel 1832
2008-08-14 11:02:54.827 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:02:54.978 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:02:55.013 Empty LocalHostName.
2008-08-14 11:02:55.046 Using localhost value of kronk
2008-08-14 11:02:55.088 New DB connection, total: 1
2008-08-14 11:02:55.125 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:55.155 Closing DB connection named 'DBManager0'
2008-08-14 11:02:55.188 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:55.222 New DB connection, total: 2
2008-08-14 11:02:55.255 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:02:55.289 Current Schema Version: 1214
2008-08-14 11:02:55.330 Preview Error: Previewer file '/data/recordings/live/1832_20080814110251.mpg' is not valid.
2008-08-14 11:02:55.364 Preview Error: Run() file not local: '/data/recordings/live/1832_20080814110251.mpg'
2008-08-14 11:02:55.402 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1832_20080814110251.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:02:56.015 AFD: Opened codec 0x82af3a0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:02:56.047 AFD: codec AC3 has 2 channels
2008-08-14 11:02:56.082 AFD: Opened codec 0x82af990, id(AC3) type(Audio)
2008-08-14 11:02:56.167 Preview: Grabbed preview '/data/recordings/live/1831_20080814110241.mpg' 528x480@64s
2008-08-14 11:03:03.741 TVRec(1): HW Tuner: 1->1
2008-08-14 11:03:04.973 Finished recording Unknown: channel 1832
2008-08-14 11:03:05.075 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:05.221 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:05.257 Empty LocalHostName.
2008-08-14 11:03:05.276 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(13)
2008-08-14 11:03:05.289 Using localhost value of kronk
2008-08-14 11:03:05.323 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(13)
2008-08-14 11:03:05.368 New DB connection, total: 1
2008-08-14 11:03:05.390 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(13)
2008-08-14 11:03:05.427 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:05.491 Closing DB connection named 'DBManager0'
2008-08-14 11:03:05.509 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(13)
2008-08-14 11:03:05.524 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:05.557 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(13)
2008-08-14 11:03:05.626 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(13)
2008-08-14 11:03:05.592 New DB connection, total: 2
2008-08-14 11:03:05.657 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(13)
2008-08-14 11:03:05.724 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(13)
2008-08-14 11:03:05.691 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:05.757 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(13)
2008-08-14 11:03:05.793 Current Schema Version: 1214
2008-08-14 11:03:06.041 Finished recording Unknown: channel 1833
2008-08-14 11:03:07.120 Finished recording Unknown: channel 1833
2008-08-14 11:03:07.197 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:07.356 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:07.387 Empty LocalHostName.
2008-08-14 11:03:07.420 Using localhost value of kronk
2008-08-14 11:03:07.463 New DB connection, total: 1
2008-08-14 11:03:07.500 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:07.529 Closing DB connection named 'DBManager0'
2008-08-14 11:03:07.562 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:07.597 New DB connection, total: 2
2008-08-14 11:03:07.629 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:07.664 Current Schema Version: 1214
2008-08-14 11:03:07.706 Preview Error: Previewer file '/data/recordings/live/1833_20080814110303.mpg' is not valid.
2008-08-14 11:03:07.738 Preview Error: Run() file not local: '/data/recordings/live/1833_20080814110303.mpg'
2008-08-14 11:03:07.776 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1833_20080814110303.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:03:08.308 AFD: Opened codec 0x82af230, id(MPEG2VIDEO) type(Video)
2008-08-14 11:03:08.338 AFD: codec AC3 has 2 channels
2008-08-14 11:03:08.372 AFD: Opened codec 0x82af820, id(AC3) type(Audio)
2008-08-14 11:03:08.460 Preview: Grabbed preview '/data/recordings/live/1832_20080814110253.mpg' 528x480@64s
2008-08-14 11:03:17.828 TVRec(1): HW Tuner: 1->1
2008-08-14 11:03:19.078 Finished recording Unknown: channel 1833
2008-08-14 11:03:19.170 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:19.324 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:19.325 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(11)
2008-08-14 11:03:19.367 Empty LocalHostName.
2008-08-14 11:03:19.400 Using localhost value of kronk
2008-08-14 11:03:19.416 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(11)
2008-08-14 11:03:19.459 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(11)
2008-08-14 11:03:19.443 New DB connection, total: 1
2008-08-14 11:03:19.492 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(11)
2008-08-14 11:03:19.530 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:19.550 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(11)
2008-08-14 11:03:19.585 Closing DB connection named 'DBManager0'
2008-08-14 11:03:19.617 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(11)
2008-08-14 11:03:19.676 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(11)
2008-08-14 11:03:19.651 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:19.709 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(11)
2008-08-14 11:03:19.737 New DB connection, total: 2
2008-08-14 11:03:19.768 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(11)
2008-08-14 11:03:19.802 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:19.853 Current Schema Version: 1214
2008-08-14 11:03:20.040 Finished recording Unknown: channel 1834
2008-08-14 11:03:21.114 Finished recording Unknown: channel 1834
2008-08-14 11:03:21.168 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:21.348 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:21.405 Empty LocalHostName.
2008-08-14 11:03:21.437 Using localhost value of kronk
2008-08-14 11:03:21.480 New DB connection, total: 1
2008-08-14 11:03:21.508 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:21.539 Closing DB connection named 'DBManager0'
2008-08-14 11:03:21.563 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:21.589 New DB connection, total: 2
2008-08-14 11:03:21.613 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:21.640 Current Schema Version: 1214
2008-08-14 11:03:21.680 Preview Error: Previewer file '/data/recordings/live/1834_20080814110318.mpg' is not valid.
2008-08-14 11:03:21.714 Preview Error: Run() file not local: '/data/recordings/live/1834_20080814110318.mpg'
2008-08-14 11:03:21.744 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1834_20080814110318.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:03:22.332 AFD: Opened codec 0x82af3e0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:03:22.356 AFD: codec AC3 has 2 channels
2008-08-14 11:03:22.382 AFD: Opened codec 0x82af9d0, id(AC3) type(Audio)
2008-08-14 11:03:22.492 Preview: Grabbed preview '/data/recordings/live/1833_20080814110306.mpg' 528x480@64s
2008-08-14 11:03:30.452 TVRec(1): HW Tuner: 1->1
2008-08-14 11:03:31.690 Finished recording Unknown: channel 1834
2008-08-14 11:03:31.832 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:31.906 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:31.932 Empty LocalHostName.
2008-08-14 11:03:31.965 Using localhost value of kronk
2008-08-14 11:03:32.000 New DB connection, total: 1
2008-08-14 11:03:32.028 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:32.058 Closing DB connection named 'DBManager0'
2008-08-14 11:03:32.083 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:32.104 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(8)
2008-08-14 11:03:32.109 New DB connection, total: 2
2008-08-14 11:03:32.132 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(8)
2008-08-14 11:03:32.182 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(8)
2008-08-14 11:03:32.158 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:32.207 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(8)
2008-08-14 11:03:32.235 Current Schema Version: 1214
2008-08-14 11:03:32.258 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(8)
2008-08-14 11:03:32.334 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(8)
2008-08-14 11:03:32.416 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(8)
2008-08-14 11:03:32.441 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(8)
2008-08-14 11:03:32.466 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(8)
2008-08-14 11:03:32.707 Finished recording Unknown: channel 1835
2008-08-14 11:03:33.783 Finished recording Unknown: channel 1835
2008-08-14 11:03:33.856 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:34.015 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:34.045 Empty LocalHostName.
2008-08-14 11:03:34.069 Using localhost value of kronk
2008-08-14 11:03:34.104 New DB connection, total: 1
2008-08-14 11:03:34.140 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:34.171 Closing DB connection named 'DBManager0'
2008-08-14 11:03:34.203 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:34.230 New DB connection, total: 2
2008-08-14 11:03:34.262 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:34.288 Current Schema Version: 1214
2008-08-14 11:03:34.329 Preview Error: Previewer file '/data/recordings/live/1835_20080814110330.mpg' is not valid.
2008-08-14 11:03:34.362 Preview Error: Run() file not local: '/data/recordings/live/1835_20080814110330.mpg'
2008-08-14 11:03:34.400 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1835_20080814110330.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:03:34.743 AFD: Opened codec 0x82af3a0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:03:34.771 AFD: codec AC3 has 2 channels
2008-08-14 11:03:34.797 AFD: Opened codec 0x82af990, id(AC3) type(Audio)
2008-08-14 11:03:34.829 AFD: codec AC3 has 1 channels
2008-08-14 11:03:34.855 AFD: Opened codec 0x82aff80, id(AC3) type(Audio)
2008-08-14 11:03:34.940 Preview: Grabbed preview '/data/recordings/live/1834_20080814110320.mpg' 528x480@64s
2008-08-14 11:03:44.898 TVRec(1): HW Tuner: 1->1
2008-08-14 11:03:46.127 Finished recording Unknown: channel 1835
2008-08-14 11:03:46.246 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:46.355 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:46.384 Empty LocalHostName.
2008-08-14 11:03:46.417 Using localhost value of kronk
2008-08-14 11:03:46.453 New DB connection, total: 1
2008-08-14 11:03:46.488 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:46.518 Closing DB connection named 'DBManager0'
2008-08-14 11:03:46.551 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:46.585 New DB connection, total: 2
2008-08-14 11:03:46.605 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(12)
2008-08-14 11:03:46.642 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(12)
2008-08-14 11:03:46.618 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:46.676 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(12)
2008-08-14 11:03:46.712 Current Schema Version: 1214
2008-08-14 11:03:46.743 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(12)
2008-08-14 11:03:46.793 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(12)
2008-08-14 11:03:46.835 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(12)
2008-08-14 11:03:46.868 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(12)
2008-08-14 11:03:46.953 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(12)
2008-08-14 11:03:46.985 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(12)
2008-08-14 11:03:47.285 Finished recording Unknown: channel 1836
2008-08-14 11:03:48.356 Finished recording Unknown: channel 1836
2008-08-14 11:03:48.433 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:48.587 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:48.613 Empty LocalHostName.
2008-08-14 11:03:48.646 Using localhost value of kronk
2008-08-14 11:03:48.689 New DB connection, total: 1
2008-08-14 11:03:48.725 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:48.756 Closing DB connection named 'DBManager0'
2008-08-14 11:03:48.789 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:48.857 New DB connection, total: 2
2008-08-14 11:03:48.889 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:48.923 Current Schema Version: 1214
2008-08-14 11:03:48.964 Preview Error: Previewer file '/data/recordings/live/1836_20080814110345.mpg' is not valid.
2008-08-14 11:03:48.998 Preview Error: Run() file not local: '/data/recordings/live/1836_20080814110345.mpg'
2008-08-14 11:03:49.036 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1836_20080814110345.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:03:49.217 AFD: Opened codec 0x82af3a0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:03:49.247 AFD: codec AC3 has 2 channels
2008-08-14 11:03:49.282 AFD: Opened codec 0x82af990, id(AC3) type(Audio)
2008-08-14 11:03:49.363 Preview: Grabbed preview '/data/recordings/live/1835_20080814110332.mpg' 528x480@64s
2008-08-14 11:03:58.058 TVRec(1): HW Tuner: 1->1
2008-08-14 11:03:59.300 Finished recording Unknown: channel 1836
2008-08-14 11:03:59.409 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:03:59.533 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:03:59.567 Empty LocalHostName.
2008-08-14 11:03:59.576 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(20)
2008-08-14 11:03:59.600 Using localhost value of kronk
2008-08-14 11:03:59.633 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(20)
2008-08-14 11:03:59.700 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(20)
2008-08-14 11:03:59.676 New DB connection, total: 1
2008-08-14 11:03:59.771 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:59.785 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(20)
2008-08-14 11:03:59.834 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(20)
2008-08-14 11:03:59.801 Closing DB connection named 'DBManager0'
2008-08-14 11:03:59.867 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(20)
2008-08-14 11:03:59.934 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(20)
2008-08-14 11:03:59.901 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:03:59.967 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(20)
2008-08-14 11:04:00.003 New DB connection, total: 2
2008-08-14 11:04:00.034 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(20)
2008-08-14 11:04:00.068 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:00.136 Current Schema Version: 1214
2008-08-14 11:04:00.314 Finished recording Unknown: channel 1838
2008-08-14 11:04:01.392 Finished recording Unknown: channel 1838
2008-08-14 11:04:01.463 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:01.618 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:01.646 Empty LocalHostName.
2008-08-14 11:04:01.679 Using localhost value of kronk
2008-08-14 11:04:01.721 New DB connection, total: 1
2008-08-14 11:04:01.758 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:01.788 Closing DB connection named 'DBManager0'
2008-08-14 11:04:01.821 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:01.856 New DB connection, total: 2
2008-08-14 11:04:01.888 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:01.923 Current Schema Version: 1214
2008-08-14 11:04:01.964 Preview Error: Previewer file '/data/recordings/live/1838_20080814110358.mpg' is not valid.
2008-08-14 11:04:01.997 Preview Error: Run() file not local: '/data/recordings/live/1838_20080814110358.mpg'
2008-08-14 11:04:02.035 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1838_20080814110358.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:04:02.610 AFD: Opened codec 0x82af440, id(MPEG2VIDEO) type(Video)
2008-08-14 11:04:02.639 AFD: codec AC3 has 1 channels
2008-08-14 11:04:02.673 AFD: Opened codec 0x82afa30, id(AC3) type(Audio)
2008-08-14 11:04:02.708 NVP: GetScreenGrabAtFrame: Recording does not have position map so we will be unable to grab the desired frame.

2008-08-14 11:04:02.739 Run 'mythcommflag --file 1836_20080814110347.mpg --rebuild' to fix.
2008-08-14 11:04:02.773 If that does not work and this is a .mpg file, try 'mythtranscode --mpeg2 --buildindex --allkeys -c 1836 -s 20080814110347'.
2008-08-14 11:04:02.844 Preview: Grabbed preview '/data/recordings/live/1836_20080814110347.mpg' 528x480@64s
2008-08-14 11:04:15.585 TVRec(1): HW Tuner: 1->1
2008-08-14 11:04:16.849 Finished recording Unknown: channel 1838
2008-08-14 11:04:16.987 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:17.071 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:17.100 Empty LocalHostName.
2008-08-14 11:04:17.132 Using localhost value of kronk
2008-08-14 11:04:17.175 New DB connection, total: 1
2008-08-14 11:04:17.215 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:17.215 DTVSM(0) Error: Wrong PMT; pmt->pn(36) desired(43)
2008-08-14 11:04:17.249 DTVSM(0) Error: Wrong PMT; pmt->pn(51) desired(43)
2008-08-14 11:04:17.250 Closing DB connection named 'DBManager0'
2008-08-14 11:04:17.283 DTVSM(0) Error: Wrong PMT; pmt->pn(35) desired(43)
2008-08-14 11:04:17.351 DTVSM(0) Error: Wrong PMT; pmt->pn(23) desired(43)
2008-08-14 11:04:17.321 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:17.418 New DB connection, total: 2
2008-08-14 11:04:17.433 DTVSM(0) Error: Wrong PMT; pmt->pn(46) desired(43)
2008-08-14 11:04:17.450 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:17.483 DTVSM(0) Error: Wrong PMT; pmt->pn(28) desired(43)
2008-08-14 11:04:17.550 DTVSM(0) Error: Wrong PMT; pmt->pn(31) desired(43)
2008-08-14 11:04:17.518 Current Schema Version: 1214
2008-08-14 11:04:17.583 DTVSM(0) Error: Wrong PMT; pmt->pn(47) desired(43)
2008-08-14 11:04:17.650 DTVSM(0) Error: Wrong PMT; pmt->pn(10) desired(43)
2008-08-14 11:04:17.895 Finished recording Unknown: channel 1855
2008-08-14 11:04:18.972 Finished recording Unknown: channel 1855
2008-08-14 11:04:19.028 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:19.207 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:19.237 Empty LocalHostName.
2008-08-14 11:04:19.270 Using localhost value of kronk
2008-08-14 11:04:19.312 New DB connection, total: 1
2008-08-14 11:04:19.349 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:19.379 Closing DB connection named 'DBManager0'
2008-08-14 11:04:19.412 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:19.447 New DB connection, total: 2
2008-08-14 11:04:19.479 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:19.514 Current Schema Version: 1214
2008-08-14 11:04:19.554 Preview Error: Previewer file '/data/recordings/live/1855_20080814110415.mpg' is not valid.
2008-08-14 11:04:19.588 Preview Error: Run() file not local: '/data/recordings/live/1855_20080814110415.mpg'
2008-08-14 11:04:19.626 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1855_20080814110415.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:04:20.063 AFD: Opened codec 0x82af3e0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:04:20.097 AFD: codec AC3 has 2 channels
2008-08-14 11:04:20.131 AFD: Opened codec 0x82af9d0, id(AC3) type(Audio)
2008-08-14 11:04:20.237 Preview: Grabbed preview '/data/recordings/live/1838_20080814110400.mpg' 528x480@64s
2008-08-14 11:04:26.123 Expiring 111 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:04:26.158 Expiring 0 MBytes for 1821 @ Thu Aug 14 11:02:24 2008 => Unknown
2008-08-14 11:04:26.192 Expiring 20 MBytes for 1821 @ Thu Aug 14 11:02:26 2008 => Unknown
2008-08-14 11:04:26.225 Expiring 0 MBytes for 1831 @ Thu Aug 14 11:02:39 2008 => Unknown
2008-08-14 11:04:26.259 Expiring 3 MBytes for 1831 @ Thu Aug 14 11:02:41 2008 => Unknown
2008-08-14 11:04:26.292 Expiring 0 MBytes for 1832 @ Thu Aug 14 11:02:51 2008 => Unknown
2008-08-14 11:04:26.325 Expiring 1 MBytes for 1832 @ Thu Aug 14 11:02:53 2008 => Unknown
2008-08-14 11:04:26.359 Expiring 0 MBytes for 1833 @ Thu Aug 14 11:03:03 2008 => Unknown
2008-08-14 11:04:26.392 Expiring 5 MBytes for 1833 @ Thu Aug 14 11:03:06 2008 => Unknown
2008-08-14 11:04:26.426 Expiring 0 MBytes for 1834 @ Thu Aug 14 11:03:18 2008 => Unknown
2008-08-14 11:04:30.705 TVRec(1): HW Tuner: 1->1
2008-08-14 11:04:31.917 Finished recording Unknown: channel 1855
2008-08-14 11:04:32.024 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:32.162 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:32.195 Empty LocalHostName.
2008-08-14 11:04:32.205 DTVSM(0) Error: Wrong PMT; pmt->pn(62) desired(1701)
2008-08-14 11:04:32.262 DTVSM(0) Error: Wrong PMT; pmt->pn(269) desired(1701)
2008-08-14 11:04:32.228 Using localhost value of kronk
2008-08-14 11:04:32.304 New DB connection, total: 1
2008-08-14 11:04:32.345 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:32.346 DTVSM(0) Error: Wrong PMT; pmt->pn(76) desired(1701)
2008-08-14 11:04:32.378 DTVSM(0) Error: Wrong PMT; pmt->pn(42) desired(1701)
2008-08-14 11:04:32.379 Closing DB connection named 'DBManager0'
2008-08-14 11:04:32.412 DTVSM(0) Error: Wrong PMT; pmt->pn(37) desired(1701)
2008-08-14 11:04:32.446 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:32.481 DTVSM(0) Error: Wrong PMT; pmt->pn(26) desired(1701)
2008-08-14 11:04:32.514 New DB connection, total: 2
2008-08-14 11:04:32.545 DTVSM(0) Error: Wrong PMT; pmt->pn(41) desired(1701)
2008-08-14 11:04:32.579 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:32.647 Current Schema Version: 1214
2008-08-14 11:04:32.829 Finished recording Unknown: channel 1865
2008-08-14 11:04:33.909 Finished recording Unknown: channel 1865
2008-08-14 11:04:33.973 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:34.147 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:34.182 Empty LocalHostName.
2008-08-14 11:04:34.215 Using localhost value of kronk
2008-08-14 11:04:34.257 New DB connection, total: 1
2008-08-14 11:04:34.294 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:34.325 Closing DB connection named 'DBManager0'
2008-08-14 11:04:34.357 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:34.393 New DB connection, total: 2
2008-08-14 11:04:34.424 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:34.459 Current Schema Version: 1214
2008-08-14 11:04:34.500 Preview Error: Previewer file '/data/recordings/live/1865_20080814110430.mpg' is not valid.
2008-08-14 11:04:34.533 Preview Error: Run() file not local: '/data/recordings/live/1865_20080814110430.mpg'
2008-08-14 11:04:34.572 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1865_20080814110430.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:04:35.123 AFD: Opened codec 0x82af3a0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:04:35.150 AFD: codec AC3 has 2 channels
2008-08-14 11:04:35.184 AFD: Opened codec 0x82af990, id(AC3) type(Audio)
2008-08-14 11:04:35.258 Preview: Grabbed preview '/data/recordings/live/1855_20080814110417.mpg' 352x480@64s
2008-08-14 11:04:42.513 TVRec(1): HW Tuner: 1->1
2008-08-14 11:04:43.764 Finished recording Unknown: channel 1865
2008-08-14 11:04:43.839 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:43.956 DTVSM(0) Error: Wrong PMT; pmt->pn(59) desired(77)
2008-08-14 11:04:43.991 DTVSM(0) Error: Wrong PMT; pmt->pn(69) desired(77)
2008-08-14 11:04:44.025 DTVSM(0) Error: Wrong PMT; pmt->pn(34) desired(77)
2008-08-14 11:04:43.998 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:44.058 DTVSM(0) Error: Wrong PMT; pmt->pn(48) desired(77)
2008-08-14 11:04:44.092 Empty LocalHostName.
2008-08-14 11:04:44.125 DTVSM(0) Error: Wrong PMT; pmt->pn(99) desired(77)
2008-08-14 11:04:44.158 Using localhost value of kronk
2008-08-14 11:04:44.192 DTVSM(0) Error: Wrong PMT; pmt->pn(49) desired(77)
2008-08-14 11:04:44.225 DTVSM(0) Error: Wrong PMT; pmt->pn(39) desired(77)
2008-08-14 11:04:44.234 New DB connection, total: 1
2008-08-14 11:04:44.259 DTVSM(0) Error: Wrong PMT; pmt->pn(45) desired(77)
2008-08-14 11:04:44.296 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:44.325 DTVSM(0) Error: Wrong PMT; pmt->pn(51) desired(77)
2008-08-14 11:04:44.360 Closing DB connection named 'DBManager0'
2008-08-14 11:04:44.426 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:44.461 New DB connection, total: 2
2008-08-14 11:04:44.493 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:44.528 Current Schema Version: 1214
2008-08-14 11:04:44.557 Finished recording Unknown: channel 1875
2008-08-14 11:04:45.639 Finished recording Unknown: channel 1875
2008-08-14 11:04:45.693 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:04:45.871 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:04:45.904 Empty LocalHostName.
2008-08-14 11:04:45.937 Using localhost value of kronk
2008-08-14 11:04:45.981 New DB connection, total: 1
2008-08-14 11:04:46.016 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:46.046 Closing DB connection named 'DBManager0'
2008-08-14 11:04:46.080 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:46.115 New DB connection, total: 2
2008-08-14 11:04:46.147 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:04:46.182 Current Schema Version: 1214
2008-08-14 11:04:46.222 Preview Error: Previewer file '/data/recordings/live/1875_20080814110442.mpg' is not valid.
2008-08-14 11:04:46.256 Preview Error: Run() file not local: '/data/recordings/live/1875_20080814110442.mpg'
2008-08-14 11:04:46.294 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1875_20080814110442.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:04:47.009 AFD: Opened codec 0x82af3a0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:04:47.048 AFD: codec AC3 has 1 channels
2008-08-14 11:04:47.083 AFD: Opened codec 0x82af990, id(AC3) type(Audio)
2008-08-14 11:04:47.165 Preview: Grabbed preview '/data/recordings/live/1865_20080814110432.mpg' 352x480@64s
2008-08-14 11:05:02.288 TVRec(1): HW Tuner: 1->1
2008-08-14 11:05:03.514 Finished recording Unknown: channel 1875
2008-08-14 11:05:03.613 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:05:03.675 DTVSM(0) Error: Wrong PMT; pmt->pn(77) desired(99)
2008-08-14 11:05:03.721 DTVSM(0) Error: Wrong PMT; pmt->pn(59) desired(99)
2008-08-14 11:05:03.746 DTVSM(0) Error: Wrong PMT; pmt->pn(69) desired(99)
2008-08-14 11:05:03.754 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:05:03.797 Empty LocalHostName.
2008-08-14 11:05:03.771 DTVSM(0) Error: Wrong PMT; pmt->pn(34) desired(99)
2008-08-14 11:05:03.829 Using localhost value of kronk
2008-08-14 11:05:03.854 DTVSM(0) Error: Wrong PMT; pmt->pn(48) desired(99)
2008-08-14 11:05:03.931 DTVSM(0) Error: Wrong PMT; pmt->pn(49) desired(99)
2008-08-14 11:05:03.915 New DB connection, total: 1
2008-08-14 11:05:03.963 DTVSM(0) Error: Wrong PMT; pmt->pn(39) desired(99)
2008-08-14 11:05:03.992 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:04.013 DTVSM(0) Error: Wrong PMT; pmt->pn(45) desired(99)
2008-08-14 11:05:04.039 Closing DB connection named 'DBManager0'
2008-08-14 11:05:04.063 DTVSM(0) Error: Wrong PMT; pmt->pn(51) desired(99)
2008-08-14 11:05:04.089 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:04.140 New DB connection, total: 2
2008-08-14 11:05:04.172 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:04.199 Current Schema Version: 1214
2008-08-14 11:05:04.277 Finished recording Unknown: channel 1876
2008-08-14 11:05:05.357 Finished recording Unknown: channel 1876
2008-08-14 11:05:05.406 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:05:05.590 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:05:05.617 Empty LocalHostName.
2008-08-14 11:05:05.649 Using localhost value of kronk
2008-08-14 11:05:05.684 New DB connection, total: 1
2008-08-14 11:05:05.720 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:05.751 Closing DB connection named 'DBManager0'
2008-08-14 11:05:05.784 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:05.818 New DB connection, total: 2
2008-08-14 11:05:05.850 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:05.877 Current Schema Version: 1214
2008-08-14 11:05:05.918 Preview Error: Previewer file '/data/recordings/live/1876_20080814110502.mpg' is not valid.
2008-08-14 11:05:05.951 Preview Error: Run() file not local: '/data/recordings/live/1876_20080814110502.mpg'
2008-08-14 11:05:05.997 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1876_20080814110502.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:05:06.684 AFD: Opened codec 0x82af230, id(MPEG2VIDEO) type(Video)
2008-08-14 11:05:06.710 AFD: codec AC3 has 2 channels
2008-08-14 11:05:06.736 AFD: Opened codec 0x82af820, id(AC3) type(Audio)
2008-08-14 11:05:06.820 Preview: Grabbed preview '/data/recordings/live/1875_20080814110444.mpg' 528x480@64s
2008-08-14 11:05:31.708 TVRec(1): HW Tuner: 1->1
2008-08-14 11:05:32.921 Finished recording Unknown: channel 1876
2008-08-14 11:05:33.006 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:05:33.160 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:05:33.191 Empty LocalHostName.
2008-08-14 11:05:33.224 Using localhost value of kronk
2008-08-14 11:05:33.267 New DB connection, total: 1
2008-08-14 11:05:33.272 DTVSM(0) Error: Wrong PMT; pmt->pn(3) desired(164)
2008-08-14 11:05:33.303 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:33.333 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(164)
2008-08-14 11:05:33.367 Closing DB connection named 'DBManager0'
2008-08-14 11:05:33.400 DTVSM(0) Error: Wrong PMT; pmt->pn(6) desired(164)
2008-08-14 11:05:33.433 DTVSM(0) Error: Wrong PMT; pmt->pn(4) desired(164)
2008-08-14 11:05:33.466 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(164)
2008-08-14 11:05:33.434 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:33.500 DTVSM(0) Error: Wrong PMT; pmt->pn(5) desired(164)
2008-08-14 11:05:33.535 New DB connection, total: 2
2008-08-14 11:05:33.600 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:33.616 DTVSM(0) Error: Wrong PMT; pmt->pn(484) desired(164)
2008-08-14 11:05:33.635 Current Schema Version: 1214
2008-08-14 11:05:33.667 DTVSM(0) Error: Wrong PMT; pmt->pn(1) desired(164)
2008-08-14 11:05:33.734 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(164)
2008-08-14 11:05:33.767 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(164)
2008-08-14 11:05:33.801 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(164)
2008-08-14 11:05:33.834 DTVSM(0) Error: Wrong PMT; pmt->pn(149) desired(164)
2008-08-14 11:05:34.082 Finished recording Unknown: channel 1902
2008-08-14 11:05:35.164 Finished recording Unknown: channel 1902
2008-08-14 11:05:35.241 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:05:35.394 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:05:35.421 Empty LocalHostName.
2008-08-14 11:05:35.454 Using localhost value of kronk
2008-08-14 11:05:35.497 New DB connection, total: 1
2008-08-14 11:05:35.533 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:35.563 Closing DB connection named 'DBManager0'
2008-08-14 11:05:35.597 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:35.631 New DB connection, total: 2
2008-08-14 11:05:35.663 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:05:35.698 Current Schema Version: 1214
2008-08-14 11:05:35.739 Preview Error: Previewer file '/data/recordings/live/1902_20080814110531.mpg' is not valid.
2008-08-14 11:05:35.772 Preview Error: Run() file not local: '/data/recordings/live/1902_20080814110531.mpg'
2008-08-14 11:05:35.810 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1902_20080814110531.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:05:36.145 AFD: Opened codec 0x82af3e0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:05:36.172 AFD: codec AC3 has 2 channels
2008-08-14 11:05:36.206 AFD: Opened codec 0x82af9d0, id(AC3) type(Audio)
2008-08-14 11:05:36.278 Preview: Grabbed preview '/data/recordings/live/1876_20080814110504.mpg' 352x480@64s
2008-08-14 11:06:00.083 TVRec(1): HW Tuner: 1->1
2008-08-14 11:06:01.321 Finished recording Unknown: channel 1902
2008-08-14 11:06:01.412 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:01.461 DTVSM(0) Error: Wrong PMT; pmt->pn(615) desired(6)
2008-08-14 11:06:01.510 DTVSM(0) Error: Wrong PMT; pmt->pn(616) desired(6)
2008-08-14 11:06:01.543 DTVSM(0) Error: Wrong PMT; pmt->pn(617) desired(6)
2008-08-14 11:06:01.564 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:01.577 DTVSM(0) Error: Wrong PMT; pmt->pn(613) desired(6)
2008-08-14 11:06:01.611 Empty LocalHostName.
2008-08-14 11:06:01.644 DTVSM(0) Error: Wrong PMT; pmt->pn(22) desired(6)
2008-08-14 11:06:01.711 DTVSM(0) Error: Wrong PMT; pmt->pn(612) desired(6)
2008-08-14 11:06:01.677 Using localhost value of kronk
2008-08-14 11:06:01.744 DTVSM(0) Error: Wrong PMT; pmt->pn(618) desired(6)
2008-08-14 11:06:01.786 New DB connection, total: 1
2008-08-14 11:06:01.848 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:01.878 Closing DB connection named 'DBManager0'
2008-08-14 11:06:01.911 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:01.946 New DB connection, total: 2
2008-08-14 11:06:01.973 Finished recording Unknown: channel 2161
2008-08-14 11:06:01.978 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:02.047 Current Schema Version: 1214
2008-08-14 11:06:03.058 Finished recording Unknown: channel 2161
2008-08-14 11:06:03.113 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:03.286 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:03.323 Empty LocalHostName.
2008-08-14 11:06:03.355 Using localhost value of kronk
2008-08-14 11:06:03.398 New DB connection, total: 1
2008-08-14 11:06:03.434 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:03.465 Closing DB connection named 'DBManager0'
2008-08-14 11:06:03.498 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:03.532 New DB connection, total: 2
2008-08-14 11:06:03.564 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:03.599 Current Schema Version: 1214
2008-08-14 11:06:03.640 Preview Error: Previewer file '/data/recordings/live/2161_20080814110600.mpg' is not valid.
2008-08-14 11:06:03.673 Preview Error: Run() file not local: '/data/recordings/live/2161_20080814110600.mpg'
2008-08-14 11:06:03.712 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/2161_20080814110600.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:06:04.527 AFD: Opened codec 0x82af3e0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:06:04.566 AFD: codec AC3 has 2 channels
2008-08-14 11:06:04.600 AFD: Opened codec 0x82af9d0, id(AC3) type(Audio)
2008-08-14 11:06:04.692 Preview: Grabbed preview '/data/recordings/live/1902_20080814110534.mpg' 528x480@64s
2008-08-14 11:06:12.459 TVRec(1): HW Tuner: 1->1
2008-08-14 11:06:13.710 Finished recording Unknown: channel 2161
2008-08-14 11:06:13.825 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:13.935 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:13.975 Empty LocalHostName.
2008-08-14 11:06:14.008 Using localhost value of kronk
2008-08-14 11:06:14.029 DTVSM(0) Error: Wrong PMT; pmt->pn(612) desired(22)
2008-08-14 11:06:14.051 New DB connection, total: 1
2008-08-14 11:06:14.113 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:14.124 DTVSM(0) Error: Wrong PMT; pmt->pn(618) desired(22)
2008-08-14 11:06:14.143 Closing DB connection named 'DBManager0'
2008-08-14 11:06:14.175 DTVSM(0) Error: Wrong PMT; pmt->pn(615) desired(22)
2008-08-14 11:06:14.209 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:14.242 DTVSM(0) Error: Wrong PMT; pmt->pn(616) desired(22)
2008-08-14 11:06:14.277 New DB connection, total: 2
2008-08-14 11:06:14.309 DTVSM(0) Error: Wrong PMT; pmt->pn(617) desired(22)
2008-08-14 11:06:14.344 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:14.376 DTVSM(0) Error: Wrong PMT; pmt->pn(613) desired(22)
2008-08-14 11:06:14.411 Current Schema Version: 1214
2008-08-14 11:06:14.443 DTVSM(0) Error: Wrong PMT; pmt->pn(6) desired(22)
2008-08-14 11:06:14.722 Finished recording Unknown: channel 2162
2008-08-14 11:06:15.797 Finished recording Unknown: channel 2162
2008-08-14 11:06:15.876 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:16.030 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:16.063 Empty LocalHostName.
2008-08-14 11:06:16.096 Using localhost value of kronk
2008-08-14 11:06:16.138 New DB connection, total: 1
2008-08-14 11:06:16.175 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:16.205 Closing DB connection named 'DBManager0'
2008-08-14 11:06:16.238 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:16.273 New DB connection, total: 2
2008-08-14 11:06:16.305 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:16.340 Current Schema Version: 1214
2008-08-14 11:06:16.380 Preview Error: Previewer file '/data/recordings/live/2162_20080814110612.mpg' is not valid.
2008-08-14 11:06:16.414 Preview Error: Run() file not local: '/data/recordings/live/2162_20080814110612.mpg'
2008-08-14 11:06:16.457 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/2162_20080814110612.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:06:16.923 AFD: Opened codec 0x82af220, id(MPEG2VIDEO) type(Video)
2008-08-14 11:06:16.956 AFD: codec AC3 has 2 channels
2008-08-14 11:06:16.990 AFD: Opened codec 0x82af810, id(AC3) type(Audio)
2008-08-14 11:06:17.106 Preview: Grabbed preview '/data/recordings/live/2161_20080814110602.mpg' 528x480@64s
2008-08-14 11:06:26.468 Expiring 3 MBytes for 1834 @ Thu Aug 14 11:03:20 2008 => Unknown
2008-08-14 11:06:26.499 Expiring 0 MBytes for 1835 @ Thu Aug 14 11:03:30 2008 => Unknown
2008-08-14 11:06:26.532 Expiring 3 MBytes for 1835 @ Thu Aug 14 11:03:32 2008 => Unknown
2008-08-14 11:06:26.566 Expiring 0 MBytes for 1836 @ Thu Aug 14 11:03:45 2008 => Unknown
2008-08-14 11:06:26.599 Expiring 0 MBytes for 1836 @ Thu Aug 14 11:03:47 2008 => Unknown
2008-08-14 11:06:26.633 Expiring 0 MBytes for 1838 @ Thu Aug 14 11:03:58 2008 => Unknown
2008-08-14 11:06:26.666 Expiring 5 MBytes for 1838 @ Thu Aug 14 11:04:00 2008 => Unknown
2008-08-14 11:06:26.708 Expiring 0 MBytes for 1855 @ Thu Aug 14 11:04:15 2008 => Unknown
2008-08-14 11:06:26.766 Expiring 2 MBytes for 1855 @ Thu Aug 14 11:04:17 2008 => Unknown
2008-08-14 11:06:26.808 Expiring 0 MBytes for 1865 @ Thu Aug 14 11:04:30 2008 => Unknown
2008-08-14 11:06:26.841 Expiring 1 MBytes for 1865 @ Thu Aug 14 11:04:32 2008 => Unknown
2008-08-14 11:06:26.875 Expiring 0 MBytes for 1875 @ Thu Aug 14 11:04:42 2008 => Unknown
2008-08-14 11:06:26.908 Expiring 5 MBytes for 1875 @ Thu Aug 14 11:04:44 2008 => Unknown
2008-08-14 11:06:26.942 Expiring 0 MBytes for 1876 @ Thu Aug 14 11:05:02 2008 => Unknown
2008-08-14 11:06:30.757 TVRec(1): HW Tuner: 1->1
2008-08-14 11:06:32.004 Finished recording Unknown: channel 2162
2008-08-14 11:06:32.122 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:32.229 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:32.260 Empty LocalHostName.
2008-08-14 11:06:32.293 Using localhost value of kronk
2008-08-14 11:06:32.324 DTVSM(0) Error: Wrong PMT; pmt->pn(14) desired(5)
2008-08-14 11:06:32.337 New DB connection, total: 1
2008-08-14 11:06:32.397 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:32.413 DTVSM(0) Error: Wrong PMT; pmt->pn(15) desired(5)
2008-08-14 11:06:32.428 Closing DB connection named 'DBManager0'
2008-08-14 11:06:32.460 DTVSM(0) Error: Wrong PMT; pmt->pn(16) desired(5)
2008-08-14 11:06:32.494 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:32.527 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(5)
2008-08-14 11:06:32.562 New DB connection, total: 2
2008-08-14 11:06:32.595 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(5)
2008-08-14 11:06:32.662 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(5)
2008-08-14 11:06:32.627 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:32.730 Current Schema Version: 1214
2008-08-14 11:06:32.909 Finished recording As the World Turns: channel 1021
2008-08-14 11:06:33.990 Finished recording As the World Turns: channel 1021
2008-08-14 11:06:34.049 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:34.227 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:34.256 Empty LocalHostName.
2008-08-14 11:06:34.288 Using localhost value of kronk
2008-08-14 11:06:34.334 New DB connection, total: 1
2008-08-14 11:06:34.367 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:34.398 Closing DB connection named 'DBManager0'
2008-08-14 11:06:34.431 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:34.465 New DB connection, total: 2
2008-08-14 11:06:34.497 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:34.532 Current Schema Version: 1214
2008-08-14 11:06:34.575 Preview Error: Previewer file '/data/recordings/live/1021_20080814110630.mpg' is not valid.
2008-08-14 11:06:34.607 Preview Error: Run() file not local: '/data/recordings/live/1021_20080814110630.mpg'
2008-08-14 11:06:34.645 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1021_20080814110630.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:06:35.265 AFD: Opened codec 0x82af260, id(MPEG2VIDEO) type(Video)
2008-08-14 11:06:35.299 AFD: codec AC3 has 2 channels
2008-08-14 11:06:35.333 AFD: Opened codec 0x82af850, id(AC3) type(Audio)
2008-08-14 11:06:35.429 Preview: Grabbed preview '/data/recordings/live/2162_20080814110614.mpg' 544x480@64s
2008-08-14 11:06:44.547 TVRec(1): HW Tuner: 1->1
2008-08-14 11:06:45.751 Finished recording As the World Turns: channel 1021
2008-08-14 11:06:45.862 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:45.985 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:46.020 Empty LocalHostName.
2008-08-14 11:06:46.053 Using localhost value of kronk
2008-08-14 11:06:46.057 DTVSM(0) Error: Wrong PMT; pmt->pn(99) desired(98)
2008-08-14 11:06:46.101 New DB connection, total: 1
2008-08-14 11:06:46.172 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:46.205 Closing DB connection named 'DBManager0'
2008-08-14 11:06:46.237 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:46.271 New DB connection, total: 2
2008-08-14 11:06:46.304 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:46.339 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:06:46.348 Current Schema Version: 1214
2008-08-14 11:06:47.420 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:06:47.490 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:06:47.680 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:06:47.707 Empty LocalHostName.
2008-08-14 11:06:47.731 Using localhost value of kronk
2008-08-14 11:06:47.765 New DB connection, total: 1
2008-08-14 11:06:47.802 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:47.832 Closing DB connection named 'DBManager0'
2008-08-14 11:06:47.866 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:47.900 New DB connection, total: 2
2008-08-14 11:06:47.932 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:06:47.958 Current Schema Version: 1214
2008-08-14 11:06:47.999 Preview Error: Previewer file '/data/recordings/live/1051_20080814110644.mpg' is not valid.
2008-08-14 11:06:48.033 Preview Error: Run() file not local: '/data/recordings/live/1051_20080814110644.mpg'
2008-08-14 11:06:48.070 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1051_20080814110644.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:06:48.910 AFD: Opened codec 0x82af880, id(MPEG2VIDEO) type(Video)
2008-08-14 11:06:48.942 AFD: codec AC3 has 2 channels
2008-08-14 11:06:49.060 AFD: Opened codec 0x82afe70, id(AC3) type(Audio)
2008-08-14 11:06:49.538 Preview: Grabbed preview '/data/recordings/live/1021_20080814110632.mpg' 1920x1088@64s
2008-08-14 11:08:26.984 Expiring 7 MBytes for 1876 @ Thu Aug 14 11:05:04 2008 => Unknown
2008-08-14 11:08:27.017 Expiring 0 MBytes for 1902 @ Thu Aug 14 11:05:31 2008 => Unknown
2008-08-14 11:08:27.059 Expiring 4 MBytes for 1902 @ Thu Aug 14 11:05:34 2008 => Unknown
2008-08-14 11:08:27.092 Expiring 0 MBytes for 2161 @ Thu Aug 14 11:06:00 2008 => Unknown
2008-08-14 11:08:27.126 Expiring 2 MBytes for 2161 @ Thu Aug 14 11:06:02 2008 => Unknown
2008-08-14 11:08:27.159 Expiring 0 MBytes for 2162 @ Thu Aug 14 11:06:12 2008 => Unknown
2008-08-14 11:08:27.193 Expiring 4 MBytes for 2162 @ Thu Aug 14 11:06:14 2008 => Unknown
2008-08-14 11:08:27.234 Expiring 0 MBytes for 1021 @ Thu Aug 14 11:00:00 2008 => As the World Turns
2008-08-14 11:08:27.268 Expiring 22 MBytes for 1021 @ Thu Aug 14 11:00:00 2008 => As the World Turns
2008-08-14 11:08:27.301 Expiring 0 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:09:11.845 TVRec(1): HW Tuner: 1->1
2008-08-14 11:09:13.080 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:09:13.179 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:09:13.314 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:09:13.343 Empty LocalHostName.
2008-08-14 11:09:13.376 Using localhost value of kronk
2008-08-14 11:09:13.419 New DB connection, total: 1
2008-08-14 11:09:13.463 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:09:13.472 DTVSM(0) Error: Wrong PMT; pmt->pn(650) desired(656)
2008-08-14 11:09:13.494 Closing DB connection named 'DBManager0'
2008-08-14 11:09:13.560 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:09:13.613 New DB connection, total: 2
2008-08-14 11:09:13.643 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:09:13.678 Current Schema Version: 1214
2008-08-14 11:09:13.753 Finished recording Unknown: channel 1821
2008-08-14 11:09:14.847 Finished recording Unknown: channel 1821
2008-08-14 11:09:14.938 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:09:15.117 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:09:15.147 Empty LocalHostName.
2008-08-14 11:09:15.179 Using localhost value of kronk
2008-08-14 11:09:15.222 New DB connection, total: 1
2008-08-14 11:09:15.258 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:09:15.289 Closing DB connection named 'DBManager0'
2008-08-14 11:09:15.324 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:09:15.356 New DB connection, total: 2
2008-08-14 11:09:15.388 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:09:15.423 Current Schema Version: 1214
2008-08-14 11:09:15.470 Preview Error: Previewer file '/data/recordings/live/1821_20080814110912.mpg' is not valid.
2008-08-14 11:09:15.508 Preview Error: Run() file not local: '/data/recordings/live/1821_20080814110912.mpg'
2008-08-14 11:09:15.544 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1821_20080814110912.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:09:16.221 AFD: Opened codec 0x82afa70, id(MPEG2VIDEO) type(Video)
2008-08-14 11:09:16.248 AFD: codec AC3 has 6 channels
2008-08-14 11:09:16.282 AFD: Opened codec 0x82b0060, id(AC3) type(Audio)
2008-08-14 11:09:16.802 Preview: Grabbed preview '/data/recordings/live/1051_20080814110646.mpg' 1920x1088@64s
2008-08-14 11:10:16.990 TVRec(1): Changing from WatchingLiveTV to None
2008-08-14 11:10:17.227 Finished recording Unknown: channel 1821
2008-08-14 11:10:18.911 MainServer::HandleAnnounce Playback
2008-08-14 11:10:18.943 adding: kronk as a client (events: 0)
2008-08-14 11:10:18.978 TVRec(1): Changing from None to WatchingLiveTV
2008-08-14 11:10:19.015 TVRec(1): HW Tuner: 1->1
2008-08-14 11:10:20.116 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:10:20.643 Finished recording Unknown: channel 1821
2008-08-14 11:10:21.758 Finished recording Unknown: channel 1821
2008-08-14 11:10:21.842 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:10:21.996 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:10:22.025 Empty LocalHostName.
2008-08-14 11:10:22.057 Using localhost value of kronk
2008-08-14 11:10:22.100 New DB connection, total: 1
2008-08-14 11:10:22.137 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:22.167 Closing DB connection named 'DBManager0'
2008-08-14 11:10:22.200 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:22.234 New DB connection, total: 2
2008-08-14 11:10:22.266 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:22.302 Current Schema Version: 1214
2008-08-14 11:10:22.342 Preview Error: Previewer file '/data/recordings/live/1821_20080814111019.mpg' is not valid.
2008-08-14 11:10:22.376 Preview Error: Run() file not local: '/data/recordings/live/1821_20080814111019.mpg'
2008-08-14 11:10:22.414 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1821_20080814111019.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:10:27.347 Expiring 0 MBytes for 1821 @ Thu Aug 14 11:09:12 2008 => Unknown
2008-08-14 11:10:30.044 TVRec(1): HW Tuner: 1->1
2008-08-14 11:10:31.269 Finished recording Unknown: channel 1821
2008-08-14 11:10:31.391 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:10:31.496 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:10:31.526 Empty LocalHostName.
2008-08-14 11:10:31.559 Using localhost value of kronk
2008-08-14 11:10:31.568 DTVSM(0) Error: Wrong PMT; pmt->pn(99) desired(98)
2008-08-14 11:10:31.618 New DB connection, total: 1
2008-08-14 11:10:31.657 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:31.693 Closing DB connection named 'DBManager0'
2008-08-14 11:10:31.726 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:31.761 New DB connection, total: 2
2008-08-14 11:10:31.793 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:31.824 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:10:31.828 Current Schema Version: 1214
2008-08-14 11:10:32.913 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:10:32.994 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:10:33.176 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:10:33.213 Empty LocalHostName.
2008-08-14 11:10:33.245 Using localhost value of kronk
2008-08-14 11:10:33.288 New DB connection, total: 1
2008-08-14 11:10:33.324 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:33.356 Closing DB connection named 'DBManager0'
2008-08-14 11:10:33.388 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:33.422 New DB connection, total: 2
2008-08-14 11:10:33.454 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:10:33.489 Current Schema Version: 1214
2008-08-14 11:10:33.530 Preview Error: Previewer file '/data/recordings/live/1051_20080814111030.mpg' is not valid.
2008-08-14 11:10:33.563 Preview Error: Run() file not local: '/data/recordings/live/1051_20080814111030.mpg'
2008-08-14 11:10:33.601 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1051_20080814111030.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:10:34.399 AFD: Opened codec 0x82af3b0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:10:34.431 AFD: codec AC3 has 2 channels
2008-08-14 11:10:34.457 AFD: Opened codec 0x82af9a0, id(AC3) type(Audio)
2008-08-14 11:10:35.246 Preview: Grabbed preview '/data/recordings/live/1821_20080814111020.mpg' 1920x1088@64s
2008-08-14 11:10:36.537 TVRec(1): Changing from WatchingLiveTV to None
2008-08-14 11:10:36.775 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:11:09.038 Reschedule requested for id 2.
2008-08-14 11:11:09.179 Scheduled 1 items in 0.1 = 0.09 match + 0.05 place
2008-08-14 11:12:27.394 Expiring 122 MBytes for 1821 @ Thu Aug 14 11:09:13 2008 => Unknown
2008-08-14 11:12:27.424 Expiring 0 MBytes for 1821 @ Thu Aug 14 11:10:19 2008 => Unknown
2008-08-14 11:12:27.457 Expiring 11 MBytes for 1821 @ Thu Aug 14 11:10:20 2008 => Unknown
2008-08-14 11:12:27.491 Expiring 0 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:12:27.524 Expiring 6 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:13:54.150 MainServer::HandleAnnounce Monitor
2008-08-14 11:13:54.199 adding: kronk as a client (events: 0)
2008-08-14 11:13:59.219 MainServer::HandleAnnounce Monitor
2008-08-14 11:13:59.249 adding: kronk as a client (events: 0)
2008-08-14 11:14:00.224 Reschedule requested for id 0.
2008-08-14 11:14:00.285 Scheduled 1 items in 0.1 = 0.04 match + 0.02 place
2008-08-14 11:14:02.839 MainServer::HandleAnnounce Monitor
2008-08-14 11:14:02.873 adding: kronk as a client (events: 0)
2008-08-14 11:14:22.202 MainServer::HandleAnnounce Monitor
2008-08-14 11:14:22.233 adding: kronk as a client (events: 0)
2008-08-14 11:14:26.460 MainServer::HandleAnnounce Monitor
2008-08-14 11:14:26.490 adding: kronk as a client (events: 0)
2008-08-14 11:14:29.941 TVRec(3): ASK_RECORDING 3 29 0 0
2008-08-14 11:14:31.892 MainServer::HandleAnnounce Monitor
2008-08-14 11:14:31.917 adding: kronk as a client (events: 0)
2008-08-14 11:14:56.029 MainServer::HandleAnnounce Monitor
2008-08-14 11:14:56.060 adding: kronk as a client (events: 0)
2008-08-14 11:14:58.180 MainServer::HandleAnnounce Monitor
2008-08-14 11:14:58.205 adding: kronk as a client (events: 0)
2008-08-14 11:15:02.430 TVRec(3): Changing from None to RecordingOnly
2008-08-14 11:15:02.465 TVRec(3): HW Tuner: 3->3
2008-08-14 11:15:02.549 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:15:02.581 Started recording: test (Manual Record) "Thu Aug 14 11:15:00 2008": channel 1021 on cardid 3, sourceid 1
2008-08-14 11:15:26.258 MainServer::HandleAnnounce Monitor
2008-08-14 11:15:26.289 adding: kronk as a client (events: 0)
2008-08-14 11:15:49.138 MainServer::HandleAnnounce Monitor
2008-08-14 11:15:49.163 adding: kronk as a client (events: 0)
2008-08-14 11:16:00.543 TVRec(3): Changing from RecordingOnly to None
2008-08-14 11:16:00.607 Finished recording test (Manual Record) "Thu Aug 14 11:15:00 2008": channel 1021
2008-08-14 11:16:00.608 Reschedule requested for id 0.
2008-08-14 11:16:00.690 Scheduled 0 items in 0.1 = 0.07 match + 0.01 place
2008-08-14 11:16:27.563 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:17:38.922 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:17:38.953 Empty LocalHostName.
2008-08-14 11:17:38.994 Using localhost value of kronk
2008-08-14 11:17:39.042 New DB connection, total: 1
2008-08-14 11:17:39.075 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:17:39.104 Closing DB connection named 'DBManager0'
2008-08-14 11:17:39.136 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:17:39.172 New DB connection, total: 2
2008-08-14 11:17:39.203 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:17:39.280 Current Schema Version: 1214
Starting up as the master server.
2008-08-14 11:17:39.355 New DB connection, total: 3
2008-08-14 11:17:39.387 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:17:39.489 New DB scheduler connection
2008-08-14 11:17:39.520 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:17:39.569 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-08-14 11:17:39.603 Main::Registering HttpStatus Extension
2008-08-14 11:17:39.637 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-14 11:17:39.670 Enabled verbose msgs:  important general
2008-08-14 11:17:39.706 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:17:42.557 Reschedule requested for id -1.
2008-08-14 11:17:42.641 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2008-08-14 11:17:42.681 Seem to be woken up by USER
2008-08-14 11:17:49.907 MainServer::HandleAnnounce Monitor
2008-08-14 11:17:49.948 adding: kronk as a client (events: 0)
2008-08-14 11:17:52.849 MainServer::HandleAnnounce Monitor
2008-08-14 11:17:52.878 adding: kronk as a client (events: 0)
2008-08-14 11:17:54.737 MainServer::HandleAnnounce Monitor
2008-08-14 11:17:54.773 adding: kronk as a client (events: 0)
2008-08-14 11:18:01.914 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:01.944 adding: kronk as a client (events: 0)
2008-08-14 11:18:02.030 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111500.mpg'
2008-08-14 11:18:02.062 MainServer: Failed to make preview image.
2008-08-14 11:18:02.106 Preview Error: Run() file not local: '1021_20080814111500.mpg'
2008-08-14 11:18:07.622 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:07.664 adding: kronk as a client (events: 0)
2008-08-14 11:18:07.731 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111500.mpg'
2008-08-14 11:18:07.764 MainServer: Failed to make preview image.
2008-08-14 11:18:12.994 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:13.023 adding: kronk as a client (events: 0)
2008-08-14 11:18:13.194 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:13.224 adding: kronk as a client (events: 0)
2008-08-14 11:18:16.102 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111500.mpg': No such file or directory
2008-08-14 11:18:20.049 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:20.081 adding: kronk as a client (events: 0)
2008-08-14 11:18:22.136 Reschedule requested for id 0.
2008-08-14 11:18:22.182 Scheduled 0 items in 0.0 = 0.03 match + 0.01 place
2008-08-14 11:18:26.239 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:26.268 adding: kronk as a client (events: 0)
2008-08-14 11:18:29.997 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:30.025 adding: kronk as a client (events: 0)
2008-08-14 11:18:35.696 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:35.726 adding: kronk as a client (events: 0)
2008-08-14 11:18:35.801 Reschedule requested for id 2.
2008-08-14 11:18:35.843 Scheduled 0 items in 0.0 = 0.03 match + 0.01 place
2008-08-14 11:18:36.874 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:36.904 adding: kronk as a client (events: 0)
2008-08-14 11:18:40.210 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:40.244 adding: kronk as a client (events: 0)
2008-08-14 11:18:50.300 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:50.328 adding: kronk as a client (events: 0)
2008-08-14 11:18:50.387 Reschedule requested for id 3.
2008-08-14 11:18:50.451 Scheduled 1 items in 0.1 = 0.05 match + 0.02 place
2008-08-14 11:18:50.490 TVRec(3): ASK_RECORDING 3 8 0 0
2008-08-14 11:18:51.460 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:51.489 adding: kronk as a client (events: 0)
2008-08-14 11:18:55.132 MainServer::HandleAnnounce Monitor
2008-08-14 11:18:55.154 adding: kronk as a client (events: 0)
2008-08-14 11:18:59.558 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:19:02.531 TVRec(3): Changing from None to RecordingOnly
2008-08-14 11:19:02.561 TVRec(3): HW Tuner: 3->3
2008-08-14 11:19:02.622 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:19:02.652 Started recording: 2.1 (KUTV-DT) "Thu Aug 14 11:19:00 2008": channel 1021 on cardid 3, sourceid 1
2008-08-14 11:19:02.853 MainServer::HandleAnnounce Monitor
2008-08-14 11:19:02.885 adding: kronk as a client (events: 0)
2008-08-14 11:19:42.428 MainServer::HandleAnnounce Monitor
2008-08-14 11:19:42.464 adding: kronk as a client (events: 0)
2008-08-14 11:20:00.618 TVRec(3): Changing from RecordingOnly to None
2008-08-14 11:20:00.649 Finished recording 2.1 (KUTV-DT) "Thu Aug 14 11:19:00 2008": channel 1021
2008-08-14 11:20:00.650 Reschedule requested for id 0.
2008-08-14 11:20:00.728 Scheduled 0 items in 0.1 = 0.06 match + 0.01 place
2008-08-14 11:20:03.470 MainServer::HandleAnnounce Monitor
2008-08-14 11:20:03.502 adding: kronk as a client (events: 0)
2008-08-14 11:20:07.978 MainServer::HandleAnnounce Monitor
2008-08-14 11:20:08.018 adding: kronk as a client (events: 0)
2008-08-14 11:20:08.096 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg'
2008-08-14 11:20:08.127 MainServer: Failed to make preview image.
2008-08-14 11:20:08.168 Preview Error: Run() file not local: '1021_20080814111900.mpg'
2008-08-14 11:20:46.740 MainServer::HandleAnnounce Monitor
2008-08-14 11:20:46.771 adding: kronk as a client (events: 0)
2008-08-14 11:20:46.805 MainServer::HandleAnnounce Monitor
2008-08-14 11:20:46.838 adding: kronk as a client (events: 1)
2008-08-14 11:37:57.392 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:37:57.432 Empty LocalHostName.
2008-08-14 11:37:57.474 Using localhost value of kronk
2008-08-14 11:37:57.520 New DB connection, total: 1
2008-08-14 11:37:57.555 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:37:57.583 Closing DB connection named 'DBManager0'
2008-08-14 11:37:57.616 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:37:57.651 New DB connection, total: 2
2008-08-14 11:37:57.683 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:37:57.718 Current Schema Version: 1214
Starting up as the master server.
2008-08-14 11:37:57.793 New DB connection, total: 3
2008-08-14 11:37:57.825 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:37:57.935 New DB scheduler connection
2008-08-14 11:37:57.967 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:37:58.017 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-08-14 11:37:58.050 Main::Registering HttpStatus Extension
2008-08-14 11:37:58.083 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-14 11:37:58.117 Enabled verbose msgs:  important general
2008-08-14 11:37:58.152 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:38:01.004 Reschedule requested for id -1.
2008-08-14 11:38:01.071 Scheduled 0 items in 0.1 = 0.04 match + 0.02 place
2008-08-14 11:38:01.127 Seem to be woken up by USER
2008-08-14 11:38:14.709 MainServer::HandleAnnounce Monitor
2008-08-14 11:38:14.747 adding: kronk as a client (events: 0)
2008-08-14 11:38:14.781 MainServer::HandleAnnounce Monitor
2008-08-14 11:38:14.814 adding: kronk as a client (events: 1)
2008-08-14 11:38:14.851 MainServer::HandleAnnounce Playback
2008-08-14 11:38:14.881 adding: kronk as a client (events: 0)
2008-08-14 11:38:14.916 TVRec(1): Changing from None to WatchingLiveTV
2008-08-14 11:38:14.953 TVRec(1): HW Tuner: 1->1
2008-08-14 11:38:16.064 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:38:16.909 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:38:17.993 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:38:18.069 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:38:18.234 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:38:18.263 Empty LocalHostName.
2008-08-14 11:38:18.296 Using localhost value of kronk
2008-08-14 11:38:18.339 New DB connection, total: 1
2008-08-14 11:38:18.375 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:18.405 Closing DB connection named 'DBManager0'
2008-08-14 11:38:18.438 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:18.473 New DB connection, total: 2
2008-08-14 11:38:18.505 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:18.541 Current Schema Version: 1214
2008-08-14 11:38:18.583 Preview Error: Previewer file '/data/recordings/live/1051_20080814113814.mpg' is not valid.
2008-08-14 11:38:18.614 Preview Error: Run() file not local: '/data/recordings/live/1051_20080814113814.mpg'
2008-08-14 11:38:18.652 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1051_20080814113814.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:38:42.909 TVRec(1): HW Tuner: 1->1
2008-08-14 11:38:44.116 Finished recording XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing": channel 1051
2008-08-14 11:38:44.186 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:38:44.385 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:38:44.400 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(78)
2008-08-14 11:38:44.495 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(78)
2008-08-14 11:38:44.527 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(78)
2008-08-14 11:38:44.461 Empty LocalHostName.
2008-08-14 11:38:44.560 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(78)
2008-08-14 11:38:44.608 Using localhost value of kronk
2008-08-14 11:38:44.678 New DB connection, total: 1
2008-08-14 11:38:44.714 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:44.752 Closing DB connection named 'DBManager0'
2008-08-14 11:38:44.786 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:44.821 New DB connection, total: 2
2008-08-14 11:38:44.849 Finished recording Unknown: channel 1830
2008-08-14 11:38:44.853 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:44.929 Current Schema Version: 1214
2008-08-14 11:38:45.937 Finished recording Unknown: channel 1830
2008-08-14 11:38:46.029 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:38:46.192 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:38:46.222 Empty LocalHostName.
2008-08-14 11:38:46.255 Using localhost value of kronk
2008-08-14 11:38:46.298 New DB connection, total: 1
2008-08-14 11:38:46.334 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:46.365 Closing DB connection named 'DBManager0'
2008-08-14 11:38:46.398 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:46.432 New DB connection, total: 2
2008-08-14 11:38:46.464 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:46.499 Current Schema Version: 1214
2008-08-14 11:38:46.540 Preview Error: Previewer file '/data/recordings/live/1830_20080814113843.mpg' is not valid.
2008-08-14 11:38:46.573 Preview Error: Run() file not local: '/data/recordings/live/1830_20080814113843.mpg'
2008-08-14 11:38:46.611 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1830_20080814113843.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:38:47.461 AFD: Opened codec 0x82afa80, id(MPEG2VIDEO) type(Video)
2008-08-14 11:38:47.491 AFD: codec AC3 has 6 channels
2008-08-14 11:38:47.525 AFD: Opened codec 0x82b0070, id(AC3) type(Audio)
2008-08-14 11:38:47.901 Preview: Grabbed preview '/data/recordings/live/1051_20080814113816.mpg' 1920x1088@64s
2008-08-14 11:38:57.388 TVRec(1): HW Tuner: 1->1
2008-08-14 11:38:58.647 Finished recording Unknown: channel 1830
2008-08-14 11:38:58.752 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:38:58.889 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:38:58.901 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(19)
2008-08-14 11:38:58.924 Empty LocalHostName.
2008-08-14 11:38:58.956 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(19)
2008-08-14 11:38:59.023 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(19)
2008-08-14 11:38:58.989 Using localhost value of kronk
2008-08-14 11:38:59.056 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(19)
2008-08-14 11:38:59.099 New DB connection, total: 1
2008-08-14 11:38:59.123 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(19)
2008-08-14 11:38:59.161 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:59.224 Closing DB connection named 'DBManager0'
2008-08-14 11:38:59.241 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(19)
2008-08-14 11:38:59.261 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:59.290 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(19)
2008-08-14 11:38:59.357 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(19)
2008-08-14 11:38:59.325 New DB connection, total: 2
2008-08-14 11:38:59.407 DTVSM(0) Error: Wrong PMT; pmt->pn(24) desired(19)
2008-08-14 11:38:59.441 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:38:59.509 Current Schema Version: 1214
2008-08-14 11:38:59.687 Finished recording Unknown: channel 1837
2008-08-14 11:39:00.763 Finished recording Unknown: channel 1837
2008-08-14 11:39:00.831 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:00.994 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:01.027 Empty LocalHostName.
2008-08-14 11:39:01.060 Using localhost value of kronk
2008-08-14 11:39:01.102 New DB connection, total: 1
2008-08-14 11:39:01.141 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:01.170 Closing DB connection named 'DBManager0'
2008-08-14 11:39:01.203 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:01.237 New DB connection, total: 2
2008-08-14 11:39:01.269 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:01.304 Current Schema Version: 1214
2008-08-14 11:39:01.345 Preview Error: Previewer file '/data/recordings/live/1837_20080814113857.mpg' is not valid.
2008-08-14 11:39:01.378 Preview Error: Run() file not local: '/data/recordings/live/1837_20080814113857.mpg'
2008-08-14 11:39:01.416 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1837_20080814113857.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:39:01.987 AFD: Opened codec 0x82af3b0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:39:02.020 AFD: codec AC3 has 2 channels
2008-08-14 11:39:02.055 AFD: Opened codec 0x82af9a0, id(AC3) type(Audio)
2008-08-14 11:39:02.142 Preview: Grabbed preview '/data/recordings/live/1830_20080814113844.mpg' 704x480@64s
2008-08-14 11:39:09.332 TVRec(1): HW Tuner: 1->1
2008-08-14 11:39:10.585 Finished recording Unknown: channel 1837
2008-08-14 11:39:10.691 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:10.819 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:10.855 Empty LocalHostName.
2008-08-14 11:39:10.887 Using localhost value of kronk
2008-08-14 11:39:10.892 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(24)
2008-08-14 11:39:10.954 DTVSM(0) Error: Wrong PMT; pmt->pn(78) desired(24)
2008-08-14 11:39:10.931 New DB connection, total: 1
2008-08-14 11:39:10.987 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(24)
2008-08-14 11:39:11.025 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:11.054 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(24)
2008-08-14 11:39:11.088 Closing DB connection named 'DBManager0'
2008-08-14 11:39:11.146 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:11.164 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(24)
2008-08-14 11:39:11.182 New DB connection, total: 2
2008-08-14 11:39:11.213 DTVSM(0) Error: Wrong PMT; pmt->pn(19) desired(24)
2008-08-14 11:39:11.246 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:11.280 DTVSM(0) Error: Wrong PMT; pmt->pn(20) desired(24)
2008-08-14 11:39:11.316 Current Schema Version: 1214
2008-08-14 11:39:11.347 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(24)
2008-08-14 11:39:11.380 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(24)
2008-08-14 11:39:11.681 Finished recording Unknown: channel 1839
2008-08-14 11:39:12.760 Finished recording Unknown: channel 1839
2008-08-14 11:39:12.817 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:12.991 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:13.017 Empty LocalHostName.
2008-08-14 11:39:13.049 Using localhost value of kronk
2008-08-14 11:39:13.093 New DB connection, total: 1
2008-08-14 11:39:13.130 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:13.159 Closing DB connection named 'DBManager0'
2008-08-14 11:39:13.192 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:13.226 New DB connection, total: 2
2008-08-14 11:39:13.259 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:13.293 Current Schema Version: 1214
2008-08-14 11:39:13.334 Preview Error: Previewer file '/data/recordings/live/1839_20080814113909.mpg' is not valid.
2008-08-14 11:39:13.368 Preview Error: Run() file not local: '/data/recordings/live/1839_20080814113909.mpg'
2008-08-14 11:39:13.406 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1839_20080814113909.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:39:13.832 AFD: Opened codec 0x82af3c0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:39:13.859 AFD: codec AC3 has 2 channels
2008-08-14 11:39:13.885 AFD: Opened codec 0x82af9b0, id(AC3) type(Audio)
2008-08-14 11:39:13.974 Preview: Grabbed preview '/data/recordings/live/1837_20080814113859.mpg' 704x480@64s
2008-08-14 11:39:18.009 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:22.985 TVRec(1): HW Tuner: 1->1
2008-08-14 11:39:24.235 Finished recording Unknown: channel 1839
2008-08-14 11:39:24.351 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:24.456 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:24.488 Empty LocalHostName.
2008-08-14 11:39:24.492 DTVSM(0) Error: Wrong PMT; pmt->pn(56) desired(71)
2008-08-14 11:39:24.529 Using localhost value of kronk
2008-08-14 11:39:24.529 DTVSM(0) Error: Wrong PMT; pmt->pn(57) desired(71)
2008-08-14 11:39:24.572 New DB connection, total: 1
2008-08-14 11:39:24.599 DTVSM(0) Error: Wrong PMT; pmt->pn(30) desired(71)
2008-08-14 11:39:24.634 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:24.663 DTVSM(0) Error: Wrong PMT; pmt->pn(29) desired(71)
2008-08-14 11:39:24.697 Closing DB connection named 'DBManager0'
2008-08-14 11:39:24.763 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:24.781 DTVSM(0) Error: Wrong PMT; pmt->pn(63) desired(71)
2008-08-14 11:39:24.831 DTVSM(0) Error: Wrong PMT; pmt->pn(40) desired(71)
2008-08-14 11:39:24.863 DTVSM(0) Error: Wrong PMT; pmt->pn(32) desired(71)
2008-08-14 11:39:24.798 New DB connection, total: 2
2008-08-14 11:39:24.897 DTVSM(0) Error: Wrong PMT; pmt->pn(50) desired(71)
2008-08-14 11:39:24.930 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:24.964 DTVSM(0) Error: Wrong PMT; pmt->pn(54) desired(71)
2008-08-14 11:39:24.999 Current Schema Version: 1214
2008-08-14 11:39:25.030 DTVSM(0) Error: Wrong PMT; pmt->pn(44) desired(71)
2008-08-14 11:39:25.310 Finished recording Unknown: channel 1843
2008-08-14 11:39:26.385 Finished recording Unknown: channel 1843
2008-08-14 11:39:26.442 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:26.617 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:26.651 Empty LocalHostName.
2008-08-14 11:39:26.683 Using localhost value of kronk
2008-08-14 11:39:26.726 New DB connection, total: 1
2008-08-14 11:39:26.763 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:26.793 Closing DB connection named 'DBManager0'
2008-08-14 11:39:26.826 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:26.860 New DB connection, total: 2
2008-08-14 11:39:26.893 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:26.927 Current Schema Version: 1214
2008-08-14 11:39:26.968 Preview Error: Previewer file '/data/recordings/live/1843_20080814113923.mpg' is not valid.
2008-08-14 11:39:27.002 Preview Error: Run() file not local: '/data/recordings/live/1843_20080814113923.mpg'
2008-08-14 11:39:27.040 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1843_20080814113923.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:39:27.512 AFD: Opened codec 0x82af3b0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:39:27.544 AFD: codec AC3 has 2 channels
2008-08-14 11:39:27.578 AFD: Opened codec 0x82af9a0, id(AC3) type(Audio)
2008-08-14 11:39:27.667 Preview: Grabbed preview '/data/recordings/live/1839_20080814113911.mpg' 704x480@64s
2008-08-14 11:39:34.400 TVRec(1): HW Tuner: 1->1
2008-08-14 11:39:35.619 Finished recording Unknown: channel 1843
2008-08-14 11:39:35.732 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:35.847 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:35.876 Empty LocalHostName.
2008-08-14 11:39:35.909 Using localhost value of kronk
2008-08-14 11:39:35.954 New DB connection, total: 1
2008-08-14 11:39:35.988 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:36.000 DTVSM(0) Error: Wrong PMT; pmt->pn(56) desired(32)
2008-08-14 11:39:36.054 DTVSM(0) Error: Wrong PMT; pmt->pn(57) desired(32)
2008-08-14 11:39:36.018 Closing DB connection named 'DBManager0'
2008-08-14 11:39:36.084 DTVSM(0) Error: Wrong PMT; pmt->pn(30) desired(32)
2008-08-14 11:39:36.151 DTVSM(0) Error: Wrong PMT; pmt->pn(29) desired(32)
2008-08-14 11:39:36.118 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:36.219 New DB connection, total: 2
2008-08-14 11:39:36.237 DTVSM(0) Error: Wrong PMT; pmt->pn(71) desired(32)
2008-08-14 11:39:36.251 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:36.285 DTVSM(0) Error: Wrong PMT; pmt->pn(63) desired(32)
2008-08-14 11:39:36.320 Current Schema Version: 1214
2008-08-14 11:39:36.351 DTVSM(0) Error: Wrong PMT; pmt->pn(40) desired(32)
2008-08-14 11:39:36.418 DTVSM(0) Error: Wrong PMT; pmt->pn(50) desired(32)
2008-08-14 11:39:36.452 DTVSM(0) Error: Wrong PMT; pmt->pn(54) desired(32)
2008-08-14 11:39:36.485 DTVSM(0) Error: Wrong PMT; pmt->pn(44) desired(32)
2008-08-14 11:39:36.731 Finished recording Unknown: channel 1847
2008-08-14 11:39:37.806 Finished recording Unknown: channel 1847
2008-08-14 11:39:37.862 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:38.038 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:38.072 Empty LocalHostName.
2008-08-14 11:39:38.105 Using localhost value of kronk
2008-08-14 11:39:38.147 New DB connection, total: 1
2008-08-14 11:39:38.184 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:38.214 Closing DB connection named 'DBManager0'
2008-08-14 11:39:38.247 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:38.281 New DB connection, total: 2
2008-08-14 11:39:38.314 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:38.349 Current Schema Version: 1214
2008-08-14 11:39:38.389 Preview Error: Previewer file '/data/recordings/live/1847_20080814113934.mpg' is not valid.
2008-08-14 11:39:38.423 Preview Error: Run() file not local: '/data/recordings/live/1847_20080814113934.mpg'
2008-08-14 11:39:38.461 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1847_20080814113934.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:39:38.854 AFD: Opened codec 0x82af3b0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:39:38.881 AFD: codec AC3 has 2 channels
2008-08-14 11:39:38.916 AFD: Opened codec 0x82af9a0, id(AC3) type(Audio)
2008-08-14 11:39:39.018 Preview: Grabbed preview '/data/recordings/live/1843_20080814113925.mpg' 704x480@64s
2008-08-14 11:39:47.057 TVRec(1): HW Tuner: 1->1
2008-08-14 11:39:48.308 Finished recording Unknown: channel 1847
2008-08-14 11:39:48.404 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:48.547 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:48.583 Empty LocalHostName.
2008-08-14 11:39:48.616 Using localhost value of kronk
2008-08-14 11:39:48.659 New DB connection, total: 1
2008-08-14 11:39:48.697 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:48.712 DTVSM(0) Error: Wrong PMT; pmt->pn(62) desired(76)
2008-08-14 11:39:48.734 Closing DB connection named 'DBManager0'
2008-08-14 11:39:48.800 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:48.817 DTVSM(0) Error: Wrong PMT; pmt->pn(269) desired(76)
2008-08-14 11:39:48.835 New DB connection, total: 2
2008-08-14 11:39:48.866 DTVSM(0) Error: Wrong PMT; pmt->pn(42) desired(76)
2008-08-14 11:39:48.934 DTVSM(0) Error: Wrong PMT; pmt->pn(37) desired(76)
2008-08-14 11:39:48.900 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:48.966 DTVSM(0) Error: Wrong PMT; pmt->pn(1701) desired(76)
2008-08-14 11:39:49.002 Current Schema Version: 1214
2008-08-14 11:39:49.033 DTVSM(0) Error: Wrong PMT; pmt->pn(26) desired(76)
2008-08-14 11:39:49.100 DTVSM(0) Error: Wrong PMT; pmt->pn(41) desired(76)
2008-08-14 11:39:49.346 Finished recording Unknown: channel 1863
2008-08-14 11:39:50.422 Finished recording Unknown: channel 1863
2008-08-14 11:39:50.505 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:39:50.665 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:39:50.695 Empty LocalHostName.
2008-08-14 11:39:50.728 Using localhost value of kronk
2008-08-14 11:39:50.771 New DB connection, total: 1
2008-08-14 11:39:50.807 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:50.838 Closing DB connection named 'DBManager0'
2008-08-14 11:39:50.871 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:50.905 New DB connection, total: 2
2008-08-14 11:39:50.937 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:39:50.972 Current Schema Version: 1214
2008-08-14 11:39:51.013 Preview Error: Previewer file '/data/recordings/live/1863_20080814113947.mpg' is not valid.
2008-08-14 11:39:51.046 Preview Error: Run() file not local: '/data/recordings/live/1863_20080814113947.mpg'
2008-08-14 11:39:51.084 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/1863_20080814113947.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:39:51.517 AFD: Opened codec 0x82af3b0, id(MPEG2VIDEO) type(Video)
2008-08-14 11:39:51.546 AFD: codec AC3 has 2 channels
2008-08-14 11:39:51.581 AFD: Opened codec 0x82af9a0, id(AC3) type(Audio)
2008-08-14 11:39:51.676 Preview: Grabbed preview '/data/recordings/live/1847_20080814113936.mpg' 704x480@64s
2008-08-14 11:40:06.013 TVRec(1): HW Tuner: 1->1
2008-08-14 11:40:07.224 Finished recording Unknown: channel 1863
2008-08-14 11:40:07.305 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:40:07.468 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:40:07.503 Empty LocalHostName.
2008-08-14 11:40:07.508 DTVSM(0) Error: Wrong PMT; pmt->pn(15) desired(25)
2008-08-14 11:40:07.536 Using localhost value of kronk
2008-08-14 11:40:07.570 DTVSM(0) Error: Wrong PMT; pmt->pn(1) desired(25)
2008-08-14 11:40:07.613 New DB connection, total: 1
2008-08-14 11:40:07.636 DTVSM(0) Error: Wrong PMT; pmt->pn(2) desired(25)
2008-08-14 11:40:07.670 DTVSM(0) Error: Wrong PMT; pmt->pn(6) desired(25)
2008-08-14 11:40:07.675 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:40:07.703 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(25)
2008-08-14 11:40:07.738 Closing DB connection named 'DBManager0'
2008-08-14 11:40:07.804 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:40:07.820 DTVSM(0) Error: Wrong PMT; pmt->pn(4) desired(25)
2008-08-14 11:40:07.839 New DB connection, total: 2
2008-08-14 11:40:07.870 DTVSM(0) Error: Wrong PMT; pmt->pn(3) desired(25)
2008-08-14 11:40:07.904 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:40:07.940 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(25)
2008-08-14 11:40:08.004 DTVSM(0) Error: Wrong PMT; pmt->pn(5) desired(25)
2008-08-14 11:40:07.972 Current Schema Version: 1214
2008-08-14 11:40:08.037 DTVSM(0) Error: Wrong PMT; pmt->pn(10) desired(25)
2008-08-14 11:40:08.104 DTVSM(0) Error: Wrong PMT; pmt->pn(14) desired(25)
2008-08-14 11:40:08.351 Finished recording Unknown: channel 2163
2008-08-14 11:40:09.426 Finished recording Unknown: channel 2163
2008-08-14 11:40:09.504 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:40:09.658 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:40:09.691 Empty LocalHostName.
2008-08-14 11:40:09.724 Using localhost value of kronk
2008-08-14 11:40:09.766 New DB connection, total: 1
2008-08-14 11:40:09.803 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:40:09.833 Closing DB connection named 'DBManager0'
2008-08-14 11:40:09.866 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:40:09.901 New DB connection, total: 2
2008-08-14 11:40:09.933 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:40:09.968 Current Schema Version: 1214
2008-08-14 11:40:10.011 Preview Error: Previewer file '/data/recordings/live/2163_20080814114006.mpg' is not valid.
2008-08-14 11:40:10.042 Preview Error: Run() file not local: '/data/recordings/live/2163_20080814114006.mpg'
2008-08-14 11:40:10.080 Preview Error: Preview process not ok.
			fileinfo(/data/recordings/live/2163_20080814114006.mpg.png) exists: 0 readable: 0 size: 0
2008-08-14 11:40:10.530 AFD: Opened codec 0x82af330, id(MPEG2VIDEO) type(Video)
2008-08-14 11:40:10.559 AFD: codec AC3 has 2 channels
2008-08-14 11:40:10.593 AFD: Opened codec 0x82af920, id(AC3) type(Audio)
2008-08-14 11:40:10.680 Preview: Grabbed preview '/data/recordings/live/1863_20080814113949.mpg' 704x480@64s
2008-08-14 11:40:18.059 Expiring 0 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:40:18.089 Expiring 24 MBytes for 1051 @ Thu Aug 14 10:00:00 2008 => XXIX Summer Olympics "Beach Volleyball, Swimming, Rowing"
2008-08-14 11:40:18.123 Expiring 0 MBytes for 1830 @ Thu Aug 14 11:38:43 2008 => Unknown
2008-08-14 11:40:18.156 Expiring 2 MBytes for 1830 @ Thu Aug 14 11:38:44 2008 => Unknown
2008-08-14 11:40:18.189 Expiring 0 MBytes for 1837 @ Thu Aug 14 11:38:57 2008 => Unknown
2008-08-14 11:40:18.223 Expiring 1 MBytes for 1837 @ Thu Aug 14 11:38:59 2008 => Unknown
2008-08-14 11:40:18.256 Expiring 0 MBytes for 1839 @ Thu Aug 14 11:39:09 2008 => Unknown
2008-08-14 11:40:18.290 Expiring 1 MBytes for 1839 @ Thu Aug 14 11:39:11 2008 => Unknown
2008-08-14 11:40:18.323 Expiring 0 MBytes for 1843 @ Thu Aug 14 11:39:23 2008 => Unknown
2008-08-14 11:40:20.341 TVRec(1): Changing from WatchingLiveTV to None
2008-08-14 11:40:20.597 Finished recording Unknown: channel 2163
2008-08-14 11:46:53.847 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 11:46:53.888 Empty LocalHostName.
2008-08-14 11:46:53.945 Using localhost value of kronk
2008-08-14 11:46:53.986 New DB connection, total: 1
2008-08-14 11:46:54.026 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:46:54.063 Closing DB connection named 'DBManager0'
2008-08-14 11:46:54.096 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:46:54.130 New DB connection, total: 2
2008-08-14 11:46:54.162 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:46:54.191 Current Schema Version: 1214
Starting up as the master server.
2008-08-14 11:46:54.265 New DB connection, total: 3
2008-08-14 11:46:54.296 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:46:54.376 New DB scheduler connection
2008-08-14 11:46:54.404 Connected to database 'mythconverg' at host: localhost
2008-08-14 11:46:54.450 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-08-14 11:46:54.504 Main::Registering HttpStatus Extension
2008-08-14 11:46:54.529 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-08-14 11:46:54.563 Enabled verbose msgs:  important general
2008-08-14 11:46:54.598 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:46:57.433 Reschedule requested for id -1.
2008-08-14 11:46:57.504 Scheduled 0 items in 0.1 = 0.04 match + 0.03 place
2008-08-14 11:46:57.541 Seem to be woken up by USER
2008-08-14 11:47:27.987 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:28.025 adding: kronk as a client (events: 0)
2008-08-14 11:47:28.460 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:28.493 adding: kronk as a client (events: 0)
2008-08-14 11:47:29.947 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:29.987 adding: kronk as a client (events: 0)
2008-08-14 11:47:30.271 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:30.305 adding: kronk as a client (events: 0)
2008-08-14 11:47:31.753 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:31.782 adding: kronk as a client (events: 0)
2008-08-14 11:47:31.931 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg'
2008-08-14 11:47:31.967 MainServer: Failed to make preview image.
2008-08-14 11:47:32.156 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:32.192 adding: kronk as a client (events: 0)
2008-08-14 11:47:37.348 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:37.384 adding: kronk as a client (events: 0)
2008-08-14 11:47:37.509 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg'
2008-08-14 11:47:37.544 MainServer: Failed to make preview image.
2008-08-14 11:47:37.585 MythSocket(8279e18:-1): writeStringList: Error, socket went unconnected.
2008-08-14 11:47:37.688 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:37.719 adding: kronk as a client (events: 0)
2008-08-14 11:47:43.475 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:43.512 adding: kronk as a client (events: 0)
2008-08-14 11:47:43.637 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg'
2008-08-14 11:47:43.672 MainServer: Failed to make preview image.
2008-08-14 11:47:43.865 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:43.897 adding: kronk as a client (events: 0)
2008-08-14 11:47:44.319 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:44.356 adding: kronk as a client (events: 0)
2008-08-14 11:47:44.483 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg'
2008-08-14 11:47:44.523 MainServer: Failed to make preview image.
2008-08-14 11:47:44.568 Preview Error: Run() file not local: '1021_20080814111900.mpg'
2008-08-14 11:47:44.708 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:44.740 adding: kronk as a client (events: 0)
2008-08-14 11:47:50.783 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:50.818 adding: kronk as a client (events: 0)
2008-08-14 11:47:50.945 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg'
2008-08-14 11:47:50.977 MainServer: Failed to make preview image.
2008-08-14 11:47:51.171 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:51.202 adding: kronk as a client (events: 0)
2008-08-14 11:47:54.388 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:54.424 adding: kronk as a client (events: 0)
2008-08-14 11:47:54.641 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:54.675 adding: kronk as a client (events: 0)
2008-08-14 11:47:55.000 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:55.034 adding: kronk as a client (events: 0)
2008-08-14 11:47:57.563 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1021_20080814111900.mpg': No such file or directory
2008-08-14 11:47:57.825 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:57.864 adding: kronk as a client (events: 0)
2008-08-14 11:47:58.163 MainServer::HandleAnnounce Monitor
2008-08-14 11:47:58.207 adding: kronk as a client (events: 0)
2008-08-14 11:48:03.601 Reschedule requested for id 0.
2008-08-14 11:48:03.650 Scheduled 0 items in 0.0 = 0.03 match + 0.01 place
2008-08-14 11:48:05.745 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:05.781 adding: kronk as a client (events: 0)
2008-08-14 11:48:05.841 Reschedule requested for id 4.
2008-08-14 11:48:05.901 Scheduled 1 items in 0.1 = 0.04 match + 0.02 place
2008-08-14 11:48:05.935 TVRec(3): ASK_RECORDING 3 0 0 0
2008-08-14 11:48:06.133 TVRec(3): Changing from None to RecordingOnly
2008-08-14 11:48:06.168 TVRec(3): HW Tuner: 3->3
2008-08-14 11:48:06.225 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:48:06.259 Started recording: 1 (DSC) "Thu Aug 14 11:48:00 2008": channel 1843 on cardid 3, sourceid 1
2008-08-14 11:48:06.903 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:06.934 adding: kronk as a client (events: 0)
2008-08-14 11:48:07.245 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:07.276 adding: kronk as a client (events: 0)
2008-08-14 11:48:08.592 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:08.620 adding: kronk as a client (events: 0)
2008-08-14 11:48:08.881 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:08.913 adding: kronk as a client (events: 0)
2008-08-14 11:48:14.440 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-14 11:48:14.477 Expiring 2 MBytes for 1843 @ Thu Aug 14 11:39:25 2008 => Unknown
2008-08-14 11:48:14.506 Expiring 0 MBytes for 1847 @ Thu Aug 14 11:39:34 2008 => Unknown
2008-08-14 11:48:14.540 Expiring 1 MBytes for 1847 @ Thu Aug 14 11:39:36 2008 => Unknown
2008-08-14 11:48:14.573 Expiring 0 MBytes for 1863 @ Thu Aug 14 11:39:47 2008 => Unknown
2008-08-14 11:48:14.606 Expiring 4 MBytes for 1863 @ Thu Aug 14 11:39:49 2008 => Unknown
2008-08-14 11:48:14.640 Expiring 0 MBytes for 2163 @ Thu Aug 14 11:40:06 2008 => Unknown
2008-08-14 11:48:14.673 Expiring 5 MBytes for 2163 @ Thu Aug 14 11:40:08 2008 => Unknown
2008-08-14 11:48:41.451 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:41.481 adding: kronk as a client (events: 0)
2008-08-14 11:48:41.801 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:41.832 adding: kronk as a client (events: 0)
2008-08-14 11:48:45.283 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:45.321 adding: kronk as a client (events: 0)
2008-08-14 11:48:45.572 MainServer::HandleAnnounce Monitor
2008-08-14 11:48:45.606 adding: kronk as a client (events: 0)
2008-08-14 11:49:00.223 TVRec(3): Changing from RecordingOnly to None
2008-08-14 11:49:00.294 Finished recording 1 (DSC) "Thu Aug 14 11:48:00 2008": channel 1843
2008-08-14 11:49:00.295 Reschedule requested for id 0.
2008-08-14 11:49:00.376 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2008-08-14 11:49:04.156 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:04.190 adding: kronk as a client (events: 0)
2008-08-14 11:49:04.454 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:04.615 adding: kronk as a client (events: 0)
2008-08-14 11:49:06.310 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:06.344 adding: kronk as a client (events: 0)
2008-08-14 11:49:06.587 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:06.619 adding: kronk as a client (events: 0)
2008-08-14 11:49:07.202 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:07.237 adding: kronk as a client (events: 0)
2008-08-14 11:49:07.323 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1843_20080814114800.mpg'
2008-08-14 11:49:07.354 MainServer: Failed to make preview image.
2008-08-14 11:49:07.396 Preview Error: Run() file not local: '1843_20080814114800.mpg'
2008-08-14 11:49:07.544 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:07.580 adding: kronk as a client (events: 0)
2008-08-14 11:49:10.542 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:10.577 adding: kronk as a client (events: 0)
2008-08-14 11:49:10.664 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1843_20080814114800.mpg'
2008-08-14 11:49:10.694 MainServer: Failed to make preview image.
2008-08-14 11:49:10.809 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:10.836 adding: kronk as a client (events: 0)
2008-08-14 11:49:14.183 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:14.217 adding: kronk as a client (events: 0)
2008-08-14 11:49:14.303 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/kronk/1843_20080814114800.mpg'
2008-08-14 11:49:14.334 MainServer: Failed to make preview image.
2008-08-14 11:49:14.451 MainServer::HandleAnnounce Monitor
2008-08-14 11:49:14.593 adding: kronk as a client (events: 0)
2008-08-14 11:59:16.202 MainServer::HandleAnnounce Monitor
2008-08-14 11:59:16.233 adding: kronk as a client (events: 0)
2008-08-14 11:59:16.267 MainServer::HandleAnnounce Monitor
2008-08-14 11:59:16.300 adding: kronk as a client (events: 1)
2008-08-14 11:59:16.335 Reschedule requested for id -1.
2008-08-14 11:59:16.445 Scheduled 0 items in 0.1 = 0.04 match + 0.06 place
2008-08-14 12:03:14.749 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

I noticed that the frontend didn't log anything from today, so I will not post it.

I first noticed this happening (before I formatted the system) when I changed the IP addresses in mythtv-setup to 10.0.0.2 (on both).  When the first one was set to 127.0.0.1 and the second one to 10.0.0.2, I could not schedule recordings.  I tried updating MythTV to the latest build with Synaptic, but same results.  Then I reloaded, set both IPs to 10.0.0.2 and cannot record again.  Is this a bug?

If anyone has seen this before, please let me know.  Thanks!

Jon

---

### Post by dibble5504 on 2008-09-10
I am having a similar problem.  IP addresses are static on my FE and BE so they have not caused a problem.  I haven't had a successful recording since 2008-09-03 (1 week) which is about the time that I had an apt upgrade on mythtv.  Coincidence??

---

