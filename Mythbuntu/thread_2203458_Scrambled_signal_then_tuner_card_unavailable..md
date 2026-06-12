---
title: "Scrambled signal then tuner card unavailable."
date: 2014-02-03
forum: Mythbuntu
---

### Post by z7APXKm on 2014-02-03
This is a cross post from the MythTV talk forum.  I'm having a problem with my MythTV media PC.

The symptoms are - 
 
1.  Failed or partially failed recording containing scrambled signal.
2.  Subsequent recordings fail.
3. Unable to view liveTV "all tuners are currently busy"
4.  Restart and everything is OK.

I'm using a TBS PCI-E DVB-T2 Dual TV Tuner Card (TBS6280).

```
mythtv:
  Installed: 2:0.25.2+fixes.20120802.46cab93-0ubuntu1
  Candidate: 2:0.25.2+fixes.20120802.46cab93-0ubuntu1
  Version table:
 *** 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 0
        100 /var/lib/dpkg/status
     2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages
```

mythpreviewgen.log
```

Jan 27 04:12:28 Myth mythcommflag[8148]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
Jan 27 10:30:29 Myth mythcommflag[10769]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythcommflag version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
Jan 27 10:30:29 Myth mythcommflag[10769]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jan 27 10:30:29 Myth mythcommflag[10769]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jan 27 10:30:29 Myth mythcommflag[10769]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jan 27 10:30:29 Myth mythcommflag[10769]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jan 27 10:30:29 Myth mythcommflag[10769]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jan 27 10:30:29 Myth mythcommflag[10769]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jan 27 10:30:29 Myth mythcommflag[10769]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jan 27 10:30:29 Myth mythcommflag[10769]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jan 27 10:30:29 Myth mythcommflag[10769]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_GB.UTF-8
Jan 27 10:30:29 Myth mythcommflag[10769]: E CoreContext configuration.cpp:64 (Load) Error parsing: /home/mythtv/.mythtv/config.xml at line: 1  column: 1
Jan 27 10:30:29 Myth mythcommflag[10769]: E CoreContext configuration.cpp:66 (Load) Error Msg: unexpected end of file
Jan 27 10:30:29 Myth mythcommflag[10769]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of Myth
Jan 27 10:30:29 Myth mythcommflag[10769]: E CoreContext configuration.cpp:64 (Load) Error parsing: /home/mythtv/.mythtv/config.xml at line: 1  column: 1
Jan 27 10:30:29 Myth mythcommflag[10769]: E CoreContext configuration.cpp:66 (Load) Error Msg: unexpected end of file
Jan 27 10:30:29 Myth mythcommflag[10769]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
Jan 27 10:30:29 Myth mythcommflag[10769]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0xd35450, id(MPEG2VIDEO) type(Video)
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP2 has 2 channels
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0xd4f1e0, id(MP2) type(Audio)
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 0 channels
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0xd50f70, id(MP3) type(Audio)
Jan 27 10:30:29 Myth mythcommflag[10769]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0xd52ec0, id(DVB_SUBTITLE) type(Subtitle)
Jan 27 10:30:32 Myth mythcommflag[10769]: I CoreContext ClassicCommDetector.cpp:359 (go) Finding Logo
Jan 27 10:30:32 Myth mythcommflag[10769]: E Decoder avformatdecoder.cpp:4216 (ProcessAudioPacket) AFD: Unknown audio decoding error
Jan 27 10:30:36  mythcommflag[10769]: last message repeated 169 times
Jan 27 10:30:36 Myth mythcommflag[10769]: W Decoder ringbuffer.cpp:1023 (WaitForReadsAllowed) RingBuf(/var/lib/mythtv/recordings/15608_20140127100000.mpg): Taking too long to be allowed to read..
Jan 27 10:30:37 Myth mythcommflag[10769]: E Decoder avformatdecoder.cpp:4216 (ProcessAudioPacket) AFD: Unknown audio decoding error
Jan 27 10:30:39  mythcommflag[10769]: last message repeated 4 times
Jan 27 10:30:39 Myth mythcommflag[10769]: W Decoder ringbuffer.cpp:1023 (WaitForReadsAllowed) RingBuf(/var/lib/mythtv/recordings/15608_20140127100000.mpg): Taking too long to be allowed to read..
--- END OF FILE ---

```

mythbackend.log
```

Jan 27 10:27:04 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:28:14  mythbackend[2342]: last message repeated 9 times
Jan 27 10:28:17 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:28:18 Myth mythbackend[2342]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jan 27 10:28:33 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:29:34  mythbackend[2342]: last message repeated 5 times
...
Jan 27 10:30:00 Myth mythbackend[2342]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(5): Changing from RecordingOnly to None
Jan 27 10:30:00 Myth mythbackend[2342]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
Jan 27 10:30:00 Myth mythbackend[2342]: I TVRecEvent tv_rec.cpp:816 (FinishedRecording) TVRec(5): FinishedRecording(15608_2014-01-27T10:00:00) damaged recq:<RecordingQuality overall_score="0" key="15608_2014-01-27T10:00:00" countinuity_error_count="4211" packet_count="76476">#012    <Gap start="2014-01-27T10:00:00" end="2014-01-27T10:18:39" duration="1119" />#012    <Gap start="2014-01-27T10:18:52" end="2014-01-27T10:18:53" duration="1" />#012    <Gap start="2014-01-27T10:18:59" end="2014-01-27T10:19:01" duration="1" />#012    <Gap start="2014-01-27T10:19:12" end="2014-01-27T10:19:13" duration="1" />#012    <Gap start="2014-01-27T10:19:47" end="2014-01-27T10:19:48" duration="1" />#012    <Gap start="2014-01-27T10:19:52" end="2014-01-27T10:19:53" duration="1" />#012    <Gap start="2014-01-27T10:19:53" end="2014-01-27T10:19:55" duration="1" />#012    <Gap start="2014-01-27T10:20:01" end="2014-01-27T10:20:03" duration="1" />#012    <Gap start="2014-01-27T10:20:11" end="2014-01-27T10:20:12" duration="1" />#012    <Gap start="2014-01-27T10:20:30" end="2014-01-27T10:20:32" duration="1" />#012    <Gap start="2014-01-27T10:20:36" end="2014-01-27T10:20:38" duration="2" />#012    <Gap start="2014-01-27T10:20:43" end="2014-01-27T10:20:44" duration="1" />#012    <Gap start="2014-01-27T10:20:45" end="2014-01-27T10:20:47" duration="1" />#012    <Gap start="2014-01-27T10:20:47" end="2014-01-27T10:20:48" duration="1" />#012    <Gap start="2014-01-27T10:20:50" end="2014-01-27T10:20:51" duration="1" />#012    <Gap start="2014-01-27T10:20:57" end="2014-01-27T10:20:59" duration="1" />#012    <Gap start="2014-01-27T10:21:05" end="2014-01-27T10:21:06" duration="1" />#012    <Gap start="2014-01-27T10:21:07" end="2014-01-27T10:21:08" duration="1" />#012    <Gap start="2014-01-27T10:21:09" end="2014-01-27T10:21:11" duration="2" />#012    <Gap start="2014-01-27T10:21:12" end="2014-01-27T10:21:14" duration="1" />#012    <Gap start="2014-01-27T10:21:30" end="2014-01-27T10:21:31" duration="1" />#012    <Gap start="2014-01-27T10:21:42" end
Jan 27 10:30:00 Myth mythbackend[2342]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for M*A*S*H on cardid 5 (Recording => Recorded)
Jan 27 10:30:00 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Jan 27 10:30:00 Myth mythbackend[2342]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Jan 27 10:30:00 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 48 items in 0.1 = 0.00 match + 0.06 place
Jan 27 10:30:00 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:00 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 0)
Jan 27 10:30:00 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:00 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 1)
Jan 27 10:30:24 Myth mythbackend[2342]: I Metadata_1659 jobqueue.cpp:2151 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for M*A*S*H recorded from channel 15608 at 2014-01-27T10:00:00
Jan 27 10:30:24 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:24 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 0)
Jan 27 10:30:24 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:24 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 1)
Jan 27 10:30:25 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:25 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 0)
Jan 27 10:30:25 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:25 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 1)
Jan 27 10:30:29 Myth mythbackend[2342]: I Commflag_1660 jobqueue.cpp:2276 (DoFlagCommercialsThread) JobQueue: Commercial Detection Starting for M*A*S*H recorded from channel 15608 at 2014-01-27T10:00:00
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 0)
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 1)
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 0)
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:29 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 1)
Jan 27 10:30:40 Myth mythbackend[2342]: E Commflag_1660 jobqueue.cpp:2362 (DoFlagCommercialsThread) JobQueue: Commercial Detection Errored: M*A*S*H recorded from channel 15608 at 2014-01-27T10:00:00 (Failed with exit status 140)
Jan 27 10:30:40 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:40 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 0)
Jan 27 10:30:40 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jan 27 10:30:40 Myth mythbackend[2342]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Myth as a client (events: 1)
Jan 27 10:30:42 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Jan 27 10:30:42 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 48 items in 0.1 = 0.04 match + 0.07 place
Jan 27 10:33:24 Myth mythbackend[2342]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jan 27 10:38:28 Myth mythbackend[2342]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jan 27 10:40:40 Myth mythbackend[2342]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jan 27 10:41:33 Myth mythbackend[2342]: E DVBRead dtvsignalmonitor.cpp:321 (HandlePAT) DTVSM(/dev/dvb/adapter0/frontend0): Program #4288 not found in PAT!#012Program Association Section#012 PSIP tableID(0x0) length(37) extension(0x40be)#012      version(8) current(1) section(0) last_section(0)#012      tsid(16574) programCount(7)#012  program number     0 has PID 0x0010#012  program number 17472 has PID 0x0064#012  program number 17598 has PID 0x19c8#012  program number 17662 has PID 0x00c8#012  program number 17664 has PID 0x012c#012  program number 17920 has PID 0x1b58#012  program number 18112 has PID 0x1bbc
Jan 27 10:41:45 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:42:49  mythbackend[2342]: last message repeated 9 times
...
Jan 27 10:43:35 Myth mythbackend[2342]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jan 27 10:43:39 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:43:40 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:43:42 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Jan 27 10:43:42 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 48 items in 0.1 = 0.04 match + 0.06 place
Jan 27 10:43:51 Myth mythbackend[2342]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jan 27 10:44:54  mythbackend[2342]: last message repeated 6 times
...
Jan 27 10:46:43 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Jan 27 10:46:43 Myth mythbackend[2342]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 48 items in 0.1 = 0.03 match + 0.06 place

```

mythcommflag.log (from a different incident, but same prob.)
```

Feb  2 00:56:16 Myth mythcommflag[30400]: E Decoder avformatdecoder.cpp:4216 (ProcessAudioPacket) AFD: Unknown audio decoding error
Feb  2 00:57:27  mythcommflag[30400]: last message repeated 53 times

```

Any help gratefully received.

---

### Post by alien878 on 2014-02-06
Re-seat the card?

Problems reading from the dvb device tend to be HW related.  From the logs, I see "DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected".

---

### Post by z7APXKm on 2014-02-14
Well, top marks to the support people at TBSDTV who replied straight away to my email.

They suggested the following thread as a possible solution:
[http://www.tbsdtv.com/forum/viewtopic.php?f=52&t=7631#p24903](http://www.tbsdtv.com/forum/viewtopic.php?f=52&t=7631#p24903)

No problems in the last few days, fingers crossed.

---

