---
title: "Mythtv .20 Backend Crashing on Feisty"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by yankeeprof on 2007-11-06
Ever since upgrading Mythtv to .20 so I could subscribe to Schedule Direct, I've been experiencing random crashes of my backend  server.  I have Monit installed so  when it crashes the backend  automatically starts but yesterday it crashed several times as I was watching my beloved bills.  I've looked at my backend log and there is nothing that stands out as the cause of the problem.  So I was hoping that maybe someone on the forum has had a similar problem and might be able to provide advice.  I'm running Mythtv on Feisty.  I've run mysqlcheck on the myth database and everything checked out.  I'm thinking perhaps it's a bug in .20 but am not sure.  Below is the output of my log during bills game and I would sure appreciate any advice. Per monit, I experienced another crash 20 minutes ago during a recording session.

007-11-04 13:48:09.755 Unable to find active recorder for this
recording, realtime flagging will not be enabled.
0: start_time: 0.036 duration: 47.862
1: start_time: 0.026 duration: 47.840
stream: start_time: 0.289 duration: 531.909 bitrate=5195 kb/s
2007-11-04 13:48:09.811 AFD: Opened codec 0x81522d0, id(MPEG2VIDEO)
type(Video)
2007-11-04 13:48:09.843 AFD: Opened codec 0x8152620, id(MP2) type(Audio)
2007-11-04 13:48:14.476 JobQueue: Commercial Flagging Starting for NFL
Football "Cincinnati Bengals at Buffalo Bills" recorded from channel
1008 at Sun Nov 4 13:48:00 2007

2007-11-04 13:56:04.288 JobQueue: Commercial Flagging Finished, 0
break(s) found.
0: start_time: 0.036 duration: 47.862
1: start_time: 0.026 duration: 47.840
stream: start_time: 0.289 duration: 531.909 bitrate=5195 kb/s
2007-11-04 13:56:04.333 AFD: Opened codec 0x8262c00, id(MPEG2VIDEO)
type(Video)
2007-11-04 13:56:04.349 AFD: Opened codec 0x81997c0, id(MP2) type(Audio)
2007-11-04 13:56:56.969 Event socket closed. No connection to the
backend.
2007-11-04 13:57:01.198 Using runtime prefix = /usr
2007-11-04 13:57:01.285 New DB connection, total: 1
2007-11-04 13:57:01.315 Connected to database 'mythconverg' at host:
localhost

2007-11-04 13:57:11.950 Unable to find active recorder for this
recording, realtime flagging will not be enabled.
0: start_time: 0.036 duration: 47.883
1: start_time: 0.026 duration: 47.855
stream: start_time: 0.289 duration: 532.143 bitrate=5191 kb/s
2007-11-04 13:57:12.028 AFD: Opened codec 0x8152260, id(MPEG2VIDEO)
type(Video)
2007-11-04 13:57:12.075 AFD: Opened codec 0x81525b0, id(MP2) type(Audio)
2007-11-04 13:57:16.693 JobQueue: Commercial Flagging Starting for NFL
Football "Cincinnati Bengals at Buffalo Bills" recorded from channel
1008 at Sun Nov 4 13:57:00 2007
2007-11-04 13:57:16.814 Using runtime prefix = /usr
2007-11-04 13:57:16.828 New DB connection, total: 1
2007-11-04 13:57:16.844 Connected to database 'mythconverg' at host:
localhost
2007-11-04 13:57:16.849 New DB connection, total: 2
2007-11-04 13:57:16.863 Connected to database 'mythconverg' at host:
localhost
2007-11-04 13:57:17.053 Connecting to backend server: 192.168.2.100:6543

007-11-04 14:25:43.718 AFD: Opened codec 0x81b7200, id(MPEG2VIDEO)
type(Video)
2007-11-04 14:25:43.720 AFD: Opened codec 0x81b7660, id(MP2) type(Audio)
2007-11-04 14:30:01.826 Event socket closed. No connection to the
backend.
2007-11-04 14:30:06.559 Using runtime prefix = /usr
2007-11-04 14:30:06.694 New DB connection, total: 1
2007-11-04 14:30:06.717 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:30:06.719 Current Schema Version: 1160
Starting up as the master server.
2007-11-04 14:30:06.731 New DB connection, total: 2
2007-11-04 14:30:06.732 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:30:06.734 EITHelper: localtime offset -5:00:00
2007-11-04 14:30:06.737 New DB connection, total: 3
2007-11-04 14:30:06.738 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:30:06.884 EITHelper: localtime offset -5:00:00
2007-11-04 14:30:07.029 New DB scheduler connection
2007-11-04 14:30:07.031 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:30:08.450 Main::Registering HttpStatus Extension
2007-11-04 14:30:08.456 mythbackend version: 0.20.20070821-1
[www.mythtv.org](www.mythtv.org)
2007-11-04 14:30:08.457 Enabled verbose msgs:  important general
2007-11-04 14:30:08.458 AutoExpire: Found 2 recorders w/max rate of 144
MiB/min
2007-11-04 14:30:08.459 AutoExpire: Required Free Space: 3.1 GB w/freq:
10 min
2007-11-04 14:30:09.094 Reschedule requested for id -1.
2007-11-04 14:30:09.992 Scheduled 151 items in 0.9 = 0.27 match + 0.63
place
2007-11-04 14:30:10.002 Recording starts soon, AUTO-Startup assumed
2007-11-04 14:30:10.092 TVRec(7): Changing from None to RecordingOnly
2007-11-04 14:30:10.099 TVRec(7): HW Tuner: 7->7
2007-11-04 14:30:10.307 Started recording: NFL Football "Cincinnati
Bengals at Buffalo Bills": channel 1008 on cardid 7, sourceid 1
2007-11-04 14:30:17.070 JobQueue: Commercial Flagging Starting for NFL
Football "Cincinnati Bengals at Buffalo Bills" recorded from channel
1008 at Sun Nov 4 14:30:00 2007
2007-11-04 14:30:17.171 Using runtime prefix = /usr
2007-11-04 14:30:17.195 New DB connection, total: 1
2007-11-04 14:30:17.211 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:30:17.220 New DB connection, total: 2
2007-11-04 14:30:17.234 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:30:17.276 Connecting to backend server: 192.168.2.100:6543
(try 1 of 5)
2007-11-04 14:30:17.295 Using protocol version 31
2007-11-04 14:30:17.315 MainServer::HandleAnnounce Monitor
2007-11-04 14:30:17.327 adding: mythtv as a client (events: 0)
2007-11-04 14:30:17.331 MainServer::HandleAnnounce Monitor
2007-11-04 14:30:17.345 adding: mythtv as a client (events: 1)
[mpeg2video @ 0xb72422e8]ac-tex damaged at 26 27
[mpeg2video @ 0xb72422e8]Warning MVs not available
2007-11-04 14:30:25.868 Connecting to backend server: 192.168.2.100:6543
(try 1 of 5)
2007-11-04 14:30:25.886 Using protocol version 31
2007-11-04 14:30:25.887 MainServer::HandleAnnounce Monitor
2007-11-04 14:30:25.892 adding: mythtv as a client (events: 0)
2007-11-04 14:30:25.893 MainServer::HandleAnnounce Monitor
2007-11-04 14:30:25.894 adding: mythtv as a client (events: 1)
0: start_time: 0.036 duration: 1.766
1: start_time: 0.026 duration: 1.737
stream: start_time: 0.289 duration: 19.731 bitrate=5222 kb/s
2007-11-04 14:30:31.416 AFD: Opened codec 0x8152780, id(MPEG2VIDEO)
type(Video)
2007-11-04 14:30:31.435 AFD: Opened codec 0x8152ad0, id(MP2) type(Audio)
2007-11-04 14:32:22.118 JobQueue: Commercial Flagging Starting for NFL
Football "Cincinnati Bengals at Buffalo Bills" recorded from channel
1008 at Sun Nov 4 13:57:00 2007
2007-11-04 14:32:22.217 Using runtime prefix = /usr
2007-11-04 14:32:22.233 New DB connection, total: 1
2007-11-04 14:32:22.245 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:32:22.260 New DB connection, total: 2
2007-11-04 14:32:22.274 Connected to database 'mythconverg' at host:
localhost
2007-11-04 14:32:22.284 Connecting to backend server: 192.168.2.100:
stream: start_time: 0.289 duration: 1974.517 bitrate=5192 kb/s
2007-11-04 14:51:24.699 AFD: Opened codec 0xb0b7a990, id(MPEG2VIDEO)
type(Video)
2007-11-04 14:51:24.710 AFD: Opened codec 0xb0bcfb10, id(MP2)
type(Audio)
2007-11-04 15:12:07.652 Event socket closed. No connection to the
backend.
2007-11-04 15:12:12.124 Using runtime prefix = /usr
2007-11-04 15:12:12.250 New DB connection, total: 1
2007-11-04 15:12:12.273 Connected to database 'mythconverg' at host:
localhost
2007-11-04 15:12:12.278 Current Schema Version: 1160
Starting up as the master server.
2007-11-04 15:12:12.285 New DB connection, total: 2
2007-11-04 15:12:12.304 Connected to database 'mythconverg' at host:
localhost

---

