---
title: "Stuck listings in &quot;upcoming recordings&quot;"
date: 2010-12-09
forum: Mythbuntu
---

### Post by winewood on 2010-12-09
Edit: Mythubuntu 10.4 
 
My mythweb has been acting strange for some time now. Currently, under the upcoming recordings list, a show appears as "Currently Recording" since yesterday. It is not currently recording anything. This recording does not appear in the "Watch Recordings" selection menu on the front end, nor does it appear in the "Upcoming Recordings" list on the frontend.
 
The stuck programs may or may not have actually recorded (most of the time not). This started 3 weeks ago. 6 programs in a day may record, but randomly, one will get stuck on the "upcoming" page in mythweb. The only way to remove this "stuck" recording from mythweb is to restart my machine. If I leave four or five up, I will be unable to watch tv or record.
 
I have 2 different tuners on my box, and swapped which one will record all the programs. This did not fix thep problem. I will post a picture if someone can tell where a free upload is so I can link.
 
Any help would be appreciated.
 
I am posting logs from when I recorded a program at 13:00 on 11-29-2010. There is not obvious errors.
 
```
2010-11-29 13:17:04.651 ProgramInfo(1081_20101114190000.mpg), Error: GetPlaybackURL: '1081_20101114190000.mpg' should be local, but it can not be found.
2010-11-29 13:17:04.653 ProgramInfo(1081_20101114200000.mpg), Error: GetPlaybackURL: '1081_20101114200000.mpg' should be local, but it can not be found.
2010-11-29 13:22:31.984 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-29 13:36:32.132 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-29 13:36:32.141 Expiring 268 MBytes for 1682 @ Sun Nov 28 13:00:00 2010 => The Mysteries of Alfred Hedgehog "Cabana Drama; Three Star Mystery"
2010-11-29 13:36:32.243 autoexpire: Expiring Program: Expiring 268 MBytes for 1682 @ Sun Nov 28 13:00:00 2010 => The Mysteries of Alfred Hedgehog "Cabana Drama; Three Star Mystery"
2010-11-29 13:36:32.254 ProgramInfo(): Updated pathname '':'' -> '1682_20101128131711.mpg'
2010-11-29 13:36:32.360 ProgramInfo(): Updated pathname '':'' -> '1682_20101128131711.mpg'
2010-11-29 13:36:35.311 ProgramInfo(): Updated pathname '':'' -> '1682_20101128131711.mpg'
2010-11-29 13:40:31.283 UPnpMedia: BuildMediaMap VIDEO scan starting in :/opt/videos:
2010-11-29 13:40:31.334 UPnpMedia: BuildMediaMap Done. Found 18 objects
2010-11-29 13:50:32.357 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-29 13:59:00.981 Reschedule requested for id 0.
2010-11-29 13:59:02.285 Scheduled 149 items in 1.3 = 0.00 match + 1.29 place
2010-11-29 13:59:02.340 scheduler: Scheduled items: Scheduled 149 items in 1.3 = 0.00 match + 1.29 place
2010-11-29 13:59:30.327 TVRec(7): ASK_RECORDING 7 29 0 0
2010-11-29 13:59:30.414 TVRec(6): ASK_RECORDING 6 29 0 0
2010-11-29 14:00:01.701 ProgramInfo(): Updated pathname '':'' -> '1051_20101129120000.mpg'
2010-11-29 14:00:01.704 ProgramInfo(): Updated pathname '':'' -> '1051_20101129120000.mpg'
2010-11-29 14:00:01.709 Finished recording The Real Housewives of Orange County "Nothing Is as It Seems": channel 1051
2010-11-29 14:00:01.715 scheduler: Finished recording: The Real Housewives of Orange County "Nothing Is as It Seems": channel 1051
2010-11-29 14:00:02.276 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-29 14:00:02.282 ProgramInfo(): Updated pathname '':'' -> '1051_20101129120000.mpg'
2010-11-29 14:00:02.370 ProgramInfo(): Updated pathname '':'' -> '1051_20101129140001.mpg'
2010-11-29 14:00:03.097 TVRec(6): RingBufferChanged()
2010-11-29 14:00:03.103 ProgramInfo(): Updated pathname '':'' -> '1051_20101129120000.mpg'
2010-11-29 14:00:03.112 Finished recording The Real Housewives of Orange County "Nothing Is as It Seems": channel 1051
2010-11-29 14:00:03.210 ProgramInfo(): Updated pathname '':'' -> '1051_20101129120000.mpg'
2010-11-29 14:00:03.448 ProgramInfo(): Updated pathname '':'' -> '1051_20101129140000.mpg'
2010-11-29 14:00:03.498 TVRec(7): Changing from None to RecordingOnly
2010-11-29 14:00:03.523 TVRec(7): HW Tuner: 7->7

```
 
at 18:30 recording a program on 12-02-2010
 
```
2010-12-02 18:19:14.861 UPnpMedia: BuildMediaMap VIDEO scan starting in :/opt/videos:
2010-12-02 18:19:14.894 UPnpMedia: BuildMediaMap Done. Found 18 objects
2010-12-02 18:24:31.881 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-12-02 18:29:00.075 Reschedule requested for id 0.
2010-12-02 18:29:01.227 Scheduled 147 items in 1.1 = 0.00 match + 1.14 place
2010-12-02 18:29:01.265 scheduler: Last message repeated 3 times: Finished recording: Zula Patrol "Bula's Spin Party; Day for Night": channel 1682
2010-12-02 18:29:01.268 scheduler: Scheduled items: Scheduled 147 items in 1.1 = 0.00 match + 1.14 place
2010-12-02 18:29:29.816 ProgramInfo(): Updated pathname '':'' -> '1682_20101202180000.mpg'
2010-12-02 18:29:29.816 TVRec(6): ASK_RECORDING 6 29 0 0
2010-12-02 18:29:30.063 TVRec(7): ASK_RECORDING 7 29 0 0
2010-12-02 18:30:02.469 TVRec(6): HW Tuner: 6->6
2010-12-02 18:30:02.492 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-12-02 18:30:02.504 Started recording: Entertainment Tonight "London Red Carpet Event": channel 1081 on cardid 6, sourceid 1
2010-12-02 18:30:02.514 scheduler: Started recording: Entertainment Tonight "London Red Carpet Event": channel 1081 on cardid 6, sourceid 1
2010-12-02 18:30:02.908 ProgramInfo(): Updated pathname '':'' -> '1682_20101202180000.mpg'
2010-12-02 18:30:02.912 ProgramInfo(): Updated pathname '':'' -> '1682_20101202180000.mpg'
2010-12-02 18:30:02.914 Finished recording Turbo Dogs "Pinata Party; What a Card": channel 1682
2010-12-02 18:30:02.917 scheduler: Finished recording: Turbo Dogs "Pinata Party; What a Card": channel 1682
2010-12-02 18:30:03.352 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-12-02 18:30:03.427 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 18:30:03.442 ProgramInfo(): Updated pathname '':'' -> '1682_20101202180000.mpg'
2010-12-02 18:30:03.532 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 18:30:03.558 ProgramInfo(): Updated pathname '':'' -> '1682_20101202180000.mpg'
2010-12-02 18:30:04.670 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-12-02 18:30:04.677 Using runtime prefix = /usr
2010-12-02 18:30:04.678 Using configuration directory = /home/mythtv/.mythtv
2010-12-02 18:30:04.680 Empty LocalHostName.
2010-12-02 18:30:04.690 Using localhost value of MythTV
2010-12-02 18:30:04.805 New DB connection, total: 1
2010-12-02 18:30:04.815 Connected to database 'mythconverg' at host: localhost
2010-12-02 18:30:04.815 Closing DB connection named 'DBManager0'
2010-12-02 18:30:04.818 Connected to database 'mythconverg' at host: localhost
2010-12-02 18:30:04.824 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-02 18:30:04.830 ProgramInfo(): Updated pathname '':'' -> '1682_20101202180000.mpg'
2010-12-02 18:30:07.458 AFD: Opened codec 0x7f54f0053fe0, id(MPEG2VIDEO) type(Video)
2010-12-02 18:30:07.459 AFD: codec AC3 has 2 channels
2010-12-02 18:30:07.461 AFD: Opened codec 0x7f54f0052f20, id(AC3) type(Audio)
2010-12-02 18:30:07.463 AFD: codec AC3 has 2 channels
2010-12-02 18:30:07.465 AFD: Opened codec 0x7f54f0059c00, id(AC3) type(Audio)
2010-12-02 18:30:07.949 Preview: Grabbed preview '/opt/livetv/1682_20101202180000.mpg' 704x480@64s
2010-12-02 18:30:08.162 ~MythContext waiting for threads to exit.
2010-12-02 18:38:32.043 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-12-02 18:38:32.122 Expiring 629 MBytes for 1682 @ Wed Dec 1 18:00:00 2010 => Turbo Dogs "What a Lulu!; Can't Do It All"
2010-12-02 18:38:32.175 autoexpire: Expiring Program: Expiring 629 MBytes for 1682 @ Wed Dec 1 18:00:00 2010 => Turbo Dogs "What a Lulu!; Can't Do It All"
2010-12-02 18:38:32.184 ProgramInfo(): Updated pathname '':'' -> '1682_20101201180000.mpg'
2010-12-02 18:38:32.251 ProgramInfo(): Updated pathname '':'' -> '1682_20101201180000.mpg'
2010-12-02 18:38:35.204 ProgramInfo(): Updated pathname '':'' -> '1682_20101201180000.mpg'
2010-12-02 18:43:56.251 [mpeg2video @ 0x7f562207b360]ac-tex damaged at 38 62
2010-12-02 18:43:56.251 [mpeg2video @ 0x7f562207b360]Warning MVs not available
2010-12-02 18:43:59.444 ProgramInfo(): Updated pathname '':'' -> '1081_20101202160000.mpg'
2010-12-02 18:44:00.440 ~MythContext waiting for threads to exit.
2010-12-02 18:44:00.493 ProgramInfo(): Updated pathname '':'' -> '1081_20101202160000.mpg'
2010-12-02 18:44:00.585 ProgramInfo(): Updated pathname '':'' -> '1081_20101202160000.mpg'
2010-12-02 18:44:01.508 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-12-02 18:44:01.510 Using runtime prefix = /usr
2010-12-02 18:44:01.510 Using configuration directory = /home/mythtv/.mythtv
2010-12-02 18:44:01.511 Empty LocalHostName.
2010-12-02 18:44:01.512 Using localhost value of MythTV
2010-12-02 18:44:01.569 New DB connection, total: 1
2010-12-02 18:44:01.578 Connected to database 'mythconverg' at host: localhost
2010-12-02 18:44:01.579 Closing DB connection named 'DBManager0'
2010-12-02 18:44:01.582 Connected to database 'mythconverg' at host: localhost
2010-12-02 18:44:01.588 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-02 18:44:01.593 ProgramInfo(): Updated pathname '':'' -> '1081_20101202160000.mpg'
2010-12-02 18:44:01.926 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:01.935 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:01.969 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.003 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.005 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.007 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.008 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.009 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.011 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.012 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.014 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.015 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.016 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.017 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.019 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.020 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.021 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.022 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.024 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.025 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.026 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.029 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.031 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.068 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.070 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.071 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.072 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.074 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.075 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.076 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.077 [mpeg2video @ 0x7fa0ab35c360]mpeg_decode_postinit() failure
2010-12-02 18:44:02.132 AFD: Opened codec 0x219bdf0, id(MPEG2VIDEO) type(Video)
2010-12-02 18:44:02.133 AFD: codec AC3 has 6 channels
2010-12-02 18:44:02.134 AFD: Opened codec 0x2199cc0, id(AC3) type(Audio)
2010-12-02 18:44:02.134 AFD: codec AC3 has 1 channels
2010-12-02 18:44:02.135 AFD: Opened codec 0x219a320, id(AC3) type(Audio)
2010-12-02 18:44:02.997 Preview: Grabbed preview '/opt/recordings/1081_20101202160000.mpg' 1920x1088@64s
2010-12-02 18:44:03.219 ~MythContext waiting for threads to exit.
2010-12-02 18:44:03.293 commflag: Commercial Flagging Finished: The Oprah Winfrey Show "Best of Oprah: Aging Beauty Cybill Shepherd, Dynasty's Linda Evans & Desperate Housewives' Teri Hatcher" recorded from channel 1081 at Thu Dec 2 16:00:00 2010 (6 commercial break(s))
2010-12-02 18:44:03.348 ProgramInfo(): Updated pathname '':'' -> '1081_20101202160000.mpg'
2010-12-02 18:46:40.376 Error: offset>181, pes length & current can not be queried
2010-12-02 18:49:17.914 UPnpMedia: BuildMediaMap VIDEO scan starting in :/opt/videos:
2010-12-02 18:49:17.971 UPnpMedia: BuildMediaMap Done. Found 18 objects
2010-12-02 18:52:32.336 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-12-02 18:52:40.940 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 18:52:40.952 TVRec(6): Changing from WatchingLiveTV to None
2010-12-02 18:52:41.200 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 18:52:41.204 Finished recording Entertainment Tonight "London Red Carpet Event": channel 1081
2010-12-02 18:52:41.216 scheduler: Finished recording: Entertainment Tonight "London Red Carpet Event": channel 1081
2010-12-02 18:52:41.226 ProgramInfo(1081_20101202183002.mpg), Error: Unknown type, recording width was 0
2010-12-02 18:52:41.261 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 18:52:41.264 Finished recording Entertainment Tonight "London Red Carpet Event": channel 1081
2010-12-02 18:52:41.265 ProgramInfo(1081_20101202183002.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2010-12-02 18:52:41.267 ProgramInfo(1081_20101202183002.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2010-12-02 18:52:41.275 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 18:52:41.466 ProgramInfo(): Updated pathname '':'' -> '1081_20101202183002.mpg'
2010-12-02 19:06:32.470 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-12-02 19:17:02.351 MainServer::ANN Monitor

```

---

