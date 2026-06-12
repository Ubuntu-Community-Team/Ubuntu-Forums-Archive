---
title: "Poll took an unusually long time"
date: 2012-08-21
forum: Mythbuntu
---

### Post by twinfrey on 2012-08-21
I have been trying to work out problems with mythtv before the start of NFL but I keep running into problems.  Yesterday I recorded a program and tried to start another one about 20 minutes later.  When it tried to record the second one it said "[FONT=Courier New]Poll took an unusually long time[/FONT]" and it tried to record on the wrong tuner (because the requested tuner timed out) so it got stuck in a state of "tuning".  Has anybody seen this problem?
 
 
 
```
Aug 20 20:24:21 twinfreyPC mythbackend[1524]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 20 20:25:18 twinfreyPC mythbackend[1524]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Aug 20 20:30:22 twinfreyPC mythbackend[1524]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Aug 20 20:35:29 twinfreyPC mythbackend[1524]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Aug 20 20:38:21 twinfreyPC mythbackend[1524]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 20 20:38:47 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 33529 ms
Aug 20 20:40:34 twinfreyPC mythbackend[1524]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Aug 20 20:40:35 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 107164 ms
Aug 20 20:41:06 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 31593 ms
Aug 20 20:41:55 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 49398 ms
Aug 20 20:42:09 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 13186 ms
Aug 20 20:42:11 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2734 ms
Aug 20 20:42:18 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 6533 ms
Aug 20 20:42:22 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3751 ms
Aug 20 20:42:27 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4210 ms
Aug 20 20:42:37 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 9485 ms
Aug 20 20:42:47 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 9703 ms
Aug 20 20:42:52 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5227 ms
Aug 20 20:42:58 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 6122 ms
Aug 20 20:43:15 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 17059 ms
Aug 20 20:43:21 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5347 ms
Aug 20 20:43:43 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 20398 ms
Aug 20 20:43:51 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 7525 ms
Aug 20 20:43:56 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3968 ms
Aug 20 20:43:58 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2831 ms
Aug 20 20:44:01 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3001 ms
Aug 20 20:44:07 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 6049 ms
Aug 20 20:44:12 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4138 ms
Aug 20 20:44:19 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 7380 ms
Aug 20 20:44:23 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3848 ms
Aug 20 20:44:33 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 9437 ms
Aug 20 20:44:37 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4258 ms
Aug 20 20:44:42 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5300 ms
Aug 20 20:44:46 twinfreyPC mythbackend[1524]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Aug 20 20:44:54 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4525 ms
Aug 20 20:45:00 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 6122 ms
Aug 20 20:45:11 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 10574 ms
Aug 20 20:45:17 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2735 ms
Aug 20 20:45:34 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 15051 ms
Aug 20 20:45:41 twinfreyPC mythbackend[1524]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Aug 20 20:45:42 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 8034 ms
Aug 20 20:45:47 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3969 ms
Aug 20 20:45:52 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5589 ms
Aug 20 20:46:02 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5783 ms
Aug 20 20:46:24 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 21995 ms
Aug 20 20:47:09 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 42466 ms
Aug 20 20:47:19 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 10139 ms
Aug 20 20:47:26 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 7186 ms
Aug 20 20:47:48 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 21971 ms
Aug 20 20:47:56 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4162 ms
Aug 20 20:48:03 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 6775 ms
Aug 20 20:48:09 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4573 ms
Aug 20 20:48:16 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3629 ms
Aug 20 20:48:28 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 11978 ms
Aug 20 20:48:40 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 11518 ms
Aug 20 20:48:43 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2856 ms
Aug 20 20:48:46 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2565 ms
Aug 20 20:49:07 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 21221 ms
Aug 20 20:49:35 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 25939 ms
Aug 20 20:49:49 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 8977 ms
Aug 20 20:50:01 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 11349 ms
Aug 20 20:50:08 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5856 ms
Aug 20 20:50:13 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4380 ms
Aug 20 20:50:47 twinfreyPC mythbackend[1524]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Aug 20 20:50:51 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 38207 ms
Aug 20 20:51:05 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 14107 ms
Aug 20 20:51:32 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 26617 ms
Aug 20 20:51:37 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3194 ms
Aug 20 20:51:51 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 13236 ms
Aug 20 20:52:03 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 10501 ms
Aug 20 20:52:07 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4114 ms
Aug 20 20:52:10 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2903 ms
Aug 20 20:52:13 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3291 ms
Aug 20 20:52:16 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 2783 ms
Aug 20 20:52:21 twinfreyPC mythbackend[1524]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 20 20:52:29 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 12244 ms
Aug 20 20:52:44 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 15365 ms
Aug 20 20:52:59 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 13357 ms
Aug 20 20:53:04 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4646 ms
Aug 20 20:53:09 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5178 ms
Aug 20 20:53:25 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 16357 ms
Aug 20 20:53:44 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 13865 ms
Aug 20 20:54:03 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 19116 ms
Aug 20 20:54:10 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 7017 ms
Aug 20 20:54:13 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 3243 ms
Aug 20 20:54:18 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4670 ms
Aug 20 20:54:23 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5154 ms
Aug 20 20:54:29 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5323 ms
Aug 20 20:54:34 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 5396 ms
Aug 20 20:54:38 twinfreyPC mythbackend[1524]: W DeviceReadBuffer DeviceReadBuffer.cpp:525 (Poll) DevRdB(/dev/dvb/adapter0/frontend0): Poll took an unusually long time 4452 ms
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 14.
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 2 items in 0.0 = 0.00 match + 0.02 place
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I TVRecEvent tv_rec.cpp:1518 (HandlePendingRecordings) TVRec(3): ASK_RECORDING 3 0 0 0
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(3): Changing from None to RecordingOnly
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I TVRecEvent mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 10
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I TVRecEvent tv_rec.cpp:3456 (TuningCheckForHWChange) TVRec(3): HW Tuner: 3->3
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Tuning recording: "Law & Order: Special Victims Unit":"Bad Blood": channel 1352 on cardid 3, sourceid 1
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 2 items in 0.0 = 0.00 match + 0.01 place
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(3:/dev/dvb/adapter1/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Aug 20 20:54:44 twinfreyPC mythbackend[1524]: E SignalMonitor dvbchannel.cpp:1051 (GetSNR) DVBChan(3:/dev/dvb/adapter1/frontend0): Getting Frontend signal/noise ratio failed.#012#011#011#011eno: Invalid argument (22)

```

---

