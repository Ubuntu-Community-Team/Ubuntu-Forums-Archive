---
title: "Mythtv keeps crashing"
date: 2010-10-21
forum: Mythbuntu
---

### Post by scottishnarn on 2010-10-21
After upgrading to the latest fixes branch on Wednesday (I'm using 0.23.1 fixes on Ubuntu 9.10) mythtv keeps crashing and restarting every 20 mins. 

My recordings are broken up into 20 minute chunks, so mythbackend seems to be crashing. (I've got a DVB tuner and a WinTV PVR 150 and the same behavior occurs on both cards).

Mythfrontend also crashes every 20 minutes. If I run a gnome without mythfrontend it runs fine without crashing (but the recordings still get broken up into 20 minutes chunks so mythbackend is still crashing). 

Any ideas?

Thanks
David

---

### Post by LowSky on 2010-10-21
we need see the mythtv backend logs to know what is going wrong

the file we need to see is this,
```
/var/log/mythtv/mythbackend.log
```
 open it and copy the last few days worth of data

---

### Post by scottishnarn on 2010-10-21
I tried to post a couple of days of log but it the forum kept timing out. So here's a little bit from the end
```

2010-10-21 20:05:32.379 Using localhost value of gandalf
2010-10-21 20:05:32.536 New DB connection, total: 1
2010-10-21 20:05:32.591 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:05:32.610 Closing DB connection named 'DBManager0'
2010-10-21 20:05:32.614 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:05:32.621 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:05:32.661 MythBackend: Starting up as the master server.
2010-10-21 20:05:32.682 New DB connection, total: 2
2010-10-21 20:05:32.712 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:05:32.771 New DB connection, total: 3
2010-10-21 20:05:32.777 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:05:32.889 Channel(/dev/videoivtv) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-10-21 20:05:32.909 New DB scheduler connection
2010-10-21 20:05:32.976 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:05:33.227 Enabling Upnpmedia rebuild thread.
2010-10-21 20:05:34.540 Main::Registering HttpStatus Extension
2010-10-21 20:05:34.657 Enabled verbose msgs:  important general
2010-10-21 20:05:34.666 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 20:05:36.269 Reschedule requested for id -1.
2010-10-21 20:05:36.859 Scheduled 31 items in 0.5 = 0.06 match + 0.46 place
2010-10-21 20:05:36.883 AUTO-Startup assumed
2010-10-21 20:05:36.926 TVRec(1): ASK_RECORDING 1 0 0 0
2010-10-21 20:05:37.063 TVRec(1): Changing from None to RecordingOnly
2010-10-21 20:05:37.068 TVRec(1): HW Tuner: 1->1
2010-10-21 20:05:37.195 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-10-21 20:05:37.205 Started recording: Nigella Kitchen "Rags to Riches": channel 1002 on cardid 1, sourceid 1
2010-10-21 20:05:37.878 TVRec(2): ASK_RECORDING 2 0 0 0
2010-10-21 20:05:38.615 TVRec(1): rec->GetFileName(): '/mnt/mythtv/recordings/1002_20101021200600.mpg'
2010-10-21 20:05:43.334 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-21 20:05:43.774 UPnpMedia: BuildMediaMap Done. Found 92 objects
2010-10-21 20:05:48.596 MainServer::ANN Monitor
2010-10-21 20:05:48.605 adding: gandalf as a client (events: 0)
2010-10-21 20:05:48.622 MainServer::ANN Monitor
2010-10-21 20:05:48.644 adding: gandalf as a client (events: 1)
2010-10-21 20:05:51.808 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:05:51.829 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:05:52.334 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:05:53.700 MainServer::ANN Playback
2010-10-21 20:05:53.703 adding: gandalf as a client (events: 0)
2010-10-21 20:05:53.705 MainServer::HandleAnnounce FileTransfer
2010-10-21 20:05:53.707 adding: gandalf as a remote file transfer
2010-10-21 20:05:55.965 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:05:57.919 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:05:57.951 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:06:03.368 ProgramInfo(): Updated pathname '':'' -> '102_20101020204000.mpg'
2010-10-21 20:06:53.203 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-10-21 20:10:03.286 MainServer::ANN Monitor
2010-10-21 20:10:03.287 adding: gandalf as a client (events: 0)
2010-10-21 20:17:02.575 MainServer::ANN Monitor
2010-10-21 20:17:02.576 adding: gandalf as a client (events: 0)
2010-10-21 20:17:03.230 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:17:03.237 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:19:04.235 ProgramInfo(): Updated pathname '':'' -> '102_20101020204000.mpg'
2010-10-21 20:20:03.764 MainServer::ANN Monitor
2010-10-21 20:20:03.775 adding: gandalf as a client (events: 0)
2010-10-21 20:20:53.324 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 256
2010-10-21 20:25:30.678 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:25:30.680 Using runtime prefix = /usr
2010-10-21 20:25:30.681 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:25:30.682 Empty LocalHostName.
2010-10-21 20:25:30.683 Using localhost value of gandalf
2010-10-21 20:25:30.693 New DB connection, total: 1
2010-10-21 20:25:30.697 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:25:30.698 Closing DB connection named 'DBManager0'
2010-10-21 20:25:30.700 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:25:30.706 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:25:30.709 MythBackend: Starting up as the master server.
2010-10-21 20:25:30.717 New DB connection, total: 2
2010-10-21 20:25:30.719 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:25:30.727 New DB connection, total: 3
2010-10-21 20:25:30.728 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:25:30.797 Channel(/dev/videoivtv) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-10-21 20:25:30.810 New DB scheduler connection
2010-10-21 20:25:30.811 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:25:30.848 Enabling Upnpmedia rebuild thread.
2010-10-21 20:25:32.055 Main::Registering HttpStatus Extension
2010-10-21 20:25:32.056 Enabled verbose msgs:  important general
2010-10-21 20:25:32.060 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 20:25:33.823 Reschedule requested for id -1.
2010-10-21 20:25:33.974 Scheduled 31 items in 0.1 = 0.02 match + 0.12 place
2010-10-21 20:25:33.980 AUTO-Startup assumed
2010-10-21 20:25:33.991 TVRec(1): ASK_RECORDING 1 0 0 0
2010-10-21 20:25:34.027 TVRec(1): Changing from None to RecordingOnly
2010-10-21 20:25:34.032 TVRec(1): HW Tuner: 1->1
2010-10-21 20:25:34.065 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:25:34.082 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-10-21 20:25:34.090 Started recording: Nigella Kitchen "Rags to Riches": channel 1002 on cardid 1, sourceid 1
2010-10-21 20:25:34.635 TVRec(1): rec->GetFileName(): '/mnt/mythtv/recordings/1002_20101021202600.mpg'
2010-10-21 20:25:34.784 TVRec(2): ASK_RECORDING 2 0 0 0
2010-10-21 20:25:40.861 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-21 20:25:40.935 UPnpMedia: BuildMediaMap Done. Found 92 objects
2010-10-21 20:26:50.832 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-10-21 20:29:22.321 MainServer::ANN Monitor
2010-10-21 20:29:22.323 adding: gandalf as a client (events: 2)
2010-10-21 20:29:22.610 MainServer::ANN Monitor
2010-10-21 20:29:22.618 adding: gandalf as a client (events: 2)
2010-10-21 20:29:22.670 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:29:22.675 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:29:23.649 MainServer::ANN Monitor
2010-10-21 20:29:23.650 adding: gandalf as a client (events: 2)
2010-10-21 20:29:25.906 MainServer::ANN Monitor
2010-10-21 20:29:25.922 adding: gandalf as a client (events: 2)
2010-10-21 20:29:26.138 MainServer::ANN Monitor
2010-10-21 20:29:26.156 adding: gandalf as a client (events: 2)
2010-10-21 20:29:26.252 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:29:26.275 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:29:27.759 MainServer::ANN Monitor
2010-10-21 20:29:27.772 adding: gandalf as a client (events: 2)
2010-10-21 20:29:32.465 ProgramInfo(): Updated pathname '':'' -> '1002_20101021200600.mpg'
2010-10-21 20:29:32.465 New DB connection, total: 4
2010-10-21 20:29:32.467 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:29:32.492 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:32.559 ProgramInfo(): Updated pathname '':'' -> '1002_20101021200000.mpg'
2010-10-21 20:29:32.826 ProgramInfo(): Updated pathname '':'' -> '1002_20101020220000.mpg'
2010-10-21 20:29:32.842 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:29:32.846 ProgramInfo(): Updated pathname '':'' -> '106_20101020220000.mpg'
2010-10-21 20:29:33.024 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:29:33.045 Using runtime prefix = /usr
2010-10-21 20:29:33.054 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:29:33.062 Empty LocalHostName.
2010-10-21 20:29:33.074 Using localhost value of gandalf
2010-10-21 20:29:33.139 New DB connection, total: 1
2010-10-21 20:29:33.170 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:33.181 Closing DB connection named 'DBManager0'
2010-10-21 20:29:33.213 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:33.228 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:29:33.292 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:29:33.392 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:29:33.398 Using runtime prefix = /usr
2010-10-21 20:29:33.413 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:29:33.418 Empty LocalHostName.
2010-10-21 20:29:33.434 Using localhost value of gandalf
2010-10-21 20:29:33.486 New DB connection, total: 1
2010-10-21 20:29:33.503 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:33.507 Closing DB connection named 'DBManager0'
2010-10-21 20:29:33.516 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:33.559 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:29:33.574 ProgramInfo(): Updated pathname '':'' -> '106_20101020220000.mpg'
2010-10-21 20:29:33.738 Preview Error: Previewer file '/mnt/mythtv/recordings/106_20101020220000.mpg' is not valid.
2010-10-21 20:29:33.749 Preview Error: Run() file not local: '/mnt/mythtv/recordings/106_20101020220000.mpg'
2010-10-21 20:29:33.765 ~MythContext waiting for threads to exit.
2010-10-21 20:29:33.847 ProgramInfo(): Updated pathname '':'' -> '1001_20101020210000.mpg'
2010-10-21 20:29:33.856 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:29:33.928 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0@64s --chanid 106 --starttime 20101020220000 --outfile "/mnt/mythtv/recordings/106_20101020220000.mpg.png" '
2010-10-21 20:29:34.362 ProgramInfo(): Updated pathname '':'' -> '106_20101020210000.mpg'
2010-10-21 20:29:34.786 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:29:34.798 Using runtime prefix = /usr
2010-10-21 20:29:34.802 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:29:34.839 Empty LocalHostName.
2010-10-21 20:29:34.845 Using localhost value of gandalf
2010-10-21 20:29:34.886 New DB connection, total: 1
2010-10-21 20:29:34.920 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:34.923 Closing DB connection named 'DBManager0'
2010-10-21 20:29:34.929 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:29:34.960 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:29:34.985 ProgramInfo(): Updated pathname '':'' -> '106_20101020210000.mpg'
2010-10-21 20:29:35.106 Preview Error: Previewer file '/mnt/mythtv/recordings/106_20101020210000.mpg' is not valid.
2010-10-21 20:29:35.114 Preview Error: Run() file not local: '/mnt/mythtv/recordings/106_20101020210000.mpg'
2010-10-21 20:29:35.176 ~MythContext waiting for threads to exit.
2010-10-21 20:29:35.214 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0@64s --chanid 106 --starttime 20101020210000 --outfile "/mnt/mythtv/recordings/106_20101020210000.mpg.png" '
2010-10-21 20:29:36.845 AFD: Opened codec 0xe024a0, id(MPEG2VIDEO) type(Video)
2010-10-21 20:29:36.915 AFD: codec MP2 has 2 channels
2010-10-21 20:29:36.931 AFD: Opened codec 0xe01250, id(MP2) type(Audio)
2010-10-21 20:29:36.939 AFD: codec MP2 has 1 channels
2010-10-21 20:29:36.953 AFD: Opened codec 0xe090b0, id(MP2) type(Audio)
2010-10-21 20:29:36.967 AFD: Opened codec 0xe09710, id(DVB_SUBTITLE) type(Subtitle)
2010-10-21 20:29:43.882 Preview: Grabbed preview '/mnt/mythtv/recordings/1002_20101021202600.mpg' 720x576@64s
2010-10-21 20:29:46.715 ~MythContext waiting for threads to exit.
2010-10-21 20:30:00.101 TVRec(1): Changing from RecordingOnly to None
2010-10-21 20:30:00.104 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:30:00.106 Finished recording Nigella Kitchen "Rags to Riches": channel 1002
2010-10-21 20:30:00.140 Reschedule requested for id 0.
2010-10-21 20:30:00.161 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:30:00.173 ProgramInfo(1002_20101021202600.mpg), Error: Unknown type, recording width was 720
2010-10-21 20:30:00.303 Scheduled 30 items in 0.2 = 0.04 match + 0.11 place
2010-10-21 20:30:00.579 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:30:00.588 Finished recording Nigella Kitchen "Rags to Riches": channel 1002
2010-10-21 20:30:00.618 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:30:00.669 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:30:00.680 Using runtime prefix = /usr
2010-10-21 20:30:00.680 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:30:00.682 Empty LocalHostName.
2010-10-21 20:30:00.683 Using localhost value of gandalf
2010-10-21 20:30:00.692 New DB connection, total: 1
2010-10-21 20:30:00.697 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:30:00.698 Closing DB connection named 'DBManager0'
2010-10-21 20:30:00.699 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:30:00.705 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:30:00.708 ProgramInfo(): Updated pathname '':'' -> '1002_20101021202600.mpg'
2010-10-21 20:30:02.750 MainServer::ANN Monitor
2010-10-21 20:30:02.751 adding: gandalf as a client (events: 0)
2010-10-21 20:30:03.408 AFD: Opened codec 0x1474720, id(MPEG2VIDEO) type(Video)
2010-10-21 20:30:03.409 AFD: codec MP2 has 2 channels
2010-10-21 20:30:03.409 AFD: Opened codec 0x14735f0, id(MP2) type(Audio)
2010-10-21 20:30:03.410 AFD: codec MP2 has 1 channels
2010-10-21 20:30:03.411 AFD: Opened codec 0x147b170, id(MP2) type(Audio)
2010-10-21 20:30:03.412 AFD: Opened codec 0x147b990, id(DVB_SUBTITLE) type(Subtitle)
2010-10-21 20:30:03.589 Preview: Grabbed preview '/mnt/mythtv/recordings/1002_20101021202600.mpg' 720x576@64s
2010-10-21 20:30:03.684 ~MythContext waiting for threads to exit.
2010-10-21 20:30:35.042 MainServer::ANN Monitor
2010-10-21 20:30:35.043 adding: gandalf as a client (events: 2)
2010-10-21 20:30:35.138 MainServer::ANN Monitor
2010-10-21 20:30:35.139 adding: gandalf as a client (events: 2)
2010-10-21 20:30:35.188 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:30:35.192 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:30:35.243 MainServer::ANN Monitor
2010-10-21 20:30:35.244 adding: gandalf as a client (events: 2)
2010-10-21 20:30:35.303 ProgramInfo(): Updated pathname '':'' -> '102_20101020202000.mpg'
2010-10-21 20:30:38.133 MainServer::ANN Monitor
2010-10-21 20:30:38.133 adding: gandalf as a client (events: 2)
2010-10-21 20:30:38.227 MainServer::ANN Monitor
2010-10-21 20:30:38.228 adding: gandalf as a client (events: 2)
2010-10-21 20:30:38.272 ProgramInfo(): Updated pathname '':'' -> '102_20101020202000.mpg'
2010-10-21 20:30:38.277 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:30:38.307 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:30:38.357 MainServer::ANN Monitor
2010-10-21 20:30:38.361 adding: gandalf as a client (events: 2)
2010-10-21 20:30:38.417 ProgramInfo(): Updated pathname '':'' -> '102_20101020200001.mpg'
2010-10-21 20:30:41.863 MainServer::ANN Monitor
2010-10-21 20:30:41.864 adding: gandalf as a client (events: 2)
2010-10-21 20:30:41.958 MainServer::ANN Monitor
2010-10-21 20:30:41.959 adding: gandalf as a client (events: 2)
2010-10-21 20:30:42.006 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:30:42.022 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:30:42.081 MainServer::ANN Monitor
2010-10-21 20:30:42.091 adding: gandalf as a client (events: 2)
2010-10-21 20:30:42.148 ProgramInfo(): Updated pathname '':'' -> '102_20101020204000.mpg'
2010-10-21 20:30:42.400 Reschedule requested for id 0.
2010-10-21 20:30:42.403 ProgramInfo(): Updated pathname '':'' -> '102_20101020200001.mpg'
2010-10-21 20:30:42.521 Scheduled 30 items in 0.1 = 0.00 match + 0.11 place
2010-10-21 20:30:46.510 ProgramInfo(): Updated pathname '':'' -> '102_20101020204000.mpg'
2010-10-21 20:30:46.510 Reschedule requested for id 0.
2010-10-21 20:30:46.629 Scheduled 30 items in 0.1 = 0.02 match + 0.09 place
2010-10-21 20:30:48.107 MainServer::ANN Monitor
2010-10-21 20:30:48.108 adding: gandalf as a client (events: 2)
2010-10-21 20:30:48.201 MainServer::ANN Monitor
2010-10-21 20:30:48.203 adding: gandalf as a client (events: 2)
2010-10-21 20:30:48.249 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:30:48.253 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:30:48.936 MainServer::ANN Monitor
2010-10-21 20:30:48.937 adding: gandalf as a client (events: 2)
2010-10-21 20:30:50.678 Reschedule requested for id 0.
2010-10-21 20:30:51.042 Scheduled 30 items in 0.3 = 0.01 match + 0.31 place
2010-10-21 20:30:52.667 ProgramInfo(): Updated pathname '':'' -> '1002_20101020220000.mpg'
2010-10-21 20:30:52.706 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 20:30:52.860 ProgramInfo(): Updated pathname '':'' -> '1002_20101020222000.mpg'
2010-10-21 20:30:52.939 ProgramInfo(): Updated pathname '':'' -> '106_20101020224000.mpg'
2010-10-21 20:30:53.017 ProgramInfo(): Updated pathname '':'' -> '106_20101020220000.mpg'
2010-10-21 20:30:53.353 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:30:53.408 Using runtime prefix = /usr
2010-10-21 20:30:53.427 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:30:53.451 Empty LocalHostName.
2010-10-21 20:30:53.457 Using localhost value of gandalf
2010-10-21 20:30:53.481 New DB connection, total: 1
2010-10-21 20:30:53.501 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:30:53.507 Closing DB connection named 'DBManager0'
2010-10-21 20:30:53.527 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:30:53.534 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:30:53.548 ProgramInfo(): Updated pathname '':'' -> '106_20101020220000.mpg'
2010-10-21 20:30:53.592 Preview Error: Previewer file '/mnt/mythtv/recordings/106_20101020220000.mpg' is not valid.
2010-10-21 20:30:53.614 Preview Error: Run() file not local: '/mnt/mythtv/recordings/106_20101020220000.mpg'
2010-10-21 20:30:53.616 ~MythContext waiting for threads to exit.
2010-10-21 20:30:53.691 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0@64s --chanid 106 --starttime 20101020220000 --outfile "/mnt/mythtv/recordings/106_20101020220000.mpg.png" '
2010-10-21 20:30:53.708 ProgramInfo(): Updated pathname '':'' -> '1002_20101020220001.mpg'
2010-10-21 20:30:53.809 ProgramInfo(): Updated pathname '':'' -> '106_20101020220001.mpg'
2010-10-21 20:30:53.879 ProgramInfo(): Updated pathname '':'' -> '106_20101020222000.mpg'
2010-10-21 20:30:53.959 ProgramInfo(): Updated pathname '':'' -> '1001_20101020214000.mpg'
2010-10-21 20:30:54.031 ProgramInfo(): Updated pathname '':'' -> '1001_20101020212000.mpg'
2010-10-21 20:30:54.138 ProgramInfo(): Updated pathname '':'' -> '1001_20101020210000.mpg'
2010-10-21 20:30:54.154 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 20:30:54.188 ProgramInfo(): Updated pathname '':'' -> '1001_20101020210001.mpg'
2010-10-21 20:30:54.297 ProgramInfo(): Updated pathname '':'' -> '106_20101020212000.mpg'
2010-10-21 20:30:54.389 ProgramInfo(): Updated pathname '':'' -> '106_20101020210001.mpg'
2010-10-21 20:30:54.489 ProgramInfo(): Updated pathname '':'' -> '106_20101020214000.mpg'
2010-10-21 20:30:54.588 ProgramInfo(): Updated pathname '':'' -> '106_20101020210000.mpg'
2010-10-21 20:30:54.913 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:30:54.930 Using runtime prefix = /usr
2010-10-21 20:30:54.931 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:30:54.933 Empty LocalHostName.
2010-10-21 20:30:54.934 Using localhost value of gandalf
2010-10-21 20:30:54.943 New DB connection, total: 1
2010-10-21 20:30:54.949 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:30:54.950 Closing DB connection named 'DBManager0'
2010-10-21 20:30:54.951 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:30:54.957 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:30:54.960 ProgramInfo(): Updated pathname '':'' -> '106_20101020210000.mpg'
2010-10-21 20:30:54.966 Preview Error: Previewer file '/mnt/mythtv/recordings/106_20101020210000.mpg' is not valid.
2010-10-21 20:30:54.968 Preview Error: Run() file not local: '/mnt/mythtv/recordings/106_20101020210000.mpg'
2010-10-21 20:30:54.970 ~MythContext waiting for threads to exit.
2010-10-21 20:30:55.023 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0@64s --chanid 106 --starttime 20101020210000 --outfile "/mnt/mythtv/recordings/106_20101020210000.mpg.png" '
2010-10-21 20:30:55.031 ProgramInfo(): Updated pathname '':'' -> '1029_20101019220000.mpg'
2010-10-21 20:30:55.109 ProgramInfo(): Updated pathname '':'' -> '1005_20101019210000.mpg'
2010-10-21 20:30:55.179 ProgramInfo(): Updated pathname '':'' -> '106_20101019210000.mpg'
2010-10-21 20:30:55.249 ProgramInfo(): Updated pathname '':'' -> '520_20101018210000.mpg'
2010-10-21 20:30:55.328 ProgramInfo(): Updated pathname '':'' -> '1001_20101018210000.mpg'
2010-10-21 20:30:55.386 ProgramInfo(): Updated pathname '':'' -> '106_20101017220000.mpg'
2010-10-21 20:30:55.479 ProgramInfo(): Updated pathname '':'' -> '1015_20101017184000.mpg'
2010-10-21 20:30:55.611 ProgramInfo(): Updated pathname '':'' -> '1015_20101016210000.mpg'
2010-10-21 20:30:55.758 ProgramInfo(): Updated pathname '':'' -> '1001_20101016194300.mpg'
2010-10-21 20:30:55.859 ProgramInfo(): Updated pathname '':'' -> '1002_20101014200000.mpg'
2010-10-21 20:30:55.952 ProgramInfo(): Updated pathname '':'' -> '1001_20101013193000.mpg'
2010-10-21 20:30:56.016 ProgramInfo(): Updated pathname '':'' -> '1029_20101012220000.mpg'
2010-10-21 20:30:56.179 ProgramInfo(): Updated pathname '':'' -> '1005_20101012210000.mpg'
2010-10-21 20:30:56.279 ProgramInfo(): Updated pathname '':'' -> '106_20101012210000.mpg'
2010-10-21 20:30:56.345 ProgramInfo(): Updated pathname '':'' -> '1002_20101011210000.mpg'
2010-10-21 20:30:56.449 ProgramInfo(): Updated pathname '':'' -> '520_20101011210000.mpg'
2010-10-21 20:30:56.497 ProgramInfo(): Updated pathname '':'' -> '1001_20101011210000.mpg'
2010-10-21 20:30:56.682 ProgramInfo(): Updated pathname '':'' -> '106_20101010220000.mpg'
2010-10-21 20:30:56.800 ProgramInfo(): Updated pathname '':'' -> '1001_20101009193800.mpg'
2010-10-21 20:30:56.889 ProgramInfo(): Updated pathname '':'' -> '106_20101008230000.mpg'
2010-10-21 20:30:56.987 ProgramInfo(): Updated pathname '':'' -> '1001_20101006193000.mpg'
2010-10-21 20:30:57.078 ProgramInfo(): Updated pathname '':'' -> '1029_20101005220000.mpg'
2010-10-21 20:30:57.179 ProgramInfo(): Updated pathname '':'' -> '1005_20101005210000.mpg'
2010-10-21 20:30:57.292 ProgramInfo(): Updated pathname '':'' -> '520_20101004210000.mpg'
2010-10-21 20:30:57.409 ProgramInfo(): Updated pathname '':'' -> '1001_20101004210000.mpg'
2010-10-21 20:30:57.488 ProgramInfo(): Updated pathname '':'' -> '106_20101003220000.mpg'
2010-10-21 20:30:57.579 ProgramInfo(): Updated pathname '':'' -> '1001_20101002190300.mpg'
2010-10-21 20:30:57.690 ProgramInfo(): Updated pathname '':'' -> '1002_20100930200000.mpg'
2010-10-21 20:30:57.791 ProgramInfo(): Updated pathname '':'' -> '1001_20100929193000.mpg'
2010-10-21 20:30:57.933 ProgramInfo(): Updated pathname '':'' -> '1029_20100928220000.mpg'
2010-10-21 20:30:58.010 ProgramInfo(): Updated pathname '':'' -> '105_20100928210000.mpg'
2010-10-21 20:30:58.138 ProgramInfo(): Updated pathname '':'' -> '1004_20100928200000.mpg'
2010-10-21 20:30:58.229 ProgramInfo(): Updated pathname '':'' -> '520_20100927210000.mpg'
2010-10-21 20:30:58.276 ProgramInfo(): Updated pathname '':'' -> '1001_20100927210000.mpg'
2010-10-21 20:30:58.411 ProgramInfo(): Updated pathname '':'' -> '1001_20100925185800.mpg'
2010-10-21 20:30:58.561 ProgramInfo(): Updated pathname '':'' -> '1001_20100922193000.mpg'
2010-10-21 20:30:58.678 ProgramInfo(): Updated pathname '':'' -> '1029_20100921220000.mpg'
2010-10-21 20:30:58.818 ProgramInfo(): Updated pathname '':'' -> '105_20100921210000.mpg'
2010-10-21 20:30:58.889 ProgramInfo(): Updated pathname '':'' -> '1004_20100921200000.mpg'
2010-10-21 20:30:58.949 ProgramInfo(): Updated pathname '':'' -> '520_20100920210000.mpg'
2010-10-21 20:30:59.020 ProgramInfo(): Updated pathname '':'' -> '1001_20100920210000.mpg'
2010-10-21 20:30:59.148 ProgramInfo(): Updated pathname '':'' -> '1001_20100918192800.mpg'
2010-10-21 20:30:59.355 ProgramInfo(): Updated pathname '':'' -> '106_20100916210000.mpg'
2010-10-21 20:30:59.440 ProgramInfo(): Updated pathname '':'' -> '1001_20100915193000.mpg'
2010-10-21 20:30:59.546 ProgramInfo(): Updated pathname '':'' -> '1029_20100914220000.mpg'
2010-10-21 20:30:59.628 ProgramInfo(): Updated pathname '':'' -> '105_20100914210000.mpg'
2010-10-21 20:30:59.688 ProgramInfo(): Updated pathname '':'' -> '520_20100913210000.mpg'
2010-10-21 20:30:59.779 ProgramInfo(): Updated pathname '':'' -> '1001_20100911192300.mpg'
2010-10-21 20:30:59.931 ProgramInfo(): Updated pathname '':'' -> '106_20100909210000.mpg'
2010-10-21 20:31:00.034 ProgramInfo(): Updated pathname '':'' -> '1001_20100908193000.mpg'
2010-10-21 20:31:00.139 ProgramInfo(): Updated pathname '':'' -> '1029_20100907220000.mpg'
2010-10-21 20:31:00.261 ProgramInfo(): Updated pathname '':'' -> '105_20100907210000.mpg'
2010-10-21 20:31:00.320 ProgramInfo(): Updated pathname '':'' -> '1004_20100907200000.mpg'
2010-10-21 20:31:00.450 ProgramInfo(): Updated pathname '':'' -> '520_20100906210000.mpg'
2010-10-21 20:31:00.584 ProgramInfo(): Updated pathname '':'' -> '106_20100902210000.mpg'
2010-10-21 20:31:00.700 ProgramInfo(): Updated pathname '':'' -> '1029_20100831220000.mpg'
2010-10-21 20:31:00.789 ProgramInfo(): Updated pathname '':'' -> '1001_20100831210000.mpg'
2010-10-21 20:31:00.868 ProgramInfo(): Updated pathname '':'' -> '1004_20100831200000.mpg'
2010-10-21 20:31:00.955 ProgramInfo(): Updated pathname '':'' -> '106_20100826210000.mpg'
2010-10-21 20:31:01.101 ProgramInfo(): Updated pathname '':'' -> '1029_20100824220000.mpg'
2010-10-21 20:31:01.231 ProgramInfo(): Updated pathname '':'' -> '1001_20100824210000.mpg'
2010-10-21 20:31:01.355 ProgramInfo(): Updated pathname '':'' -> '611_20100822084800.mpg'
2010-10-21 20:31:01.447 ProgramInfo(): Updated pathname '':'' -> '611_20100821084800.mpg'
2010-10-21 20:31:01.532 ProgramInfo(): Updated pathname '':'' -> '106_20100819210000.mpg'
2010-10-21 20:31:01.609 ProgramInfo(): Updated pathname '':'' -> '1029_20100817220000.mpg'
2010-10-21 20:31:01.699 ProgramInfo(): Updated pathname '':'' -> '105_20100817210000.mpg'
2010-10-21 20:31:01.819 ProgramInfo(): Updated pathname '':'' -> '1001_20100817210000.mpg'
2010-10-21 20:31:01.946 ProgramInfo(): Updated pathname '':'' -> '1004_20100817200000.mpg'
2010-10-21 20:31:02.029 ProgramInfo(): Updated pathname '':'' -> '611_20100815084800.mpg'
2010-10-21 20:31:02.158 ProgramInfo(): Updated pathname '':'' -> '611_20100814084800.mpg'
2010-10-21 20:31:02.241 ProgramInfo(): Updated pathname '':'' -> '1029_20100810220000.mpg'
2010-10-21 20:31:02.349 ProgramInfo(): Updated pathname '':'' -> '105_20100810210000.mpg'
2010-10-21 20:31:02.461 ProgramInfo(): Updated pathname '':'' -> '1001_20100810210000.mpg'
2010-10-21 20:31:02.549 ProgramInfo(): Updated pathname '':'' -> '611_20100808084800.mpg'
2010-10-21 20:31:02.681 ProgramInfo(): Updated pathname '':'' -> '611_20100807084800.mpg'
2010-10-21 20:31:02.786 ProgramInfo(): Updated pathname '':'' -> '106_20100805210000.mpg'
2010-10-21 20:31:02.890 ProgramInfo(): Updated pathname '':'' -> '1029_20100803220000.mpg'
2010-10-21 20:31:02.999 ProgramInfo(): Updated pathname '':'' -> '105_20100803210000.mpg'
2010-10-21 20:31:03.080 ProgramInfo(): Updated pathname '':'' -> '1001_20100803210000.mpg'
2010-10-21 20:31:03.197 ProgramInfo(): Updated pathname '':'' -> '611_20100801084800.mpg'
2010-10-21 20:31:03.311 ProgramInfo(): Updated pathname '':'' -> '106_20100729210000.mpg'
2010-10-21 20:31:03.411 ProgramInfo(): Updated pathname '':'' -> '105_20100727210000.mpg'
2010-10-21 20:31:03.577 ProgramInfo(): Updated pathname '':'' -> '1028_20100727210000.mpg'
2010-10-21 20:31:03.669 ProgramInfo(): Updated pathname '':'' -> '611_20100725084800.mpg'
2010-10-21 20:31:03.769 ProgramInfo(): Updated pathname '':'' -> '611_20100724084800.mpg'
2010-10-21 20:31:03.839 ProgramInfo(): Updated pathname '':'' -> '106_20100722210000.mpg'
2010-10-21 20:31:03.908 ProgramInfo(): Updated pathname '':'' -> '1024_20100721200000.mpg'
2010-10-21 20:31:04.014 ProgramInfo(): Updated pathname '':'' -> '1028_20100720210000.mpg'
2010-10-21 20:31:04.177 ProgramInfo(): Updated pathname '':'' -> '107_20100719210000.mpg'
2010-10-21 20:31:04.298 ProgramInfo(): Updated pathname '':'' -> '1024_20100714200000.mpg'
2010-10-21 20:31:04.407 ProgramInfo(): Updated pathname '':'' -> '1028_20100713210000.mpg'
2010-10-21 20:31:04.482 ProgramInfo(): Updated pathname '':'' -> '106_20100708220000.mpg'
2010-10-21 20:31:04.557 ProgramInfo(): Updated pathname '':'' -> '1028_20100706210000.mpg'
2010-10-21 20:31:04.661 ProgramInfo(): Updated pathname '':'' -> '106_20100701220000.mpg'
2010-10-21 20:31:04.790 ProgramInfo(): Updated pathname '':'' -> '1028_20100629210000.mpg'
2010-10-21 20:31:04.929 ProgramInfo(): Updated pathname '':'' -> '1001_20100626180300.mpg'
2010-10-21 20:31:05.027 ProgramInfo(): Updated pathname '':'' -> '106_20100624220000.mpg'
2010-10-21 20:31:05.107 ProgramInfo(): Updated pathname '':'' -> '1028_20100622210000.mpg'
2010-10-21 20:31:05.199 ProgramInfo(): Updated pathname '':'' -> '1001_20100619183800.mpg'
2010-10-21 20:31:05.279 ProgramInfo(): Updated pathname '':'' -> '520_20100618190000.mpg'
2010-10-21 20:31:05.439 ProgramInfo(): Updated pathname '':'' -> '106_20100617220000.mpg'
2010-10-21 20:31:05.539 ProgramInfo(): Updated pathname '':'' -> '1028_20100615210000.mpg'
2010-10-21 20:31:05.651 ProgramInfo(): Updated pathname '':'' -> '106_20100615200000.mpg'
2010-10-21 20:31:05.741 ProgramInfo(): Updated pathname '':'' -> '1001_20100612184300.mpg'
2010-10-21 20:31:05.819 ProgramInfo(): Updated pathname '':'' -> '106_20100610220000.mpg'
2010-10-21 20:31:05.939 ProgramInfo(): Updated pathname '':'' -> '106_20100609210000.mpg'
2010-10-21 20:31:06.080 ProgramInfo(): Updated pathname '':'' -> '1028_20100608210000.mpg'
2010-10-21 20:31:06.167 ProgramInfo(): Updated pathname '':'' -> '1004_20100603205800.mpg'
2010-10-21 20:31:06.259 ProgramInfo(): Updated pathname '':'' -> '1004_20100602205800.mpg'
2010-10-21 20:31:06.354 ProgramInfo(): Updated pathname '':'' -> '104_20100601210000.mpg'
2010-10-21 20:31:06.481 ProgramInfo(): Updated pathname '':'' -> '1002_20100601205700.mpg'
2010-10-21 20:31:06.588 ProgramInfo(): Updated pathname '':'' -> '1004_20100531205800.mpg'
2010-10-21 20:31:06.750 ProgramInfo(): Updated pathname '':'' -> '1004_20100530205800.mpg'
2010-10-21 20:31:06.827 ProgramInfo(): Updated pathname '':'' -> '1002_20100525205700.mpg'
2010-10-21 20:31:06.951 ProgramInfo(): Updated pathname '':'' -> '1002_20100518205700.mpg'
2010-10-21 20:31:07.039 ProgramInfo(): Updated pathname '':'' -> '1002_20100511205700.mpg'
2010-10-21 20:31:07.117 ProgramInfo(): Updated pathname '':'' -> '1002_20100504205800.mpg'
2010-10-21 20:31:07.180 ProgramInfo(): Updated pathname '':'' -> '1002_20100427205800.mpg'
2010-10-21 20:31:07.301 ProgramInfo(): Updated pathname '':'' -> '1002_20100404210000.mpg'
2010-10-21 20:31:07.477 ProgramInfo(): Updated pathname '':'' -> '1002_20100328210000.mpg'
2010-10-21 20:31:07.579 ProgramInfo(): Updated pathname '':'' -> '1002_20100314210000.mpg'
2010-10-21 20:31:07.669 ProgramInfo(): Updated pathname '':'' -> '1002_20100321210000.mpg'
2010-10-21 20:31:07.739 ProgramInfo(): Updated pathname '':'' -> '205_20100223220000.mpg'
2010-10-21 20:31:07.859 ProgramInfo(): Updated pathname '':'' -> '1002_20100307210000.mpg'
2010-10-21 20:31:07.969 ProgramInfo(): Updated pathname '':'' -> '205_20100216220000.mpg'
2010-10-21 20:31:08.069 ProgramInfo(): Updated pathname '':'' -> '205_20100209220000.mpg'
2010-10-21 20:31:08.188 ProgramInfo(): Updated pathname '':'' -> '129_20100204220000.mpg'
2010-10-21 20:31:08.289 ProgramInfo(): Updated pathname '':'' -> '130_20100126220000.mpg'
2010-10-21 20:31:08.389 ProgramInfo(): Updated pathname '':'' -> '130_20100119220000.mpg'
2010-10-21 20:31:08.497 ProgramInfo(): Updated pathname '':'' -> '130_20100112220000.mpg'
2010-10-21 20:31:08.608 ProgramInfo(): Updated pathname '':'' -> '129_20091103220000.mpg'
2010-10-21 20:31:08.698 ProgramInfo(): Updated pathname '':'' -> '129_20091027220000.mpg'
2010-10-21 20:31:08.809 ProgramInfo(): Updated pathname '':'' -> '129_20091020230000.mpg'
2010-10-21 20:31:08.905 ProgramInfo(): Updated pathname '':'' -> '129_20091020220000.mpg'
2010-10-21 20:31:09.023 ProgramInfo(): Updated pathname '':'' -> '520_20090914210000.mpg'
2010-10-21 20:31:09.121 ProgramInfo(): Updated pathname '':'' -> '129_20090829210000.mpg'
2010-10-21 20:31:09.238 ProgramInfo(): Updated pathname '':'' -> '129_20090829200000.mpg'
2010-10-21 20:31:09.347 ProgramInfo(): Updated pathname '':'' -> '129_20090822230000.mpg'
2010-10-21 20:31:09.450 ProgramInfo(): Updated pathname '':'' -> '129_20090822220000.mpg'
2010-10-21 20:31:09.550 ProgramInfo(): Updated pathname '':'' -> '129_20090822210000.mpg'
2010-10-21 20:31:09.681 ProgramInfo(): Updated pathname '':'' -> '129_20090822200000.mpg'
2010-10-21 20:31:09.812 ProgramInfo(): Updated pathname '':'' -> '129_20090811210000.mpg'
2010-10-21 20:31:09.909 ProgramInfo(): Updated pathname '':'' -> '129_20090804210000.mpg'
2010-10-21 20:31:09.993 ProgramInfo(): Updated pathname '':'' -> '129_20090728210000.mpg'
2010-10-21 20:31:10.088 ProgramInfo(): Updated pathname '':'' -> '129_20090721210000.mpg'
2010-10-21 20:31:10.179 ProgramInfo(): Updated pathname '':'' -> '129_20090714210000.mpg'
2010-10-21 20:31:10.233 ProgramInfo(): Updated pathname '':'' -> '129_20090707210000.mpg'
2010-10-21 20:31:10.265 ProgramInfo(): Updated pathname '':'' -> '129_20090630210000.mpg'
2010-10-21 20:40:02.806 MainServer::ANN Monitor
2010-10-21 20:40:02.807 adding: gandalf as a client (events: 0)
2010-10-21 20:40:50.935 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 256
2010-10-21 20:45:30.117 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 20:45:30.118 Using runtime prefix = /usr
2010-10-21 20:45:30.119 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 20:45:30.120 Empty LocalHostName.
2010-10-21 20:45:30.121 Using localhost value of gandalf
2010-10-21 20:45:30.131 New DB connection, total: 1
2010-10-21 20:45:30.136 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:45:30.136 Closing DB connection named 'DBManager0'
2010-10-21 20:45:30.138 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:45:30.144 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 20:45:30.147 MythBackend: Starting up as the master server.
2010-10-21 20:45:30.154 New DB connection, total: 2
2010-10-21 20:45:30.155 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:45:30.163 New DB connection, total: 3
2010-10-21 20:45:30.164 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:45:30.225 Channel(/dev/videoivtv) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-10-21 20:45:30.238 New DB scheduler connection
2010-10-21 20:45:30.239 Connected to database 'mythconverg' at host: localhost
2010-10-21 20:45:30.264 Enabling Upnpmedia rebuild thread.
2010-10-21 20:45:31.469 Main::Registering HttpStatus Extension
2010-10-21 20:45:31.470 Enabled verbose msgs:  important general
2010-10-21 20:45:31.473 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 20:45:33.248 Reschedule requested for id -1.
2010-10-21 20:45:33.383 Scheduled 30 items in 0.1 = 0.02 match + 0.10 place
2010-10-21 20:45:33.388 Seem to be woken up by USER
2010-10-21 20:45:40.273 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-21 20:45:40.340 UPnpMedia: BuildMediaMap Done. Found 92 objects
2010-10-21 20:46:50.251 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 20:50:02.781 MainServer::ANN Monitor
2010-10-21 20:50:02.782 adding: gandalf as a client (events: 0)
2010-10-21 21:00:02.732 MainServer::ANN Monitor
2010-10-21 21:00:02.733 adding: gandalf as a client (events: 0)
2010-10-21 21:01:50.312 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 256
2010-10-21 21:05:30.198 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 21:05:30.200 Using runtime prefix = /usr
2010-10-21 21:05:30.201 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 21:05:30.202 Empty LocalHostName.
2010-10-21 21:05:30.203 Using localhost value of gandalf
2010-10-21 21:05:30.212 New DB connection, total: 1
2010-10-21 21:05:30.217 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:05:30.218 Closing DB connection named 'DBManager0'
2010-10-21 21:05:30.220 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:05:30.226 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 21:05:30.229 MythBackend: Starting up as the master server.
2010-10-21 21:05:30.235 New DB connection, total: 2
2010-10-21 21:05:30.237 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:05:30.244 New DB connection, total: 3
2010-10-21 21:05:30.246 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:05:30.303 Channel(/dev/videoivtv) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-10-21 21:05:30.314 New DB scheduler connection
2010-10-21 21:05:30.316 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:05:30.341 Enabling Upnpmedia rebuild thread.
2010-10-21 21:05:31.546 Main::Registering HttpStatus Extension
2010-10-21 21:05:31.547 Enabled verbose msgs:  important general
2010-10-21 21:05:31.550 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 21:05:33.324 Reschedule requested for id -1.
2010-10-21 21:05:33.460 Scheduled 30 items in 0.1 = 0.02 match + 0.11 place
2010-10-21 21:05:33.464 Seem to be woken up by USER
2010-10-21 21:05:40.351 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-21 21:05:40.418 UPnpMedia: BuildMediaMap Done. Found 92 objects
2010-10-21 21:06:50.327 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 21:10:02.718 MainServer::ANN Monitor
2010-10-21 21:10:02.719 adding: gandalf as a client (events: 0)
2010-10-21 21:17:02.174 MainServer::ANN Monitor
2010-10-21 21:17:02.176 adding: gandalf as a client (events: 0)
2010-10-21 21:17:02.380 ProgramInfo(1001_20101020210000.mpg), Error: GetPlaybackURL: '1001_20101020210000.mpg' should be local, but it can not be found.
2010-10-21 21:17:02.389 ProgramInfo(1002_20101020220000.mpg), Error: GetPlaybackURL: '1002_20101020220000.mpg' should be local, but it can not be found.
2010-10-21 21:20:02.798 MainServer::ANN Monitor
2010-10-21 21:20:02.799 adding: gandalf as a client (events: 0)
2010-10-21 21:21:50.449 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 256
2010-10-21 21:25:30.287 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 21:25:30.288 Using runtime prefix = /usr
2010-10-21 21:25:30.289 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 21:25:30.290 Empty LocalHostName.
2010-10-21 21:25:30.291 Using localhost value of gandalf
2010-10-21 21:25:30.301 New DB connection, total: 1
2010-10-21 21:25:30.306 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:25:30.307 Closing DB connection named 'DBManager0'
2010-10-21 21:25:30.308 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:25:30.314 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 21:25:30.317 MythBackend: Starting up as the master server.
2010-10-21 21:25:30.324 New DB connection, total: 2
2010-10-21 21:25:30.325 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:25:30.333 New DB connection, total: 3
2010-10-21 21:25:30.334 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:25:30.391 Channel(/dev/videoivtv) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-10-21 21:25:30.402 New DB scheduler connection
2010-10-21 21:25:30.404 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:25:30.429 Enabling Upnpmedia rebuild thread.
2010-10-21 21:25:31.634 Main::Registering HttpStatus Extension
2010-10-21 21:25:31.635 Enabled verbose msgs:  important general
2010-10-21 21:25:31.638 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 21:25:33.413 Reschedule requested for id -1.
2010-10-21 21:25:33.557 Scheduled 30 items in 0.1 = 0.02 match + 0.11 place
2010-10-21 21:25:33.562 Seem to be woken up by USER
2010-10-21 21:25:40.438 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-21 21:25:40.505 UPnpMedia: BuildMediaMap Done. Found 92 objects
2010-10-21 21:26:50.416 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 21:30:02.804 MainServer::ANN Monitor
2010-10-21 21:30:02.805 adding: gandalf as a client (events: 0)
2010-10-21 21:37:47.667 MainServer::ANN Monitor
2010-10-21 21:37:47.675 adding: gandalf as a client (events: 0)
2010-10-21 21:37:47.706 MainServer::ANN Monitor
2010-10-21 21:37:47.722 adding: gandalf as a client (events: 1)
2010-10-21 21:38:29.219 MainServer::ANN Monitor
2010-10-21 21:38:29.230 adding: gandalf as a client (events: 0)
2010-10-21 21:38:29.248 MainServer::ANN Monitor
2010-10-21 21:38:29.277 adding: gandalf as a client (events: 1)
2010-10-21 21:40:02.791 MainServer::ANN Monitor
2010-10-21 21:40:02.792 adding: gandalf as a client (events: 0)
2010-10-21 21:41:50.492 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 256
2010-10-21 21:45:30.523 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-10-21 21:45:30.536 Using runtime prefix = /usr
2010-10-21 21:45:30.537 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 21:45:30.538 Empty LocalHostName.
2010-10-21 21:45:30.539 Using localhost value of gandalf
2010-10-21 21:45:30.549 New DB connection, total: 1
2010-10-21 21:45:30.554 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:45:30.555 Closing DB connection named 'DBManager0'
2010-10-21 21:45:30.556 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:45:30.563 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 21:45:30.566 MythBackend: Starting up as the master server.
2010-10-21 21:45:30.575 New DB connection, total: 2
2010-10-21 21:45:30.576 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:45:30.584 New DB connection, total: 3
2010-10-21 21:45:30.585 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:45:30.654 Channel(/dev/videoivtv) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2010-10-21 21:45:30.665 New DB scheduler connection
2010-10-21 21:45:30.667 Connected to database 'mythconverg' at host: localhost
2010-10-21 21:45:30.705 Enabling Upnpmedia rebuild thread.
2010-10-21 21:45:31.911 Main::Registering HttpStatus Extension
2010-10-21 21:45:31.912 Enabled verbose msgs:  important general
2010-10-21 21:45:31.916 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 21:45:33.678 Reschedule requested for id -1.
2010-10-21 21:45:33.834 Scheduled 30 items in 0.1 = 0.02 match + 0.13 place
2010-10-21 21:45:33.840 Seem to be woken up by USER
2010-10-21 21:45:40.715 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-10-21 21:45:40.783 UPnpMedia: BuildMediaMap Done. Found 92 objects
2010-10-21 21:46:50.681 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 21:50:02.776 MainServer::ANN Monitor
2010-10-21 21:50:02.777 adding: gandalf as a client (events: 0)

```

---

### Post by scottishnarn on 2010-10-21
I also tried running mythbackend from the command line rather than from using the upstart scripts and I got an error which does appear in the logs
```
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 256
```
This error also appeared when running mythfrontend from the command line.

---

### Post by chrismurf2900 on 2010-10-22
Okay, so here is what fixed my issue.

In the frontend settings, under "TV Settings," "Playback," I just had to change the playback profile to something different.  In my case it was "VDPAU High Quality."  Which fixed my problem.

I hope that helps someone else who might also have the same kind of issue.

---

### Post by scottishnarn on 2010-10-23
Thanks but this isn't the problem on my system as the backend crashes every 20mins whether the front end is running or not. Also all remote machines connected to the backend also crash.

---

### Post by scottishnarn on 2010-10-23
I've just installed 10.10 on another partition on the same machine and installed mythtv. I'm getting exactly the same error. 

Any help? Please.

---

### Post by scottishnarn on 2010-10-24
I've obviously doing something wrong, as I'm getting the same error on Ubuntu 10.04, 9.10, 10.10 using 0.23, 0.23.1 and 0.24 on two different machines.

Yet up until last week it was all working perfectly and had been for years. 

Any ideas?

---

### Post by scottishnarn on 2010-10-24
Solved. 

It turns out that it was my new router/ADSL modem's upnp service which was killing mythbackend. Disabling it seems to have fixed it. I hope I don't need to use that feature in the future. 

OK, on reflection this should have been more obvious, the fact that it was affecting more than one machine, running completely different versions of Ubuntu and MythTV and the fact that no-one else was having the same issue should have flagged up that it wasn't a software or a computer hardware issue, but it was only after installing an older version of Ubuntu and MythTV that I knew worked on my hardware, that I finally thought about my new router.

---

### Post by alanma on 2010-12-15
Aaah brilliant thread, thanks for posting your answer

Like you I'd just had a new router only also have just had the backend fill up so thought that was why I was getting lots of attempts of the same recordings. I couldn't work out why the front end was crashing....

Turning off uPNP fixed it

cheers

Alan

---

### Post by ian dobson on 2010-12-15
Hi,

I think you can disable upnp in mythtv with the command line option -noupnp (atleast for the backend)

Regards
Ian Dobson

---

