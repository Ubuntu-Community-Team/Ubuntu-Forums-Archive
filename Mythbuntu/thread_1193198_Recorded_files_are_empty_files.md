---
title: "Recorded files are empty files"
date: 2009-06-21
forum: Mythbuntu
---

### Post by peterhocking on 2009-06-21
I'm running the 64 bit version of Mythbuntu 9.04 with a HD Homerun tuner. Live TV works fine, but any shows that I record are reported as empty files.

When I first set up the HD Homerun, all shows recorded on the first tuner were fine, but the any shows recorded using the 2nd tuner were empty. I attempted to fix by resetting up my input connections as it was suggested to me they were broken. This didn't fix it, it just meant that shows recorded using both tuners were empty.

I've re-installed Mythbuntu & set it up a  number of times. Each time live TV is fine, but any shows I record are blank.

Can anyone suggest what the problem may be?

TIA

Peter

---

### Post by ian dobson on 2009-06-21
Hi,

What do you see in your backend log? (/var/log/mythbackend.log)

Regards
Ian Dobson

---

### Post by peterhocking on 2009-06-22
> **ian dobson said:**
> Hi,

What do you see in your backend log? (/var/log/mythbackend.log)

Regards
Ian Dobson

Hi, 

Thanks for your response

Here's the log from 2 un-successful recording attempts;

Tried to record 5 minutes of TV at 8.15 last night, (unsuccessful)

2009-06-21 20:09:00.572 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:14:00.149 Reschedule requested for id 0.
2009-06-21 20:14:00.230 Scheduled 1 items in 0.1 = 0.05 match + 0.03
place
2009-06-21 20:14:30.032 TVRec(1): ASK_RECORDING 1 29 0 0
2009-06-21 20:15:02.314 TVRec(1): Changing from None to RecordingOnly
2009-06-21 20:15:02.317 TVRec(1): HW Tuner: 1->1
2009-06-21 20:15:02.319 HDHRChan(12108420/0): device found at address
192.168.11.78
2009-06-21 20:15:02.347 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-21 20:15:02.351 Started recording: testing (Manual Record) "Sun
Jun 21 20:15:00 2009": channel 1002 on cardid 1, sourceid 1
2009-06-21 20:20:00.424 TVRec(1): Changing from RecordingOnly to None
2009-06-21 20:20:00.431 Finished recording testing (Manual Record) "Sun
Jun 21 20:15:00 2009": channel 1002
2009-06-21 20:20:00.432 Reschedule requested for id 0.
2009-06-21 20:20:00.455 Scheduled 0 items in 0.0 = 0.01 match + 0.02
place
2009-06-21 20:20:01.403 Finished recording testing (Manual Record) "Sun
Jun 21 20:15:00 2009": channel 1002
2009-06-21 20:20:01.553 Using runtime prefix = /usr
2009-06-21 20:20:01.559 Empty LocalHostName.
2009-06-21 20:20:01.560 Using localhost value of tv-server
2009-06-21 20:20:01.572 New DB connection, total: 1
2009-06-21 20:20:01.580 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:01.582 Closing DB connection named 'DBManager0'
2009-06-21 20:20:01.583 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:01.587 New DB connection, total: 2
2009-06-21 20:20:01.596 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:01.605 Current Schema Version: 1214
2009-06-21 20:20:01.619 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1002_20090621201500.mpg' is not valid.
2009-06-21 20:20:01.621 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'
2009-06-21 20:20:01.635 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20090621201500.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-21 20:20:39.547 JobQueue: Commercial Flagging Starting for
testing (Manual Record) "Sun Jun 21 20:15:00 2009" recorded from channel
1002 at Sun Jun 21 20:15:00 2009
2009-06-21 20:20:39.729 Using runtime prefix = /usr
2009-06-21 20:20:39.733 Empty LocalHostName.
2009-06-21 20:20:39.734 Using localhost value of tv-server
2009-06-21 20:20:39.746 New DB connection, total: 1
2009-06-21 20:20:39.754 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:39.756 Closing DB connection named 'DBManager0'
2009-06-21 20:20:39.759 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:39.767 New DB connection, total: 2
2009-06-21 20:20:39.770 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:46.274
RingBuf(/var/lib/mythtv/recordings/1002_20090621201500.mpg): Invalid
file (fd -1) when opening
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'.
2009-06-21 20:20:46.295 Connecting to backend server:
192.168.11.111:6543 (try 1 of 5)
2009-06-21 20:20:46.297 Using protocol version 40
2009-06-21 20:20:46.299 MainServer::HandleAnnounce Monitor
2009-06-21 20:20:46.306 adding: tv-server as a client (events: 0)
2009-06-21 20:20:46.316 MainServer::HandleAnnounce Monitor
2009-06-21 20:20:46.322 adding: tv-server as a client (events: 1)
2009-06-21 20:20:46.350 NVP::OpenFile(): Error, file not
found: /var/lib/mythtv/recordings/1002_20090621201500.mpg
2009-06-21 20:20:46.522 Using runtime prefix = /usr
2009-06-21 20:20:46.529 Empty LocalHostName.
2009-06-21 20:20:46.530 Using localhost value of tv-server
2009-06-21 20:20:46.549 New DB connection, total: 1
2009-06-21 20:20:46.557 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:46.559 Closing DB connection named 'DBManager0'
2009-06-21 20:20:46.567 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:46.575 New DB connection, total: 2
2009-06-21 20:20:46.583 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:20:46.592 Current Schema Version: 1214
2009-06-21 20:20:46.606 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1002_20090621201500.mpg' is not valid.
2009-06-21 20:20:46.608 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'
2009-06-21 20:20:46.623 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20090621201500.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-21 20:21:49.564 AutoExpire: CalcParams(): Max required Free
Space: 1.0 GB w/freq: 15 min
2009-06-21 20:22:25.423 MainServer::HandleAnnounce Monitor
2009-06-21 20:22:25.427 adding: tv-server as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2009-06-21 20:22:45.251 MainServer::HandleAnnounce Monitor
2009-06-21 20:22:45.255 adding: tv-server as a client (events: 0)
2009-06-21 20:22:45.494 Using runtime prefix = /usr
2009-06-21 20:22:45.502 Empty LocalHostName.
2009-06-21 20:22:45.503 Using localhost value of tv-server
2009-06-21 20:22:45.516 New DB connection, total: 1
2009-06-21 20:22:45.523 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:45.525 Closing DB connection named 'DBManager0'
2009-06-21 20:22:45.527 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:45.531 New DB connection, total: 2
2009-06-21 20:22:45.535 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:45.544 Current Schema Version: 1214
2009-06-21 20:22:45.559 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1002_20090621201500.mpg' is not valid.
2009-06-21 20:22:45.561 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'
2009-06-21 20:22:45.575 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20090621201500.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-21 20:22:45.578 MainServer: Failed to make preview image.
2009-06-21 20:22:45.746 Using runtime prefix = /usr
2009-06-21 20:22:45.751 Empty LocalHostName.
2009-06-21 20:22:45.752 Using localhost value of tv-server
2009-06-21 20:22:45.769 New DB connection, total: 1
2009-06-21 20:22:45.777 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:45.780 Closing DB connection named 'DBManager0'
2009-06-21 20:22:45.787 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:45.796 New DB connection, total: 2
2009-06-21 20:22:45.803 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:45.812 Current Schema Version: 1214
2009-06-21 20:22:45.823 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1002_20090621201500.mpg' is not valid.
2009-06-21 20:22:45.827 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'
2009-06-21 20:22:45.843 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20090621201500.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-21 20:22:54.048 MainServer::HandleAnnounce Monitor
2009-06-21 20:22:54.051 adding: tv-server as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2009-06-21 20:22:59.724 MainServer::HandleAnnounce Monitor
2009-06-21 20:22:59.727 adding: tv-server as a client (events: 0)
2009-06-21 20:22:59.944 Using runtime prefix = /usr
2009-06-21 20:22:59.950 Empty LocalHostName.
2009-06-21 20:22:59.951 Using localhost value of tv-server
2009-06-21 20:22:59.966 New DB connection, total: 1
2009-06-21 20:22:59.974 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:59.976 Closing DB connection named 'DBManager0'
2009-06-21 20:22:59.979 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:22:59.988 New DB connection, total: 2
2009-06-21 20:22:59.995 Connected to database 'mythconverg' at host:
localhost
2009-06-21 20:23:00.004 Current Schema Version: 1214
2009-06-21 20:23:00.017 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1002_20090621201500.mpg' is not valid.
2009-06-21 20:23:00.019 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'
2009-06-21 20:23:00.035 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20090621201500.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-21 20:23:00.038 MainServer: Failed to make preview image.
2009-06-21 20:31:02.775 MainServer::HandleAnnounce Monitor
2009-06-21 20:31:02.780 adding: tv-server as a client (events: 0)
2009-06-21 20:31:08.114 MainServer::HandleAnnounce Monitor
2009-06-21 20:31:08.119 adding: tv-server as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2009-06-21 20:31:15.115 MainServer::HandleAnnounce Monitor

Recorded 1 hour of TV at 3.30 PM today, (unsuccessful)

2009-06-22 15:29:00.464 Reschedule requested for id 0.
2009-06-22 15:29:00.508 Scheduled 13 items in 0.0 = 0.00 match + 0.04
place
2009-06-22 15:29:29.593 TVRec(1): ASK_RECORDING 1 29 0 0
2009-06-22 15:30:02.618 TVRec(1): Changing from None to RecordingOnly
2009-06-22 15:30:02.624 TVRec(1): HW Tuner: 1->1
2009-06-22 15:30:02.648 HDHRChan(12108420/0): device found at address
192.168.11.78
2009-06-22 15:30:02.722 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-22 15:30:02.727 Started recording: Once a Queen: channel 1030 on
cardid 1, sourceid 1
2009-06-22 15:42:06.446 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-22 15:42:06.451 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-22 15:42:22.837 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-22 15:57:22.880 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-22 16:05:05.289 MainServer::HandleAnnounce Monitor
2009-06-22 16:05:05.290 adding: tv-server as a client (events: 0)
2009-06-22 16:05:11.012 MainServer::HandleAnnounce Monitor
2009-06-22 16:05:11.014 adding: tv-server as a client (events: 0)
2009-06-22 16:05:11.263 Using runtime prefix = /usr
2009-06-22 16:05:11.270 Empty LocalHostName.
2009-06-22 16:05:11.271 Using localhost value of tv-server
2009-06-22 16:05:11.286 New DB connection, total: 1
2009-06-22 16:05:11.294 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.296 Closing DB connection named 'DBManager0'
2009-06-22 16:05:11.299 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.305 New DB connection, total: 2
2009-06-22 16:05:11.307 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.313 Current Schema Version: 1214
2009-06-22 16:05:11.328 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1030_20090622153000.mpg' is not valid.
2009-06-22 16:05:11.330 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1030_20090622153000.mpg'
2009-06-22 16:05:11.343 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1030_20090622153000.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-22 16:05:11.346 MainServer: Failed to make preview image.
2009-06-22 16:05:11.519 Using runtime prefix = /usr
2009-06-22 16:05:11.523 Empty LocalHostName.
2009-06-22 16:05:11.524 Using localhost value of tv-server
2009-06-22 16:05:11.541 New DB connection, total: 1
2009-06-22 16:05:11.549 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.551 Closing DB connection named 'DBManager0'
2009-06-22 16:05:11.559 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.568 New DB connection, total: 2
2009-06-22 16:05:11.575 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.584 Current Schema Version: 1214
2009-06-22 16:05:11.596 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1030_20090622153000.mpg' is not valid.
2009-06-22 16:05:11.599 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1030_20090622153000.mpg'
2009-06-22 16:05:11.615 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1030_20090622153000.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-22 16:05:11.807 Using runtime prefix = /usr
2009-06-22 16:05:11.811 Empty LocalHostName.
2009-06-22 16:05:11.812 Using localhost value of tv-server
2009-06-22 16:05:11.829 New DB connection, total: 1
2009-06-22 16:05:11.837 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.839 Closing DB connection named 'DBManager0'
2009-06-22 16:05:11.848 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.856 New DB connection, total: 2
2009-06-22 16:05:11.863 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:05:11.872 Current Schema Version: 1214
2009-06-22 16:05:11.887 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1002_20090621201500.mpg' is not valid.
2009-06-22 16:05:11.890 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1002_20090621201500.mpg'
2009-06-22 16:05:11.903 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1002_20090621201500.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-22 16:05:11.906 MainServer: Failed to make preview image.
2009-06-22 16:12:12.453 UPnpMedia: BuildMediaMap VIDEO scan starting
in :/var/lib/mythtv/videos:
2009-06-22 16:12:12.458 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-06-22 16:12:14.325 MainServer::HandleAnnounce Monitor
2009-06-22 16:12:14.327 adding: tv-server as a client (events: 0)
2009-06-22 16:12:14.329 MainServer::HandleAnnounce Monitor
2009-06-22 16:12:14.329 adding: tv-server as a client (events: 1)
2009-06-22 16:12:14.331 Reschedule requested for id -1.
2009-06-22 16:12:14.383 Scheduled 13 items in 0.0 = 0.02 match + 0.03
place
2009-06-22 16:12:22.925 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-22 16:27:22.974 AutoExpire: CalcParams(): Max required Free
Space: 3.0 GB w/freq: 15 min
2009-06-22 16:30:00.990 TVRec(1): Changing from RecordingOnly to None
2009-06-22 16:30:00.998 Reschedule requested for id 0.
2009-06-22 16:30:00.999 Finished recording Once a Queen: channel 1030
2009-06-22 16:30:01.062 Scheduled 12 items in 0.0 = 0.00 match + 0.04
place
2009-06-22 16:30:02.063 Finished recording Once a Queen: channel 1030
2009-06-22 16:30:02.199 Using runtime prefix = /usr
2009-06-22 16:30:02.204 Empty LocalHostName.
2009-06-22 16:30:02.205 Using localhost value of tv-server
2009-06-22 16:30:02.217 New DB connection, total: 1
2009-06-22 16:30:02.225 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:30:02.227 Closing DB connection named 'DBManager0'
2009-06-22 16:30:02.231 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:30:02.235 New DB connection, total: 2
2009-06-22 16:30:02.239 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:30:02.245 Current Schema Version: 1214
2009-06-22 16:30:02.256 Preview Error: Previewer file
'/var/lib/mythtv/recordings/1030_20090622153000.mpg' is not valid.
2009-06-22 16:30:02.257 Preview Error: Run() file not local:
'/var/lib/mythtv/recordings/1030_20090622153000.mpg'
2009-06-22 16:30:02.268 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1030_20090622153000.mpg.png)
exists: 0 readable: 0 size: 0
2009-06-22 16:30:16.876 JobQueue: Commercial Flagging Starting for Once
a Queen recorded from channel 1030 at Mon Jun 22 15:30:00 2009
2009-06-22 16:30:17.051 Using runtime prefix = /usr
2009-06-22 16:30:17.057 Empty LocalHostName.
2009-06-22 16:30:17.058 Using localhost value of tv-server
2009-06-22 16:30:17.077 New DB connection, total: 1
2009-06-22 16:30:17.085 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:30:17.087 Closing DB connection named 'DBManager0'
2009-06-22 16:30:17.095 Connected to database 'mythconverg' at host:
localhost
2009-06-22 16:30:17.107 New DB connection, total: 2

Interestingly enough, there was one successful recording, (the first for 2+ weeks) between these 2 unsuccesful recordings

Thanks again

Peter

---

### Post by ian dobson on 2009-06-22
Hi,

Have you already seen this [https://help.ubuntu.com/community/HDHomeRun](https://help.ubuntu.com/community/HDHomeRun).

Sorry but the log file doesn't show anything interesting/wrong.

Regards
Ian Dobson

---

### Post by peterhocking on 2009-06-22
> **ian dobson said:**
> Hi,

Have you already seen this [https://help.ubuntu.com/community/HDHomeRun](https://help.ubuntu.com/community/HDHomeRun).

Sorry but the log file doesn't show anything interesting/wrong.

Regards
Ian Dobson

Hi

That was the guide I used.

It seems strange that live TV, (which records TV as you watch it), works, but not recording shows. Any further ideas where I should look?

Peter

---

