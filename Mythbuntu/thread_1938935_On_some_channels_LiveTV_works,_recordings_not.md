---
title: "On some channels: LiveTV works, recordings not"
date: 2012-03-10
forum: Mythbuntu
---

### Post by TelepathicSpy on 2012-03-10
Hi all,

since yesterday I got a strange behaviour from my MythTV backend (Mythbuntu 10.04 with MythTV 0.24.2). On some channels I can watch LiveTV but I cannot record shows. I can even watch on these channels LiveTV and press R to record it without problems. But if I just plan a recordings the backend log first looks fine:

```

2012-03-10 20:46:18.281 Started recording: "Zwischen Handwerk und Hightech - Die Medizin der Zukunft":"SPIEGEL TV": channel 13060 on cardid 1, sourceid 1
2012-03-10 20:46:18.619 TVRec(2): ASK_RECORDING 2 0 0 0

```But if I want to watch this recording, the file cannot be found
```

2012-03-10 20:46:45.601 ProgramInfo(13060_20120310204600.mpg), Error: GetPlaybackURL: '13060_20120310204600.mpg' should be local, but it can not be found.
2012-03-10 20:46:45.756 ProgramInfo(13060_20120310204600.mpg), Error: GetPlaybackURL: '13060_20120310204600.mpg' should be local, but it can not be found.
2012-03-10 20:46:46.036 ProgramInfo(13060_20120310204600.mpg), Error: GetPlaybackURL: '13060_20120310204600.mpg' should be local, but it can not be found.

```What I did recently were two things:

1) to replace my harddisc for recordings/livetv as the old one got incredibly slow. So I first thought of an permission problem - but if there was any (for example that mythtv user dont have write access to the recoding folder) then I would have a problem for all channels
2) do a bunch of updates. This was a  big bunch, I updated it last time half a year ago. I made a backup if everything fails but I do not believe that my problem occurs from that.

So, if you have any suggestions or hints for me, I would be very happy. If you need more information, just tell me!

Best regards, Dirk

PS: What I tried so far (but nothing helped):

1) Check permissions for livetv and recordings folder - they were okay
2) deleted all tuners in setup and recreated them
3) do a full channel scan

---

### Post by nickrout on 2012-03-10
make sure the backend user (mythtv) can write to all the directories in the recordings storage group.

livetv is kept in a different storage group.

---

### Post by TelepathicSpy on 2012-03-11
Hello nicrout,

and thank your for your answer. Both folders have the same permissions for user mythtv ("Aufnahmen" is my recordings folder):
```

drwxrwxrwx  2 root       mythtv     20480 2012-03-11 11:15 Aufnahmen
drwxrwxrwx  2 multimedia mythtv      4096 2012-03-11 11:15 livetv

```And it would not explain why I have problems concerning recording some channels and others not, correct?

Thanks, Dirk

---

### Post by TelepathicSpy on 2012-03-13
Hi all,

I changed the log level of my backend to 'record' and here is a log. I try to record "Scrubs - Die Anfänger":

```

2012-03-13 10:39:36.024 mythbackend version: fixes/0.24 [v0.24.2-20-g0006ba7] www.mythtv.org
2012-03-13 10:39:36.068 Using runtime prefix = /usr
2012-03-13 10:39:36.086 Using configuration directory = /home/mythtv/.mythtv
2012-03-13 10:39:36.126 Empty LocalHostName.
2012-03-13 10:39:36.147 Using localhost value of Kakadu
2012-03-13 10:39:36.352 New DB connection, total: 1
2012-03-13 10:39:36.500 Connected to database 'mythconverg' at host: Kakadu
2012-03-13 10:39:36.543 Closing DB connection named 'DBManager0'
2012-03-13 10:39:36.556 Connected to database 'mythconverg' at host: Kakadu
2012-03-13 10:39:36.638 Current locale DE_DE
2012-03-13 10:39:36.671 Reading locale defaults from /usr/share/mythtv//locales/de_de.xml
2012-03-13 10:39:37.001 Current MythTV Schema Version (DBSchemaVer): 1264
2012-03-13 10:39:37.070 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2012-03-13 10:39:37.226 Enabling Upnpmedia rebuild thread.
2012-03-13 10:39:38.463 MythBackend: Starting up as the master server.
2012-03-13 10:39:38.533 New DB connection, total: 2
2012-03-13 10:39:38.544 Connected to database 'mythconverg' at host: Kakadu
2012-03-13 10:39:38.698 DVBChan(1:/dev/dvb/adapter0/frontend0): Using DVB card /dev/dvb/adapter0/frontend0, with frontend 'STV090x Multistandard'.
2012-03-13 10:39:38.750 New DB connection, total: 3
2012-03-13 10:39:38.760 Connected to database 'mythconverg' at host: Kakadu
2012-03-13 10:39:38.786 New DB connection, total: 4
2012-03-13 10:39:38.802 Connected to database 'mythconverg' at host: Kakadu
2012-03-13 10:39:40.101 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Unsupported fec_inner parameter.
2012-03-13 10:39:40.342 TVRec(1): SetFlags(RunMainLoop,) -> RunMainLoop,
2012-03-13 10:39:40.356 TVRec(1): ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2012-03-13 10:39:40.424 DVBChan(2:/dev/dvb/adapter0/frontend0) Warning: Your frequency setting (11361750) is out of range. (min/max:950000/2150000)
2012-03-13 10:39:40.431 DVBChan(2:/dev/dvb/adapter0/frontend0) Warning: Unsupported fec_inner parameter.
2012-03-13 10:39:40.441 TVRec(2): SetFlags(RunMainLoop,) -> RunMainLoop,
2012-03-13 10:39:40.448 TVRec(2): ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2012-03-13 10:39:40.648 DVBChan(3:/dev/dvb/adapter1/frontend0): Using DVB card /dev/dvb/adapter1/frontend0, with frontend 'STB0899 Multistandard'.
2012-03-13 10:39:41.811 DVBChan(3:/dev/dvb/adapter1/frontend0) Warning: Unsupported fec_inner parameter.
2012-03-13 10:39:42.090 TVRec(3): SetFlags(RunMainLoop,) -> RunMainLoop,
2012-03-13 10:39:42.095 TVRec(3): ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2012-03-13 10:39:42.144 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Your frequency setting (12187500) is out of range. (min/max:950000/2150000)
2012-03-13 10:39:42.153 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Unsupported fec_inner parameter.
2012-03-13 10:39:42.621 TVRec(4): SetFlags(RunMainLoop,) -> RunMainLoop,
2012-03-13 10:39:42.627 TVRec(4): ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2012-03-13 10:39:42.696 New DB scheduler connection
2012-03-13 10:39:42.712 Connected to database 'mythconverg' at host: Kakadu
2012-03-13 10:39:42.734 Main::Registering HttpStatus Extension
2012-03-13 10:39:42.744 Enabled verbose msgs:  important general record
2012-03-13 10:39:42.835 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2012-03-13 10:39:43.062 MainServer::ANN Monitor
2012-03-13 10:39:43.077 adding: Kakadu as a client (events: 0)
2012-03-13 10:39:43.086 MainServer::ANN Monitor
2012-03-13 10:39:43.093 adding: Kakadu as a client (events: 1)
2012-03-13 10:39:45.806 Reschedule requested for id -1.
2012-03-13 10:39:47.275 UPnpMedia: BuildMediaMap VIDEO scan starting in :/WD15/DVDs:
2012-03-13 10:39:47.289 UPnpMedia: BuildMediaMap Done. Found 0 objects
2012-03-13 10:39:47.974 Scheduled 69 items in 2.1 = 1.28 match + 0.85 place
2012-03-13 10:39:47.992 Seem to be woken up by USER
2012-03-13 10:39:48.996 I'm idle now... shutdown will occur in 120 seconds.
2012-03-13 10:40:11.598 MainServer::ANN Playback
2012-03-13 10:40:11.612 adding: wombat as a client (events: 0)
2012-03-13 10:40:11.622 MainServer::ANN Monitor
2012-03-13 10:40:11.629 adding: wombat as a client (events: 1)
2012-03-13 10:41:02.762 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2012-03-13 10:41:08.733 Reschedule requested for id 829.
2012-03-13 10:41:09.146 Scheduled 70 items in 0.4 = 0.02 match + 0.38 place
2012-03-13 10:41:09.157 CardUtil:   Group ID 1
2012-03-13 10:41:09.165 CardUtil:   Card ID 2
2012-03-13 10:41:09.184 TVRec(1): RecordPending on inputid 1
2012-03-13 10:41:09.198 CardUtil:   Group ID 1
2012-03-13 10:41:09.207 CardUtil:   Card ID 2
2012-03-13 10:41:09.214 TVRec(2): RecordPending on inputid 1
2012-03-13 10:41:09.223 TVRec(1): StartRecording("Scrubs - Die Anf\Uffffffffer")
2012-03-13 10:41:09.239 TVRec(1): Checking input group recorders - begin
2012-03-13 10:41:09.247 TVRec(1): Checking input group recorders - done
2012-03-13 10:41:09.336 TVRec(1): StartedRecording(0xb365ef50) fn(/WD15/Aufnahmen/18501_20120313104100.mpg)
2012-03-13 10:41:09.347 TVRec(1): ClearFlags(CancelNextRecording,) -> RunMainLoop,
2012-03-13 10:41:09.356 TVRec(1): Changing from None to RecordingOnly
2012-03-13 10:41:09.364 TVRec(1): ClearFlags(FrontendReady,CancelNextRecording,) -> RunMainLoop,
2012-03-13 10:41:09.372 TVRec(1): HandleTuning Request: Program(yes) channel() input() flags(Recording,)
2012-03-13 10:41:09.383 TVRec(1): HW Tuner: 1->1
2012-03-13 10:41:09.389 TVRec(1): ClearFlags(PENDINGACTIONS,) -> RunMainLoop,
2012-03-13 10:41:09.397 TVRec(1): No recorder yet, calling TuningFrequency
2012-03-13 10:41:09.407 TVRec(1): Starting Signal Monitor
2012-03-13 10:41:09.414 TVRec(1): SetupSignalMonitor(1, 0)
2012-03-13 10:41:09.417 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Unsupported fec_inner parameter.
2012-03-13 10:41:09.465 TVRec(2): ASK_RECORDING 2 0 0 0
2012-03-13 10:41:09.735 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Cannot count Uncorrected Blocks
            eno: Die Operation wird nicht unterstützt (95)
2012-03-13 10:41:09.738 TVRec(1): Signal monitor successfully created
2012-03-13 10:41:09.747 TVRec(1): Setting up table monitoring.
2012-03-13 10:41:09.747 TVRec(1): SetFlags(SignalMonitorRunning,) -> RunMainLoop,SignalMonitorRunning,
2012-03-13 10:41:09.773 TVRec(1): ClearFlags(WaitingForSignal,) -> RunMainLoop,SignalMonitorRunning,
2012-03-13 10:41:09.788 TVRec(1): SetFlags(WaitingForSignal,) -> RunMainLoop,WaitingForSignal,SignalMonitorRunning,
2012-03-13 10:41:09.813 TVRec(1): ClearFlags(NeedToStartRecorder,) -> RunMainLoop,WaitingForSignal,SignalMonitorRunning,
2012-03-13 10:41:09.844 TVRec(1): SetFlags(NeedToStartRecorder,) -> RunMainLoop,WaitingForSignal,NeedToStartRecorder,SignalMonitorRunning,
2012-03-13 10:41:09.886 Using profile 'Live TV' to record
2012-03-13 10:41:09.907 TVRec(1): DVB service_id 17501 on net_id 1 tsid 1107
2012-03-13 10:41:09.921 TVRec(1): Successfully set up DVB table monitoring.
2012-03-13 10:41:09.938 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2012-03-13 10:41:09.974 Started recording: "Scrubs - Die Anf\Uffffffffer": channel 18501 on cardid 1, sourceid 1
2012-03-13 10:41:39.485 TVRec(2): Deleting stale pending recording 1 'Scrubs - Die Anf\Uffffffffer'

```

What I think is quite strange is this line here:

```

2012-03-13 10:41:09.886 Using profile 'Live TV' to record

```

because I didn't choose LiveTV. If anybody has a hint or suggestion, please let me know.

Regards, Dirk

---

### Post by TelepathicSpy on 2012-03-13
Hi all,

I think I solved it (I'm just a bit cautious). I found out that this problem only occurs with one of my two TV cards. and then came to my mind again that I made this whole bunch of updates some days ago and I think the linux kernel was updated, too. Normally my two TV cards (Technotrend S2-1600 and S2-3200) are working out-of-the-box with the Ubuntu kernel but I compiled an adjusted version of V4L to support the remote control of the S2-3200.

So I just recompiled and reinstalled this V4L version again and it works! I cannot explain why this problem occurred (perhaps something in the kernel changed with my TV card or the V4L driver in it) but I can live with the solution :D

Thanks everybody!

Dirk

---

### Post by nickrout on 2012-03-13
> **TelepathicSpy said:**
> Hi all,

I think I solved it (I'm just a bit cautious). I found out that this problem only occurs with one of my two TV cards. and then came to my mind again that I made this whole bunch of updates some days ago and I think the linux kernel was updated, too. Normally my two TV cards (Technotrend S2-1600 and S2-3200) are working out-of-the-box with the Ubuntu kernel but I compiled an adjusted version of V4L to support the remote control of the S2-3200.

So I just recompiled and reinstalled this V4L version again and it works! I cannot explain why this problem occurred (perhaps something in the kernel changed with my TV card or the V4L driver in it) but I can live with the solution :D

Thanks everybody!

Dirk

Well if you update your kernel you always have to recompile any drivers you use that are not part of the kernel package.

---

### Post by TelepathicSpy on 2012-03-16
This is correct, but v4l is part of the kernel and my version ist just an adjusted for the remote control. So I would expect the kernel version to work out-of-the-box with my TV cards concerning recordings, as they did before. But, anyway, my problem is solved and I can live with it.

---

