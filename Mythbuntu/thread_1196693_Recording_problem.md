---
title: "Recording problem"
date: 2009-06-25
forum: Mythbuntu
---

### Post by peterhocking on 2009-06-25
Hi

Whenever I schedule a TV show to be recorded, the resulting files is always an empty file. But when ever I start the recording while I am watching the show I want recorded, it successfully rrecords the show & I can play it back.

I'm using:
Mythbuntu 9.04 64 bit, updated with fixes branch
HD Homerun Tuner
Athlon 2800, Socket 754
Gigabyte motherboard
2 gig RAM
500 gig SATA hard drive
Pioneer SATA DVD burner

TIA

Peter

---

### Post by tgm4883 on 2009-06-25
please post your backend logs

/var/log/mythtv/mythbackend.log

---

### Post by peterhocking on 2009-06-26
> **tgm4883 said:**
> please post your backend logs

/var/log/mythtv/mythbackend.log

Hi

Thanks for your reply

Yesterday I attempted to record the same show twice, once was scheduled, (on ABC HD) which failed & the other one was on ABC1 which I started manually while watching it on Live TV. That one succeeded.

Below yesterdays log I'll put the log of another attempted recording that failed today.

Here is yesterdays log;

2009-06-25 23:24:28.248 TVRec(1): Changing from None to RecordingOnly
2009-06-25 23:24:28.412 TVRec(1): HW Tuner: 1->1
2009-06-25 23:24:28.414 HDHRChan(12108420/0): device found at address
192.168.11.78
2009-06-25 23:24:28.454 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-25 23:24:28.460 Started recording: Live at the Basement "Guy
Sebastian": channel 1020 on cardid 1, sourceid 1
2009-06-25 23:24:47.871 MainServer::HandleAnnounce Monitor
2009-06-25 23:24:47.875 adding: tv-server as a client (events: 0)
2009-06-25 23:24:50.903 MainServer::HandleAnnounce Monitor
2009-06-25 23:24:50.907 adding: tv-server as a client (events: 0)
2009-06-25 23:25:09.488 MainServer::HandleAnnounce Monitor
2009-06-25 23:25:09.496 adding: tv-server as a client (events: 0)
2009-06-25 23:25:09.498 MainServer::HandleAnnounce Monitor
2009-06-25 23:25:09.500 adding: tv-server as a client (events: 1)
2009-06-25 23:25:09.506 MainServer::HandleAnnounce Playback
2009-06-25 23:25:09.508 adding: tv-server as a client (events: 0)
2009-06-25 23:25:09.511 TVRec(2): Changing from None to WatchingLiveTV
2009-06-25 23:25:09.517 TVRec(2): HW Tuner: 2->2
2009-06-25 23:25:09.519 HDHRChan(12108420/1): device found at address
192.168.11.78
2009-06-25 23:25:10.580 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-25 23:25:11.722 Finished recording Live at the Basement "Guy
Sebastian": channel 1002
2009-06-25 23:25:12.772 Finished recording Live at the Basement "Guy
Sebastian": channel 1002
2009-06-25 23:25:12.842 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-25 23:25:13.105 Using runtime prefix = /usr
2009-06-25 23:25:13.124 Empty LocalHostName.
2009-06-25 23:25:13.125 Using localhost value of tv-server
2009-06-25 23:25:13.140 New DB connection, total: 1
2009-06-25 23:25:13.157 Connected to database 'mythconverg' at host:
localhost
2009-06-25 23:25:13.159 Closing DB connection named 'DBManager0'
2009-06-25 23:25:13.163 Connected to database 'mythconverg' at host:
localhost
2009-06-25 23:25:13.168 New DB connection, total: 2
2009-06-25 23:25:13.171 Connected to database 'mythconverg' at host:
localhost
2009-06-25 23:25:13.178 Current Schema Version: 1214
2009-06-25 23:25:13.193 Preview Error: Previewer file
'/var/lib/mythtv/recordings/Test/1002_20090625232509.mpg' is not valid.
2009-06-25 23:25:13.195 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/Test/1002_20090625232509.mpg'
2009-06-25 23:25:13.212 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/Test/1002_20090625232509.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-25 23:26:32.480 Expiring 0 MBytes for 1002 @ Thu Jun 25 23:25:00
2009 => Live at the Basement "Guy Sebastian"
2009-06-25 23:27:18.011 TVRec(2): SetLiveRecording(1)
2009-06-25 23:27:18.026 TVRec(2): SetLiveRecording() -- record
2009-06-25 23:27:18.126 Scheduler: AddRecording() recid: 37
2009-06-25 23:27:18.225 Reschedule requested for id 37.
2009-06-25 23:27:18.509 Scheduled 16 items in 0.2 = 0.03 match + 0.18
place
2009-06-25 23:27:27.550 TVRec(2): Changing from WatchingLiveTV to
RecordingOnly
2009-06-25 23:27:32.490 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-25 23:27:38.191 MainServer::HandleAnnounce Monitor
2009-06-25 23:27:38.197 adding: tv-server as a client (events: 0)
2009-06-25 23:35:32.545 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-25 23:41:34.868 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-25 23:41:34.871 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-25 23:43:32.582 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-25 23:51:32.621 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-25 23:59:32.657 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-26 00:07:32.700 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-26 00:11:34.873 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-26 00:11:34.879 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-26 00:12:17.447 MainServer::HandleAnnounce Monitor
2009-06-26 00:12:17.487 adding: tv-server as a client (events: 0)
2009-06-26 00:12:17.488 MainServer::HandleAnnounce Monitor
2009-06-26 00:12:17.490 adding: tv-server as a client (events: 1)
2009-06-26 00:12:17.495 Reschedule requested for id -1.
2009-06-26 00:12:17.622 Scheduled 16 items in 0.1 = 0.02 match + 0.10
place
2009-06-26 00:15:32.740 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-26 00:23:32.785 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 8 min
2009-06-26 00:25:30.014 TVRec(2): Changing from RecordingOnly to None
2009-06-26 00:25:30.929 TVRec(1): Changing from RecordingOnly to None
2009-06-26 00:25:30.939 Finished recording Live at the Basement "Guy
Sebastian": channel 1020
2009-06-26 00:25:30.967 Reschedule requested for id 0.
2009-06-26 00:25:31.025 Scheduled 15 items in 0.1 = 0.00 match + 0.05
place
2009-06-26 00:25:31.079 Reschedule requested for id 0.
2009-06-26 00:25:31.080 Finished recording Live at the Basement "Guy
Sebastian": channel 1002
2009-06-26 00:25:31.167 Scheduled 14 items in 0.1 = 0.02 match + 0.05
place
2009-06-26 00:25:31.326 Using runtime prefix = /usr
2009-06-26 00:25:31.333 Empty LocalHostName.
2009-06-26 00:25:31.335 Using localhost value of tv-server
2009-06-26 00:25:31.348 New DB connection, total: 1
2009-06-26 00:25:31.355 Connected to database 'mythconverg' at host:
localhost
2009-06-26 00:25:31.358 Closing DB connection named 'DBManager0'
2009-06-26 00:25:31.359 Connected to database 'mythconverg' at host:
localhost
2009-06-26 00:25:31.368 New DB connection, total: 2
2009-06-26 00:25:31.375 Connected to database 'mythconverg' at host:
localhost
2009-06-26 00:25:31.385 Current Schema Version: 1214
2009-06-26 00:25:31.973 Finished recording Live at the Basement "Guy
Sebastian": channel 1020
2009-06-26 00:25:32.126 Using runtime prefix = /usr
2009-06-26 00:25:32.131 Empty LocalHostName.
2009-06-26 00:25:32.132 Using localhost value of tv-server
2009-06-26 00:25:32.151 New DB connection, total: 1
2009-06-26 00:25:32.159 Connected to database 'mythconverg' at host:
localhost
2009-06-26 00:25:32.162 Closing DB connection named 'DBManager0'
2009-06-26 00:25:32.167 Connected to database 'mythconverg' at host:
localhost
2009-06-26 00:25:32.176 New DB connection, total: 2
2009-06-26 00:25:32.183 Connected to database 'mythconverg' at host:
localhost
2009-06-26 00:25:32.192 Current Schema Version: 1214
2009-06-26 00:25:32.206 Preview Error: Previewer file
'/var/lib/mythtv/recordings/Test/1020_20090625232400.mpg' is not valid.
2009-06-26 00:25:32.208 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/Test/1020_20090625232400.mpg'
2009-06-26 00:25:32.224 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/Test/1020_20090625232400.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-26 00:25:33.990 AFD: Opened codec 0xfd6ec0, id(MPEG2VIDEO)
type(Video)
2009-06-26 00:25:33.994 AFD: codec MP3 has 2 channels
2009-06-26 00:25:33.995 AFD: Opened codec 0xfd72a0, id(MP3) type(Audio)
2009-06-26 00:25:34.003 AFD: codec AC3 has 2 channels
2009-06-26 00:25:34.011 AFD: Opened codec 0xfd7780, id(AC3) type(Audio)
2009-06-26 00:25:34.019 AFD: Stream #3 is MPEG1VIDEO with 0 bit rate,
skipping.
2009-06-26 00:25:34.027 AFD: Stream #4 is MPEG1VIDEO with 0 bit rate,
skipping.
2009-06-26 00:25:34.243 Preview: Grabbed preview
'/var/lib/mythtv/recordings/Test/1002_20090625232511.mpg' 720x576@97s
2009-06-26 00:31:32.817 AutoExpire: CalcParams(): Max required Free
Space: 1.0 GB w/freq: 15 min


Log from today's failed scheduled recording;

2009-06-26 14:26:23.847 MainServer::HandleAnnounce Monitor
2009-06-26 14:26:23.852 adding: tv-server as a client (events: 0)
2009-06-26 14:26:23.853 MainServer::HandleAnnounce Monitor
2009-06-26 14:26:23.854 adding: tv-server as a client (events: 1)
2009-06-26 14:26:23.856 Reschedule requested for id -1.
2009-06-26 14:26:23.900 Scheduled 14 items in 0.0 = 0.01 match + 0.03
place
2009-06-26 14:28:27.916 Reschedule requested for id 0.
2009-06-26 14:28:27.963 Scheduled 14 items in 0.0 = 0.00 match + 0.04
place
2009-06-26 14:28:57.548 TVRec(1): ASK_RECORDING 1 29 0 0
2009-06-26 14:29:28.150 TVRec(1): Changing from None to RecordingOnly
2009-06-26 14:29:28.152 TVRec(1): HW Tuner: 1->1
2009-06-26 14:29:28.178 HDHRChan(12108420/0): device found at address
192.168.11.78
2009-06-26 14:29:28.309 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-26 14:29:28.312 Started recording: In Search of Bony: channel
1030 on cardid 1, sourceid 1
2009-06-26 14:31:35.710 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-26 14:43:23.170 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-26 14:43:23.175 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-26 14:46:35.764 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-26 15:01:35.810 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-26 15:13:26.177 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-26 15:13:26.179 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-26 15:16:35.856 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-26 15:27:09.530 MainServer::HandleAnnounce Monitor
2009-06-26 15:27:09.536 adding: tv-server as a client (events: 0)
2009-06-26 15:27:09.537 MainServer::HandleAnnounce Monitor
2009-06-26 15:27:09.538 adding: tv-server as a client (events: 1)
2009-06-26 15:27:09.540 Reschedule requested for id -1.
2009-06-26 15:27:09.585 Scheduled 14 items in 0.0 = 0.01 match + 0.03
place
2009-06-26 15:30:30.363 TVRec(1): Changing from RecordingOnly to None
2009-06-26 15:30:30.372 Finished recording In Search of Bony: channel
1030
2009-06-26 15:30:30.373 Reschedule requested for id 0.
2009-06-26 15:30:30.422 Scheduled 13 items in 0.0 = 0.00 match + 0.04
place
2009-06-26 15:30:31.416 Finished recording In Search of Bony: channel
1030
2009-06-26 15:30:31.674 Using runtime prefix = /usr
2009-06-26 15:30:31.685 Empty LocalHostName.
2009-06-26 15:30:31.686 Using localhost value of tv-server
2009-06-26 15:30:31.711 New DB connection, total: 1
2009-06-26 15:30:31.719 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:30:31.721 Closing DB connection named 'DBManager0'
2009-06-26 15:30:31.723 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:30:31.749 New DB connection, total: 2
2009-06-26 15:30:31.751 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:30:31.757 Current Schema Version: 1214
2009-06-26 15:30:31.775 Preview Error: Previewer file
'/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg' is not valid.
2009-06-26 15:30:31.777 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg'
2009-06-26 15:30:31.792 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-26 15:31:23.103 JobQueue: Commercial Flagging Starting for In
Search of Bony recorded from channel 1030 at Fri Jun 26 14:29:00 2009
2009-06-26 15:31:23.273 Using runtime prefix = /usr
2009-06-26 15:31:23.277 Empty LocalHostName.
2009-06-26 15:31:23.278 Using localhost value of tv-server
2009-06-26 15:31:23.291 New DB connection, total: 1
2009-06-26 15:31:23.298 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:31:23.301 Closing DB connection named 'DBManager0'
2009-06-26 15:31:23.307 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:31:23.319 New DB connection, total: 2
2009-06-26 15:31:23.323 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:31:29.832
RingBuf(/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg):
Invalid file (fd -1) when opening
'/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg'.
2009-06-26 15:31:29.914 Connecting to backend server:
192.168.11.111:6543 (try 1 of 5)
2009-06-26 15:31:29.917 Using protocol version 40
2009-06-26 15:31:29.918 MainServer::HandleAnnounce Monitor
2009-06-26 15:31:29.926 adding: tv-server as a client (events: 0)
2009-06-26 15:31:29.935 MainServer::HandleAnnounce Monitor
2009-06-26 15:31:29.942 adding: tv-server as a client (events: 1)
2009-06-26 15:31:29.980 NVP::OpenFile(): Error, file not
found: /var/lib/mythtv/recordings/Test/1030_20090626142900.mpg
2009-06-26 15:31:30.156 Using runtime prefix = /usr
2009-06-26 15:31:30.161 Empty LocalHostName.
2009-06-26 15:31:30.162 Using localhost value of tv-server
2009-06-26 15:31:30.182 New DB connection, total: 1
2009-06-26 15:31:30.189 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:31:30.191 Closing DB connection named 'DBManager0'
2009-06-26 15:31:30.199 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:31:30.208 New DB connection, total: 2
2009-06-26 15:31:30.215 Connected to database 'mythconverg' at host:
localhost
2009-06-26 15:31:30.225 Current Schema Version: 1214
2009-06-26 15:31:30.239 Preview Error: Previewer file
'/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg' is not valid.
2009-06-26 15:31:30.241 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg'
2009-06-26 15:31:30.256 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/Test/1030_20090626142900.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-26 15:31:35.902 AutoExpire: CalcParams(): Max required Free
Space: 1.0 GB w/freq: 15 min
2009-06-26 15:31:35.910 Expiring 956 MBytes for 1006 @ Thu Jun 25
15:00:00 2009 => New Idea TV
2009-06-26 15:31:35.976 ERROR when trying to delete
file: /var/lib/mythtv/recordings/1006_20090625151239.mpg/1006_20090625151239.mpg. File doesn't exist.  Database metadata will not be removed.
2009-06-26 15:43:30.182 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-26 15:43:30.187 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-26 15:46:35.959 AutoExpire: CalcParams(): Max required Free
Space: 1.0 GB w/freq: 15 min
2009-06-26 15:46:35.966 Expiring 956 MBytes for 1006 @ Thu Jun 25
15:00:00 2009 => New Idea TV
2009-06-26 15:46:35.967 Expiring 564 MBytes for 1006 @ Thu Jun 25
15:30:00 2009 => All for Kids
2009-06-26 15:46:35.970 ERROR when trying to delete
file: /var/lib/mythtv/recordings/1006_20090625151239.mpg/1006_20090625151239.mpg. File doesn't exist.  Database metadata will not be removed.
2009-06-26 15:46:35.996 ERROR when trying to delete

If you want the whole log I'm happy to email it to you.

Thanks for your help.

Peter

---

