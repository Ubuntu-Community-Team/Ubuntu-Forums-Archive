---
title: "PCTV 290e killing off channels..."
date: 2015-10-23
forum: Mythbuntu
---

### Post by JamesNorris on 2015-10-23
So I got a PCTV 290e on eBay, plugged it in, set up the backend and we're rolling. 

20 minutes later, the specific channel I am watching scrambles up and quits to the frontend. Now I can see other channels, but not this one. 
Deleted all channels, rescan, all good... this time it scrambles within 5 minutes. 

I've done this a couple of times and it seems to take a couple of chanels with it, but not all of them. 

The channels on my Nova-T card are unaffected. 
This is the frontend log from the moment I turn to an affected channel
```
2015-10-23 22:56:46.727766 N  Player(1): Waited 104ms for video buffers AALALAAAAAALAALL
2015-10-23 22:56:57.488292 W  Enabling buffering optimisations for low bitrate stream.
2015-10-23 23:00:02.857856 W  Enabling buffering optimisations for low bitrate stream.
2015-10-23 23:00:12.860004 E  FileRingBuf(/var/lib/mythtv/livetv/2101_20151023220002.mpg): OpenFile(): File too small (0B).
2015-10-23 23:00:12.860063 W  Enabling buffering optimisations for low bitrate stream.
2015-10-23 23:00:12.860169 E  Player(1): JumpToProgram's OpenFile failed (card type: DVB).
2015-10-23 23:00:12.860414 E  LiveTVChain has 9 entries
   DUMMY: 2105 (21:55:44 to 21:55:47)
     DVB: 2105 (21:55:47 to 21:55:56) discontinuous
   DUMMY: 2001 (21:55:56 to 21:55:58) discontinuous
     DVB: 2001 (21:55:58 to 21:56:09) discontinuous
   DUMMY: 19540 (21:56:09 to 21:56:11) discontinuous
     DVB: 19540 (21:56:11 to 21:56:40) discontinuous
     DVB: 2102 (21:56:40 to 21:56:57) discontinuous
   DUMMY: 2101 (21:56:57 to 22:00:00) discontinuous
*    DVB: 2101 (22:00:02 to 22:30:00)

2015-10-23 23:00:12.860462 E  Player(1): Unknown recorder error, exiting decoder
2015-10-23 23:00:12.905587 I  TV: Attempting to change from WatchingLiveTV to None
2015-10-23 23:00:12.913283 W  MythPainter: 7 images not yet de-allocated.
2015-10-23 23:00:12.913330 I  VDPAU Painter: Clearing VDPAU painter cache.
2015-10-23 23:00:13.338746 I  TV: Changing from WatchingLiveTV to None
2015-10-23 23:00:13.339195 I  TV: Exiting main playback loop.
2015-10-23 23:00:13.359808 N  Resuming idle timer

```

and my backend log:```
Oct 23 22:56:40 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:3603 (TuningCheckForHWChange) TVRec[10]: HW Tuner: 10->10
Oct 23 22:56:40 LCARS-HD mythbackend: mythbackend[29786]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Oct 23 22:56:40 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:3399 (RingBufferChanged) TVRec[10]: RingBufferChanged()
Oct 23 22:56:40 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:834 (FinishedRecording) TVRec[10]: FinishedRecording(19540_2015-10-23T21:56:11Z) damaged recq:<RecordingQuality overall_score="0" key="19540_2015-10-23T21:56:11Z" countinuity_error_count="2" packet_count="106052">#012    <Gap start="2015-10-23T21:35:00Z" end="2015-10-23T21:56:11Z" duration="1271" />#012    <Gap start="2015-10-23T21:56:39Z" end="2015-10-23T22:25:00Z" duration="1700" />#012</RecordingQuality>
Oct 23 22:56:56 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:3603 (TuningCheckForHWChange) TVRec[10]: HW Tuner: 10->10
Oct 23 22:56:57 LCARS-HD mythbackend: mythbackend[29786]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Oct 23 22:56:57 LCARS-HD mythbackend: mythbackend[29786]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Oct 23 22:56:57 LCARS-HD mythbackend: mythbackend[29786]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: LCARS-HD as a client (events: 0)
Oct 23 22:56:57 LCARS-HD mythbackend: mythbackend[29786]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Oct 23 22:56:57 LCARS-HD mythbackend: mythbackend[29786]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: LCARS-HD as a client (events: 1)
Oct 23 22:57:05 LCARS-HD mythbackend: mythbackend[29786]: E DVBRead mpeg/mpegstreamdata.cpp:364 (AssemblePSIP) MPEGStream[8](0x7f8930137d28): Error: offset>181, pes length & current cannot be queried
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 18 MB for 1001 at 2014-11-06T05:59:25Z => "BBC News"
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 3242 MB for 1001 at 2014-11-06T06:00:00Z => Breakfast
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 388 MB for 1080 at 2014-11-02T22:45:00Z => Click
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: E CoreContext programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1001_20141106055925.mpg): GetPlaybackURL: '1001_20141106055925.mpg' should be local, but it can not be found.
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: E CoreContext mainserver.cpp:2698 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/LCARS-HD/1001_20141106055925.mpg. File doesn't exist.  Database metadata will not be removed.
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: E CoreContext programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1001_20141106060000.mpg): GetPlaybackURL: '1001_20141106060000.mpg' should be local, but it can not be found.
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: E CoreContext mainserver.cpp:2698 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/LCARS-HD/1001_20141106060000.mpg. File doesn't exist.  Database metadata will not be removed.
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: E CoreContext programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(1080_20141102224500.mpg): GetPlaybackURL: '1080_20141102224500.mpg' should be local, but it can not be found.
Oct 23 22:57:33 LCARS-HD mythbackend: mythbackend[29786]: E CoreContext mainserver.cpp:2698 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/LCARS-HD/1080_20141102224500.mpg. File doesn't exist.  Database metadata will not be removed.
Oct 23 22:57:42 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 0 0 2015-10-30T18:58:00Z EITScanner
Oct 23 22:57:42 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 44 items in 0.1 = 0.02 match + 0.02 check + 0.03 place
Oct 23 22:59:27 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2015-10-25T10:55:00Z EITScanner
Oct 23 22:59:27 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 44 items in 0.0 = 0.02 match + 0.00 check + 0.03 place
Oct 23 23:00:02 LCARS-HD mythbackend: mythbackend[29786]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Oct 23 23:00:13 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[10]: Changing from WatchingLiveTV to None
Oct 23 23:00:13 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:834 (FinishedRecording) TVRec[10]: FinishedRecording(2101_2015-10-23T21:56:57Z) damaged recq:<RecordingQuality overall_score="0" key="2102_2015-10-23T21:56:40Z" countinuity_error_count="6" packet_count="44463">#012    <Gap start="2015-10-23T21:30:00Z" end="2015-10-23T21:56:40Z" duration="1600" />#012    <Gap start="2015-10-23T21:56:54Z" end="2015-10-23T22:00:00Z" duration="185" />#012</RecordingQuality>

```

Any ideas?

---

### Post by JamesNorris on 2015-10-24
Reboot seems to have no effect, but deleting and rescanning fixes temporarily. 

Here is the backend log at the very moment things go wrong; first from a scheduled recording and then on LiveTV

```
Oct 24 01:30:00 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[10]: Changing from None to RecordingOnly
Oct 24 01:30:00 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:3603 (TuningCheckForHWChange) TVRec[10]: HW Tuner: 10->10
Oct 24 01:30:01 LCARS-HD mythbackend: mythbackend[29786]: N Scheduler autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Oct 24 01:30:01 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2689 (HandleRecordingStatusChange) Tuning recording: Click: channel 2101 on cardid 10, sourceid 2
Oct 24 01:30:01 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2015-10-24T05:35:00Z EITScanner
Oct 24 01:30:01 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 0 0 2015-10-31T23:50:00Z EITScanner
Oct 24 01:30:01 LCARS-HD mythbackend: mythbackend[29786]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 54 items in 0.1 = 0.03 match + 0.03 check + 0.03 place
Oct 24 01:30:03 LCARS-HD mythbackend: mythbackend[29786]: I CoreContext scheduler.cpp:704 (UpdateRecStatus) Updating status for Click on cardid 10 (Tuning => Recording)
Oct 24 01:30:03 LCARS-HD mythbackend: mythbackend[29786]: I TVRecEvent tv_rec.cpp:4130 (TuningNewRecorder) TVRec[10]: rec->GetPathname(): '/var/lib/mythtv/recordings/2101_20151024003000.mpg'
Oct 24 01:30:25 LCARS-HD mythbackend: mythbackend[29786]: E DVBRead mpeg/mpegstreamdata.cpp:364 (AssemblePSIP) MPEGStream[10](0x7f892019ee98): Error: offset>181, pes length & current cannot be queried
Oct 24 01:31:04 LCARS-HD mythbackend: mythbackend[29786]: W DeviceReadBuffer recorders/DeviceReadBuffer.cpp:555 (Poll) DevRdB(/dev/dvb/adapter1/frontend0): Poll took an unusually long time 31091 ms
```


LiveTV. 

```
Oct 24 06:26:36 LCARS-HD mythbackend: mythbackend[2197]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 0 2015-10-24T11:00:00Z EITScanner
Oct 24 06:26:36 LCARS-HD mythbackend: mythbackend[2197]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 52 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Oct 24 06:27:55 LCARS-HD mythbackend: mythbackend[2197]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 0 2015-10-24T06:25:00Z EITScanner
Oct 24 06:27:56 LCARS-HD mythbackend: mythbackend[2197]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 52 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Oct 24 06:28:06 LCARS-HD mythbackend: mythbackend[2197]: E DVBRead mpeg/mpegstreamdata.cpp:364 (AssemblePSIP) MPEGStream[10](0x7fc84812bf18): Error: offset>181, pes length & current cannot be queried
Oct 24 06:28:11 LCARS-HD mythbackend: mythbackend[2197]: E DVBRead mpeg/mpegstreamdata.cpp:364 (AssemblePSIP) MPEGStream[10](0x7fc84812bf18): Error: offset>181, pes length & current cannot be queried
Oct 24 06:28:47 LCARS-HD mythbackend: mythbackend[2197]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2015-10-24T08:20:00Z EITScanner
Oct 24 06:28:47 LCARS-HD mythbackend: mythbackend[2197]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 52 items in 0.0 = 0.01 match + 0.00 check + 0.03 place
Oct 24 06:29:07 LCARS-HD mythbackend: mythbackend[2197]: W DeviceReadBuffer recorders/DeviceReadBuffer.cpp:555 (Poll) DevRdB(/dev/dvb/adapter1/frontend0): Poll took an unusually long time 51417 ms
```

---

### Post by JamesNorris on 2015-10-24
Update: It seems to be only some channels doing it. In particular, BBC News HD will drop out within seconds, taking a number of others, including CBeebies HD with it. 

BBC1 HD seems unaffected... could there be something in the signal that's throwing the device or MythTV?

---

