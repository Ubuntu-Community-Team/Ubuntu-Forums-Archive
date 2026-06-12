---
title: "Hauppauge HVR2250 Unable to Lock on Channels Until After Restart, EIT Scan Related?"
date: 2012-05-20
forum: Mythbuntu
---

### Post by km782 on 2012-05-20
I am having a problem with my tuner card using OTA signals.  About once a day the card is unable to tune to any channels.  If I go to "Watch Tv" the screen is black and I get the message that Mythtv is unable to get a lock.  This happens for every channel and I live in an area that is close to the TV stations and gets a strong signal.  Closing and restarting Mythbackend does not fix the problem.  If I restart the computer everything begins working again.  My specs are:

AMD 2.6Ghz A6-3650 CPU
4 GB of RAM
Asus F1A75-M Pro Motherboard
Hauppauge HVR-2250 Tuner Card

Running Mythbuntu 12.04 64 bit

mythtv-common:
  Installed: 2:0.25.0+fixes.20120517.ec51a97-0ubuntu0mythbuntu4
  Candidate: 2:0.25.0+fixes.20120520.b5b4c48-0ubuntu0mythbuntu4
  Version table:
     2:0.25.0+fixes.20120520.b5b4c48-0ubuntu0mythbuntu4 0
        500 [http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/) precise/main amd64 Packages
 *** 2:0.25.0+fixes.20120517.ec51a97-0ubuntu0mythbuntu4 0
        100 /var/lib/dpkg/status
     2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages

I can't prove it but I have a hunch that it has something to do with EIT.  Everything I read online with this tuner card people have it set not to do an EIT scan but that is because they are using QAM.  I did have the backend set to do active EIT scans with both tuners.  Since then I only checked the box for one tuner and it could be a coincidence but it seems like the problem happens less often.  If there is not way to get EIT to work with this card then I guess I could always go with a Schedules Direct subscription but I would really like to get this to work if at all possible.  I am posting my logs below.  If there is anything else that is important let me know.  Thank you for the help!

In this instance the tuner was set to end recording a program at 18:59 and begin recording another program at 18:59.  The recording for the second program stops at 3 mins 48 secs so I am assuming the problem begins at 19:02:48. (although I wasn't sitting in front of it when it happened)


Mythbackend.log
```
May 20 18:58:02 HTPC mythbackend[1523]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
May 20 18:58:32 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:1521 (HandlePendingRecordings) TVRec(1): ASK_RECORDING 1 26 0 0
May 20 18:59:00 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
May 20 18:59:00 HTPC mythbackend[1523]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
May 20 18:59:00 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(3): Changing from RecordingOnly to None
May 20 18:59:00 HTPC mythbackend[1523]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter1/frontend0): Device EOF detected
May 20 18:59:00 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:812 (FinishedRecording) TVRec(1): FinishedRecording(1541_2012-05-20T18:29:00) damaged recq:<RecordingQuality overall_score="0.783333" key="1541_2012-05-20T18:29:00" countinuity_error_count="28" packet_count="12417916">#012    <Gap start="2012-05-20T18:58:55" end="2012-05-20T19:00:00" duration="65" />#012</RecordingQuality>
May 20 18:59:00 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:812 (FinishedRecording) TVRec(3): FinishedRecording(1451_2012-05-20T18:29:00) damaged recq:<RecordingQuality overall_score="0.786667" key="1451_2012-05-20T18:29:00" countinuity_error_count="0" packet_count="13318117">#012    <Gap start="2012-05-20T18:58:56" end="2012-05-20T19:00:00" duration="64" />#012</RecordingQuality>
May 20 18:59:01 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to RecordingOnly
May 20 18:59:01 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
May 20 18:59:01 HTPC mythbackend[1523]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
May 20 18:59:01 HTPC mythbackend[1523]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Tuning recording: "60 Minutes": channel 1131 on cardid 1, sourceid 1
May 20 18:59:01 HTPC mythbackend[1523]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "The King of Queens" on cardid 1 (Recording => Recorded)
May 20 18:59:01 HTPC mythbackend[1523]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
May 20 18:59:01 HTPC mythbackend[1523]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "Family Guy" on cardid 3 (Recording => Recorded)
May 20 18:59:01 HTPC mythbackend[1523]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
May 20 18:59:01 HTPC mythbackend[1523]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1131_20120520185900.mpg): GetPlaybackURL: '1131_20120520185900.mpg' should be local, but it can not be found.
May 20 18:59:02 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 20 18:59:02 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
May 20 18:59:03 HTPC mythbackend[1523]: I CoreContext scheduler.cpp:634 (UpdateRecStatus) Updating status for "60 Minutes" on cardid 1 (Tuning => Recording)
May 20 18:59:03 HTPC mythbackend[1523]: I TVRecEvent tv_rec.cpp:3953 (TuningNewRecorder) TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/1131_20120520185900.mpg'
May 20 18:59:03 HTPC mythbackend[1523]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
May 20 18:59:03 HTPC mythbackend[1523]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
May 20 18:59:03 HTPC mythbackend[1523]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 19 items in 0.3 = 0.00 match + 0.31 place
May 20 18:59:12 HTPC mythbackend[1523]: I Metadata_199 jobqueue.cpp:2150 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "60 Minutes" recorded from channel 1131 at 2012-05-20T18:59:00
May 20 18:59:14 HTPC mythbackend[1523]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
May 20 18:59:14 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 20 18:59:14 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
May 20 18:59:14 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 20 18:59:14 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 1)
May 20 19:00:01 HTPC mythbackend[1523]: I EIT mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 13
May 20 19:00:17 HTPC mythbackend[1523]: I Commflag_200 jobqueue.cpp:2275 (DoFlagCommercialsThread) JobQueue: Commercial Detection Starting for "60 Minutes" recorded from channel 1131 at 2012-05-20T18:59:00
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 1)
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
May 20 19:00:18 HTPC mythbackend[1523]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(2176,9223372036854775807,#3) out of 149
May 20 19:01:08 HTPC mythbackend[1523]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
May 20 19:01:08 HTPC mythbackend[1523]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 17 items in 0.1 = 0.07 match + 0.08 place
May 20 19:04:18 HTPC mythbackend[1523]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
May 20 19:06:01 HTPC mythbackend[1523]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
May 20 19:09:02 HTPC mythbackend[1523]: E TVRecEvent dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(3:/dev/dvb/adapter1/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
May 20 19:09:02 HTPC mythbackend[1523]: W TVRecEvent dvbsignalmonitor.cpp:85 (DVBSignalMonitor) DVBSM(/dev/dvb/adapter1/frontend0): Cannot measure Signal Strength#012#011#011#011eno: Invalid argument (22)
May 20 19:09:19 HTPC mythbackend[1523]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
May 20 19:10:42 HTPC mythbackend[1523]: E TVRecEvent dvbchannel.cpp:1051 (GetSNR) DVBChan(3:/dev/dvb/adapter1/frontend0): Getting Frontend signal/noise ratio failed.#012#011#011#011eno: Invalid argument (22)
May 20 19:10:42 HTPC mythbackend[1523]: W TVRecEvent dvbsignalmonitor.cpp:87 (DVBSignalMonitor) DVBSM(/dev/dvb/adapter1/frontend0): Cannot measure S/N#012#011#011#011eno: Invalid argument (22)
May 20 19:10:55 HTPC mythbackend[1523]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(2221,9223372036854775807,#307) out of 456
May 20 19:10:57 HTPC mythbackend[1523]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(6826,9223372036854775807,#0) out of 456
May 20 19:11:00 HTPC mythbackend[1523]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(6826,9223372036854775807,#0) out of 456
May 20 19:11:12 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 20 19:11:12 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
May 20 19:11:12 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 20 19:11:12 HTPC mythbackend[1523]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 1)
May 20 19:14:26 HTPC mythbackend[1523]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
May 20 19:17:32 HTPC mythbackend[1523]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(3:/dev/dvb/adapter1/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
```


Syslog (error repeats over and over when I have this problem.  otherwise the log file is fairly quiet)
```
May 20 18:54:19 HTPC smbd[13396]: [2012/05/20 18:54:19.740796,  0] printing/print_cups.c:110(cups_connect)
May 20 18:54:19 HTPC smbd[13396]:   Unable to connect to CUPS server localhost:631 - Connection refused
May 20 18:54:19 HTPC smbd[790]: [2012/05/20 18:54:19.741259,  0] printing/print_cups.c:487(cups_async_callback)
May 20 18:54:19 HTPC smbd[790]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
May 20 19:03:01 HTPC kernel: [73123.852170] Event timed out
May 20 19:03:01 HTPC kernel: [73123.852184] saa7164_api_i2c_read() error, ret(2) = 0x32
May 20 19:03:01 HTPC kernel: [73123.852192] s5h1411_readreg: readreg error (ret == -5)
May 20 19:03:02 HTPC kernel: [73125.008407] Event timed out
May 20 19:03:02 HTPC kernel: [73125.008421] saa7164_api_i2c_read() error, ret(1) = 0x32
May 20 19:03:02 HTPC kernel: [73125.008429] s5h1411_readreg: readreg error (ret == -5)
May 20 19:03:11 HTPC kernel: [73133.852409] Event timed out
May 20 19:03:11 HTPC kernel: [73133.852424] saa7164_api_i2c_read() error, ret(1) = 0x32
May 20 19:03:11 HTPC kernel: [73133.852431] s5h1411_readreg: readreg error (ret == -5)
May 20 19:03:12 HTPC kernel: [73135.008333] Event timed out
May 20 19:03:12 HTPC kernel: [73135.008347] saa7164_api_i2c_read() error, ret(1) = 0x32
May 20 19:03:12 HTPC kernel: [73135.008354] s5h1411_readreg: readreg error (ret == -5)
May 20 19:03:21 HTPC kernel: [73143.852253] Event timed out
May 20 19:03:21 HTPC kernel: [73143.852267] saa7164_api_i2c_write() error, ret(1) = 0x32
May 20 19:03:21 HTPC kernel: [73143.852276] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
May 20 19:03:22 HTPC kernel: [73145.008175] Event timed out
May 20 19:03:22 HTPC kernel: [73145.008189] saa7164_api_i2c_write() error, ret(1) = 0x32
May 20 19:03:22 HTPC kernel: [73145.008198] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
May 20 19:03:31 HTPC kernel: [73153.852408] Event timed out
May 20 19:03:31 HTPC kernel: [73153.852422] saa7164_api_i2c_write() error, ret(1) = 0x32
May 20 19:03:31 HTPC kernel: [73153.852431] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
May 20 19:03:32 HTPC kernel: [73155.008082] Event timed out
May 20 19:03:32 HTPC kernel: [73155.008096] saa7164_api_i2c_write() error, ret(1) = 0x32
May 20 19:03:32 HTPC kernel: [73155.008105] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
```


dmesg
```
[83156.366194] saa7164_cmd_send() No free sequences
[83156.366198] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.366203] s5h1411_readreg: readreg error (ret == -5)
[83156.366304] saa7164_cmd_send() No free sequences
[83156.366309] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.366313] s5h1411_readreg: readreg error (ret == -5)
[83156.366324] saa7164_cmd_send() No free sequences
[83156.366328] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.366333] s5h1411_readreg: readreg error (ret == -5)
[83156.416543] saa7164_cmd_send() No free sequences
[83156.416555] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.416561] s5h1411_readreg: readreg error (ret == -5)
[83156.416567] saa7164_cmd_send() No free sequences
[83156.416571] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.416576] s5h1411_readreg: readreg error (ret == -5)
[83156.416586] saa7164_cmd_send() No free sequences
[83156.416590] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.416595] s5h1411_readreg: readreg error (ret == -5)
[83156.416697] saa7164_cmd_send() No free sequences
[83156.416701] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.416706] s5h1411_readreg: readreg error (ret == -5)
[83156.416716] saa7164_cmd_send() No free sequences
[83156.416721] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.416725] s5h1411_readreg: readreg error (ret == -5)
[83156.466937] saa7164_cmd_send() No free sequences
[83156.466949] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.466956] s5h1411_readreg: readreg error (ret == -5)
[83156.466961] saa7164_cmd_send() No free sequences
[83156.466966] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.466970] s5h1411_readreg: readreg error (ret == -5)
[83156.466980] saa7164_cmd_send() No free sequences
[83156.466984] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.466989] s5h1411_readreg: readreg error (ret == -5)
[83156.467091] saa7164_cmd_send() No free sequences
[83156.467095] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.467100] s5h1411_readreg: readreg error (ret == -5)
[83156.467110] saa7164_cmd_send() No free sequences
[83156.467115] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.467119] s5h1411_readreg: readreg error (ret == -5)
[83156.517335] saa7164_cmd_send() No free sequences
[83156.517347] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.517353] s5h1411_readreg: readreg error (ret == -5)
[83156.517359] saa7164_cmd_send() No free sequences
[83156.517364] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.517368] s5h1411_readreg: readreg error (ret == -5)
[83156.517378] saa7164_cmd_send() No free sequences
[83156.517382] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.517387] s5h1411_readreg: readreg error (ret == -5)
[83156.517489] saa7164_cmd_send() No free sequences
[83156.517494] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.517499] s5h1411_readreg: readreg error (ret == -5)
[83156.517509] saa7164_cmd_send() No free sequences
[83156.517514] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.517518] s5h1411_readreg: readreg error (ret == -5)
[83156.560422] saa7164_cmd_send() No free sequences
[83156.560435] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.560441] s5h1411_readreg: readreg error (ret == -5)
[83156.560447] saa7164_cmd_send() No free sequences
[83156.560451] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.560456] s5h1411_readreg: readreg error (ret == -5)
[83156.560463] saa7164_cmd_send() No free sequences
[83156.560468] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560474] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
[83156.560480] saa7164_cmd_send() No free sequences
[83156.560484] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560490] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
[83156.560496] saa7164_cmd_send() No free sequences
[83156.560500] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560506] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
[83156.560514] saa7164_cmd_send() No free sequences
[83156.560519] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560528] tda18271_write_regs: [3-0060|S] ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[83156.560536] tda18271_init: [3-0060|S] error -5 on line 831
[83156.560542] tda18271_tune: [3-0060|S] error -5 on line 909
[83156.560548] tda18271_set_params: [3-0060|S] error -5 on line 994
[83156.560554] saa7164_cmd_send() No free sequences
[83156.560558] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560564] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
[83156.560570] saa7164_cmd_send() No free sequences
[83156.560574] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560579] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
[83156.560585] saa7164_cmd_send() No free sequences
[83156.560589] saa7164_api_i2c_write() error, ret(1) = 0xc
[83156.560594] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
[83156.567727] saa7164_cmd_send() No free sequences
[83156.567740] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.567746] s5h1411_readreg: readreg error (ret == -5)
[83156.567752] saa7164_cmd_send() No free sequences
[83156.567756] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.567761] s5h1411_readreg: readreg error (ret == -5)
[83156.567771] saa7164_cmd_send() No free sequences
[83156.567775] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.567779] s5h1411_readreg: readreg error (ret == -5)
[83156.567883] saa7164_cmd_send() No free sequences
[83156.567888] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.567892] s5h1411_readreg: readreg error (ret == -5)
[83156.567903] saa7164_cmd_send() No free sequences
[83156.567907] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.567912] s5h1411_readreg: readreg error (ret == -5)
[83156.618120] saa7164_cmd_send() No free sequences
[83156.618132] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.618139] s5h1411_readreg: readreg error (ret == -5)
[83156.618144] saa7164_cmd_send() No free sequences
[83156.618149] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.618153] s5h1411_readreg: readreg error (ret == -5)
[83156.618164] saa7164_cmd_send() No free sequences
[83156.618168] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.618172] s5h1411_readreg: readreg error (ret == -5)
[83156.618277] saa7164_cmd_send() No free sequences
[83156.618281] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.618286] s5h1411_readreg: readreg error (ret == -5)
[83156.618296] saa7164_cmd_send() No free sequences
[83156.618301] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.618305] s5h1411_readreg: readreg error (ret == -5)
[83156.668758] saa7164_cmd_send() No free sequences
[83156.668770] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.668777] s5h1411_readreg: readreg error (ret == -5)
[83156.668782] saa7164_cmd_send() No free sequences
[83156.668787] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.668791] s5h1411_readreg: readreg error (ret == -5)
[83156.668801] saa7164_cmd_send() No free sequences
[83156.668805] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.668810] s5h1411_readreg: readreg error (ret == -5)
[83156.668912] saa7164_cmd_send() No free sequences
[83156.668917] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.668922] s5h1411_readreg: readreg error (ret == -5)
[83156.668932] saa7164_cmd_send() No free sequences
[83156.668937] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.668941] s5h1411_readreg: readreg error (ret == -5)
[83156.719160] saa7164_cmd_send() No free sequences
[83156.719172] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.719179] s5h1411_readreg: readreg error (ret == -5)
[83156.719184] saa7164_cmd_send() No free sequences
[83156.719189] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.719193] s5h1411_readreg: readreg error (ret == -5)
[83156.719204] saa7164_cmd_send() No free sequences
[83156.719208] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.719212] s5h1411_readreg: readreg error (ret == -5)
[83156.719322] saa7164_cmd_send() No free sequences
[83156.719326] saa7164_api_i2c_read() error, ret(1) = 0xc
[83156.719331] s5h1411_readreg: readreg error (ret == -5)
```


lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6530D]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:05.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
```

---

### Post by omontoya on 2012-08-20
I have the same issue. In my case it happens when both tuners of the hvr-2250 are used at some point. I see that this issue is happening since 2009 and posted in forums without a sensible solution. I have disabled one tuner, and it seems to be working better. It is not the best solution but it is better than running out of disk space due to messages going into your syslog and kern.log. Once you get the error, only a system reboot seems to fix the issue.

---

### Post by km782 on 2012-09-15
It looks like EIT has nothing to do with it.  I turned EIT off and have been relying on Schedules Direct for the last few months and am still having the same problem.  

The updates that come through periodically for Mythtv and Ubuntu seem to be altering the frequency of the errors though.  

At one point the errors disappeared completely with the updates in mid June.  I should have listened to my gut and turned all of the updates off at that point.  My system had been running for about 3 weeks straight with no tuning problems.  However, there was one little video glitch that I was hoping would be fixed with more updates.  

After updating the errors came back.  I couldn't figure out how to undo the updates (although I can see exactly what was installed in the software center) so I continued doing more updates hoping the problem would be fixed again.  Now it is as bad as it has ever been.  I am lucky if my system makes it 24 hours without having to restart it due to the errors.  This is getting extremely frustrating.

---

