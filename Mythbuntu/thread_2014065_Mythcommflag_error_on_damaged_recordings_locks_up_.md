---
title: "Mythcommflag error on damaged recordings locks up frontend"
date: 2012-07-01
forum: Mythbuntu
---

### Post by crbnrod on 2012-07-01
Not sure if anyone else is seeing this, but having an issue with the commercial flagging in .25/12.04 that is somehow locking up the FE on the same machine.
It's a combined BE/FE attached to an OTA antenna (I'm in the US), and it's somewhat common for me in the summer months to get a damaged recording due to increased tropospheric ducting. /science
Anyway, here's what I've gotten 3 times whenever mythcommflag runs on a recording that's flagged as damaged:

Backend log:
```

Jun 29 17:59:00 myth-lr mythbackend[1562]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(12): ASK_RECORDING 12 28 0 0
Jun 29 17:59:30 myth-lr mythbackend[1562]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 10
Jun 29 17:59:30 myth-lr mythbackend[1562]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(12): Changing from None to RecordingOnly
Jun 29 17:59:30 myth-lr mythbackend[1562]: I TVRecEvent mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 10
Jun 29 17:59:30 myth-lr mythbackend[1562]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(12): HW Tuner: 12->12
Jun 29 18:00:52 myth-lr mythbackend[1562]: I TVRecEvent tv_rec.cpp:3989 (TuningNewRecorder) TVRec(12): rec->GetPathname(): '/media/datalr/var/lib/mythtv/recordings/4581_20120629180000.mpg'
Jun 29 18:02:28 myth-lr mythbackend[1562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 29 18:04:32 myth-lr mythbackend[1562]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jun 29 18:06:00  mythbackend[1562]: last message repeated 2 times
Jun 29 18:07:28 myth-lr mythbackend[1562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 29 18:09:45 myth-lr mythbackend[1562]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jun 29 18:10:52  mythbackend[1562]: last message repeated 2 times
Jun 29 18:10:59 myth-lr mythbackend[1562]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jun 29 18:12:09 myth-lr mythbackend[1562]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jun 29 18:12:34  mythbackend[1562]: last message repeated 2 times
Jun 29 18:12:34 myth-lr mythbackend[1562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 29 18:17:40 myth-lr mythbackend[1562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 29 18:22:47 myth-lr mythbackend[1562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 29 18:26:41 myth-lr mythbackend[1562]: E DVBRead mpeg/mpegstreamdata.cpp:362 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Jun 29 18:27:47  mythbackend[1562]: last message repeated 2 times
Jun 29 18:27:47 myth-lr mythbackend[1562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 29 18:30:30 myth-lr mythbackend[1562]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(12): Changing from RecordingOnly to None
Jun 29 18:30:30 myth-lr mythbackend[1562]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
Jun 29 18:30:30 myth-lr mythbackend[1562]: I TVRecEvent tv_rec.cpp:816 (FinishedRecording) TVRec(12): FinishedRecording(4581_2012-06-29T18:00:00) damaged recq:<RecordingQuality overall_score="0.5" key="4581_2012-06-29T18:00:00" countinuity_error_count="151207" packet_count="8789512">#012    <Gap start="2012-06-29T18:00:00" end="2012-06-29T18:00:52" duration="52" />#012    <Gap start="2012-06-29T18:00:55" end="2012-06-29T18:00:58" duration="3" />#012    <Gap start="2012-06-29T18:01:12" end="2012-06-29T18:01:22" duration="9" />#012    <Gap start="2012-06-29T18:01:23" end="2012-06-29T18:01:27" duration="4" />#012    <Gap start="2012-06-29T18:01:28" end="2012-06-29T18:01:40" duration="12" />#012    <Gap start="2012-06-29T18:01:43" end="2012-06-29T18:01:54" duration="11" />#012    <Gap start="2012-06-29T18:01:56" end="2012-06-29T18:02:23" duration="26" />#012    <Gap start="2012-06-29T18:02:32" end="2012-06-29T18:02:33" duration="1" />#012    <Gap start="2012-06-29T18:02:37" end="2012-06-29T18:02:50" duration="13" />#012    <Gap start="2012-06-29T18:02:53" end="2012-06-29T18:02:56" duration="2" />#012    <Gap start="2012-06-29T18:02:57" end="2012-06-29T18:03:01" duration="4" />#012    <Gap start="2012-06-29T18:03:05" end="2012-06-29T18:03:09" duration="4" />#012    <Gap start="2012-06-29T18:03:09" end="2012-06-29T18:03:11" duration="1" />#012    <Gap start="2012-06-29T18:03:11" end="2012-06-29T18:03:20" duration="9" />#012    <Gap start="2012-06-29T18:03:25" end="2012-06-29T18:03:28" duration="3" />#012    <Gap start="2012-06-29T18:03:29" end="2012-06-29T18:03:38" duration="9" />#012    <Gap start="2012-06-29T18:03:38" end="2012-06-29T18:03:48" duration="9" />#012    <Gap start="2012-06-29T18:03:49" end="2012-06-29T18:03:57" duration="8" />#012    <Gap start="2012-06-29T18:03:57" end="2012-06-29T18:04:00" duration="2" />#012    <Gap start="2012-06-29T18:04:00" end="2012-06-29T18:04:03" duration="2" />#012    <Gap start="2012-06-29T18:04:03" end="2012-06-29T18:04:04" duration="1" />#012    <Gap start="2012-06-29T18:04:
Jun 29 18:30:30 myth-lr mythbackend[1562]: I PreviewGeneratorQueue mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 9
Jun 29 18:31:26 myth-lr mythbackend[1562]: I Commflag_2624 jobqueue.cpp:2276 (DoFlagCommercialsThread) JobQueue: Commercial Detection Starting for Jeopardy! recorded from channel 4581 at 2012-06-29T18:00:00
Jun 29 18:31:37 myth-lr mythbackend[1562]: E Commflag_2624 jobqueue.cpp:2362 (DoFlagCommercialsThread) JobQueue: Commercial Detection Errored: Jeopardy! recorded from channel 4581 at 2012-06-29T18:00:00 (Failed with exit status 140)

```

Mythcommflag log:
```

Jun 29 18:31:26 myth-lr mythcommflag[8232]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythcommflag version: fixes/0.25 [v0.25.1-45-g25dd4ce] www.mythtv.org
Jun 29 18:31:26 myth-lr mythcommflag[8232]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of myth-lr
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.0.2'
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
Jun 29 18:31:26 myth-lr mythcommflag[8232]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
Jun 29 18:31:26 myth-lr mythcommflag[8232]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jun 29 18:31:27 myth-lr mythcommflag[8232]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x22e5dc0, id(MPEG2VIDEO) type(Video)
Jun 29 18:31:27 myth-lr mythcommflag[8232]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec E-AC3 has 2 channels
Jun 29 18:31:27 myth-lr mythcommflag[8232]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x22ebdf0, id(E-AC3) type(Audio)
Jun 29 18:31:27 myth-lr mythcommflag[8232]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AC3 has 2 channels
Jun 29 18:31:27 myth-lr mythcommflag[8232]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x24031a0, id(AC3) type(Audio)
Jun 29 18:31:29 myth-lr mythcommflag[8232]: I CoreContext ClassicCommDetector.cpp:359 (go) Finding Logo
Jun 29 18:31:29 myth-lr mythcommflag[8232]: E Decoder avformatdecoder.cpp:4216 (ProcessAudioPacket) AFD: Unknown audio decoding error
Jun 29 18:31:29  mythcommflag[8232]: last message repeated 6 times
Jun 29 18:31:29 myth-lr mythcommflag[8232]: E Decoder avformatdecoder.cpp:3076 (ProcessVideoPacket) AFD: Unknown decoding error
Jun 29 18:31:29 myth-lr mythcommflag[8232]: E Decoder avformatdecoder.cpp:4216 (ProcessAudioPacket) AFD: Unknown audio decoding error
Jun 29 18:31:29  mythcommflag[8232]: last message repeated 6 times
Jun 29 18:31:29 myth-lr mythcommflag[8232]: E Decoder avformatdecoder.cpp:3076 (ProcessVideoPacket) AFD: Unknown decoding error
Jun 29 18:31:29 myth-lr mythcommflag[8232]: E Decoder avformatdecoder.cpp:4216 (ProcessAudioPacket) AFD: Unknown audio decoding error
Jun 29 18:32:31  mythcommflag[8232]: last message repeated 4 times

```

When this happens, the backend seems to continue running fine, because I have recordings from the same tuner that ocurred after the above error, and they work fine. However, the system gives me that report/ignore/relaunch popup asking me if I want to report the error, and then the FE on the same machine becomes unresponsive. I can kill it and then it will restart automagically, but I generally only have a remote control hooked up to this machine. There's not much in the FE log other than the weather grabber running as expected, but here's any lines I see not related to the weather:
```

Jun 29 20:06:40 myth-lr mythfrontend[1790]: E TaskQueue mmulticastsocketdevice.cpp:62 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:51): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 30 07:17:22 myth-lr mythfrontend[1790]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
Jul  1 08:40:38 myth-lr mythfrontend[1790]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
Jul  1 08:40:38 myth-lr mythfrontend[1790]: I DBLogger mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
Jul  1 12:55:40 myth-lr mythfrontend[12722]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25.1-45-g25dd4ce] www.mythtv.org
Jul  1 12:55:40 myth-lr mythfrontend[12722]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jul  1 12:55:40 myth-lr mythfrontend[12722]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
```
12:55 today is when I killed it and restarted.

Not sure where to go from here - googling indicates people have occasionally had similar problems with the same exit code, but I didn't see anything that solved it (duh, otherwise I wouldn't start the thread, haha). One idea would be to tell the commflag job to simply not try to flag recordings marked as damaged, but that's way beyond my level of know-how unless I've overlooked some easy setting in the BE setup.

Thanks for any help!

---

### Post by crbnrod on 2012-07-01
Found this:
[http://code.mythtv.org/trac/ticket/10222](http://code.mythtv.org/trac/ticket/10222)

I think the FE appears locked up because the bug reporting window popups were stealing focus from the FE and then the remote keypress can't interact with the popup, so there was nothing to turn off the screen saver(?). A possible workaround appears to be continuously telling it to ignore future errors of this type, which I think stops it from giving that popup window. It appears now I can requeue the job and let it crash to my heart's content without getting any "report this error?" popup window.

Still not sure if there's a "cleaner" way to deal with this problem, though.

---

### Post by crbnrod on 2012-07-07
Turns out it was a problem with the openGL painter, referenced in this post (and following) from the mailing list.

[http://www.mythtv.org/pipermail/mythtv-users/2012-June/335211.html](http://www.mythtv.org/pipermail/mythtv-users/2012-June/335211.html)

For now I set the painter to Qt on the frontend and everything seems to be working fine. Not sure if there's any disadvantage to using Qt instead of opengl, though.

---

### Post by crbnrod on 2012-07-08
Well, I take back the part about switching the painter to QT fixing the problem.

Seems like this occurs when the FE is idle for an extended period of time, like overnight or something - yesterday it went into idle mode several times, screensaver activated, etc., and I was able to wake it up with the remote without a problem. This morning, I just got a black screen. The logs indicate the FE is still running, but no way to really interact with it.

FWIW I am using NVIDIA GT430 on .25/12.04. this same hardware setup did not have this problem on prior build which I think was .23/10.04.

Not sure where I would look anymore (other logs or something?) to identify this problem...anyone have any ideas?

---

