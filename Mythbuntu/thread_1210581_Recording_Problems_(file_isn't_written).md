---
title: "Recording Problems (file isn't written)"
date: 2009-07-11
forum: Mythbuntu
---

### Post by JPurdy on 2009-07-11
I'm having a problem with recording programs, either scheduled or watching LiveTV. It started happening a few days ago after I did an update to try & fix a separate problem (volume). Basically, recordings happen and show up in my 'Watch Recordings' list, but when I try to select them, I get 'The flie for this recording can not be found'. Looking in the backend log, I see this:

```
2009-07-11 16:26:19.599 ProgramInfo, Error: GetPlaybackURL: '1041_20090711161400.mpg' should be local, but it can not be found.
```

In the frontend log, I see this:

```
2009-07-11 16:27:24.600 Error: File 'myth://127.0.0.1:6543/1041_20090711161400.mpg' missing.
```

I logged onto the box and there is no matching video file in my /video directory. I did a [FONT="Courier New"]/etc/init.d/mythtv-backend stop[/FONT] and then su'd into mythtv and did a [FONT="Courier New"]/usr/bin/mythbackend -v important,general,file,record[/FONT] to look at the output when it tries to record and this is what I see:

```
$ /usr/bin/mythbackend -v important,general,file,record
2009-07-11 16:13:39.313 Using runtime prefix = /usr
2009-07-11 16:13:39.314 Empty LocalHostName.
2009-07-11 16:13:39.314 Using localhost value of purdymyth
2009-07-11 16:13:39.327 New DB connection, total: 1
2009-07-11 16:13:39.333 Connected to database 'mythconverg' at host: localhost
2009-07-11 16:13:39.334 Closing DB connection named 'DBManager0'
2009-07-11 16:13:39.335 Connected to database 'mythconverg' at host: localhost
2009-07-11 16:13:39.337 New DB connection, total: 2
2009-07-11 16:13:39.338 Connected to database 'mythconverg' at host: localhost
2009-07-11 16:13:39.340 Current Schema Version: 1214
Starting up as the master server.
2009-07-11 16:13:39.349 New DB connection, total: 3
2009-07-11 16:13:39.350 Connected to database 'mythconverg' at host: localhost
2009-07-11 16:13:39.354 DVBChan(21:0): Using DVB card 0, with frontend 'Nextwave NXT200X VSB/QAM frontend'.
2009-07-11 16:13:40.301 TVRec(21): SetFlags(RunMainLoop,) -> RunMainLoop,
2009-07-11 16:13:40.301 TVRec(21): ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2009-07-11 16:13:40.305 New DB scheduler connection
2009-07-11 16:13:40.306 Connected to database 'mythconverg' at host: localhost
2009-07-11 16:13:40.316 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-07-11 16:13:40.316 Main::Registering HttpStatus Extension
2009-07-11 16:13:40.317 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-11 16:13:40.317 Enabled verbose msgs: important general file record
2009-07-11 16:13:40.317 AutoExpire: CalcParams()
2009-07-11 16:13:40.317 Maximal bitrate of busy encoders is 0 KB/min
--- GetFilesystemInfos directory list start ---
Dir: purdymyth:/video
     Location: Local
     fsID    : 1
     dirID   : 5
     TotalKB : 464814080
     UsedKB  : 415452456
     FreeKB  : 49361624

--- GetFilesystemInfos directory list end ---
2009-07-11 16:13:40.318 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-07-11 16:13:40.320 SG(): CheckAllStorageGroupDirs(): Checking All Storage Group directories
2009-07-11 16:13:40.321 SG(Default): Checking directory '/video/' in group 'Default'.
2009-07-11 16:13:43.309 Reschedule requested for id -1.
2009-07-11 16:13:43.672 MainServer::HandleAnnounce Monitor
2009-07-11 16:13:43.673 adding: purdymyth as a client (events: 0)
2009-07-11 16:13:43.673 MainServer::HandleAnnounce Monitor
2009-07-11 16:13:43.673 adding: purdymyth as a client (events: 1)
2009-07-11 16:13:43.702 Scheduled 121 items in 0.4 = 0.15 match + 0.24 place
2009-07-11 16:13:43.704 Seem to be woken up by USER
2009-07-11 16:13:43.760 MainServer::HandleAnnounce Playback
2009-07-11 16:13:43.762 adding: purdymyth as a client (events: 0)
2009-07-11 16:13:43.763 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:13:43.764 adding: purdymyth as a remote file transfer
2009-07-11 16:13:43.765 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:13:43.766 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:13:43.766 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:13:50.132 MainServer::HandleAnnounce Playback
2009-07-11 16:13:50.132 adding: purdymyth as a client (events: 0)
2009-07-11 16:13:50.132 MainServer::HandleAnnounce Playback
2009-07-11 16:13:50.132 adding: purdymyth as a client (events: 0)
2009-07-11 16:13:50.133 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:13:50.133 adding: purdymyth as a remote file transfer
2009-07-11 16:13:50.134 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:13:50.134 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:13:50.135 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:13:50.138 MythSocket(22866f0:-1): writeStringList: Error, socket went unconnected.
2009-07-11 16:14:00.309 AutoExpire: ExpireLiveTV(10000)
2009-07-11 16:14:00.309 AutoExpire: FillDBOrdered: Adding Short LiveTV programs in starttime order
2009-07-11 16:14:00.311 AutoExpire: SendDeleteMessages. Nothing to expire.
2009-07-11 16:14:00.868 MainServer::HandleAnnounce Playback
2009-07-11 16:14:00.868 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:00.869 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:00.869 adding: purdymyth as a remote file transfer
2009-07-11 16:14:00.870 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:00.870 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:00.870 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:08.465 MainServer::HandleAnnounce Playback
2009-07-11 16:14:08.466 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:08.467 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:08.467 adding: purdymyth as a remote file transfer
2009-07-11 16:14:08.467 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:08.468 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:08.468 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:10.000 Reschedule requested for id 0.
2009-07-11 16:14:10.090 MainServer::HandleAnnounce Playback
2009-07-11 16:14:10.090 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:10.091 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:10.091 adding: purdymyth as a remote file transfer
2009-07-11 16:14:10.095 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.095 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.095 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:10.195 MainServer::HandleAnnounce Playback
2009-07-11 16:14:10.196 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:10.197 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:10.197 adding: purdymyth as a remote file transfer
2009-07-11 16:14:10.198 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.198 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.198 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:10.243 Scheduled 121 items in 0.2 = 0.00 match + 0.24 place
2009-07-11 16:14:10.245 TVRec(21): RecordPending on inputid 2
2009-07-11 16:14:10.247 TVRec(21): StartRecording(Woodwright's Shop)
2009-07-11 16:14:10.247 TVRec(21): ASK_RECORDING 21 0 0 0
2009-07-11 16:14:10.302 ProgramInfo: StartedRecording: Recording to '/video/1041_20090711161400.mpg'
2009-07-11 16:14:10.309 TVRec(21): StartedRecording(0x7f06440219d0) fn(/video/1041_20090711161400.mpg)
2009-07-11 16:14:10.310 TVRec(21): ClearFlags(CancelNextRecording,) -> RunMainLoop,
2009-07-11 16:14:10.311 TVRec(21): Changing from None to RecordingOnly
2009-07-11 16:14:10.311 TVRec(21): ClearFlags(FrontendReady,CancelNextRecording,) -> RunMainLoop,
2009-07-11 16:14:10.311 TVRec(21): Request: Program(yes) channel() input() flags(Recording,)
2009-07-11 16:14:10.313 MainServer::HandleAnnounce Playback
2009-07-11 16:14:10.313 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:10.314 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:10.314 adding: purdymyth as a remote file transfer
2009-07-11 16:14:10.314 TVRec(21): HW Tuner: 21->21
2009-07-11 16:14:10.315 TVRec(21): ClearFlags(PENDINGACTIONS,) -> RunMainLoop,
2009-07-11 16:14:10.315 TVRec(21): No recorder yet, calling TuningFrequency
2009-07-11 16:14:10.318 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.319 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.319 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:10.327 TVRec(21): Starting Signal Monitor
2009-07-11 16:14:10.327 TVRec(21): SetupSignalMonitor(1, 0)
2009-07-11 16:14:10.530 TVRec(21): Signal monitor successfully created
2009-07-11 16:14:10.530 TVRec(21): Setting up table monitoring.
2009-07-11 16:14:10.534 Using profile 'Live TV' to record
2009-07-11 16:14:10.534 TVRec(21): ATSC channel: 4_1
2009-07-11 16:14:10.535 TVRec(21): Successfully set up ATSC table monitoring.
2009-07-11 16:14:10.536 TVRec(21): SetFlags(SignalMonitorRunning,) -> RunMainLoop,SignalMonitorRunning,
2009-07-11 16:14:10.536 TVRec(21): ClearFlags(WaitingForSignal,) -> RunMainLoop,SignalMonitorRunning,
2009-07-11 16:14:10.537 TVRec(21): SetFlags(WaitingForSignal,) -> RunMainLoop,WaitingForSignal,SignalMonitorRunning,
2009-07-11 16:14:10.537 TVRec(21): ClearFlags(NeedToStartRecorder,) -> RunMainLoop,WaitingForSignal,SignalMonitorRunning,
2009-07-11 16:14:10.537 TVRec(21): SetFlags(NeedToStartRecorder,) -> RunMainLoop,WaitingForSignal,NeedToStartRecorder,SignalMonitorRunning,
2009-07-11 16:14:10.538 AutoExpire: Cardid 21: is starting a recording on an unknown fsID soon.
2009-07-11 16:14:10.539 AutoExpire: CalcParams()
2009-07-11 16:14:10.540 Cardid 21: max bitrate 142089 KB/min
2009-07-11 16:14:10.540 Maximal bitrate of busy encoders is 142089 KB/min
--- GetFilesystemInfos directory list start ---
Dir: purdymyth:/video
     Location: Local
     fsID    : 1
     dirID   : 5
     TotalKB : 464814080
     UsedKB  : 415452456
     FreeKB  : 49361624

--- GetFilesystemInfos directory list end ---
2009-07-11 16:14:10.541 fsID #1: Total:   443.3 GB   Used:   396.2 GB   Free:    47.1 GB
2009-07-11 16:14:10.542     Cardid 21: max bitrate 18945 Kb/sec, fsID 1 max is now 142089 KB/min
2009-07-11 16:14:10.542   Max of 142089 KB/min for fsID 1 is higher than the existing Max of 0 so we'll use this Max instead
2009-07-11 16:14:10.542 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-07-11 16:14:10.544 Started recording: Woodwright's Shop "Screw Box for Wooden Threads": channel 1041 on cardid 21, sourceid 1
2009-07-11 16:14:10.625 MainServer::HandleAnnounce Playback
2009-07-11 16:14:10.625 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:10.626 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:10.626 adding: purdymyth as a remote file transfer
2009-07-11 16:14:10.628 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.628 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:10.628 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:10.741 DVBSH(0): AddListener(0x22c6d88) -- begin
2009-07-11 16:14:10.741 DVBSH(0): AddListener(0x22c6d88) -- locked
2009-07-11 16:14:10.742 DVBSH(0): AddListener(0x22c6d88) -- end
2009-07-11 16:14:10.742 DVBSH(0): AddPIDFilter(0x0) priority 2
2009-07-11 16:14:10.742 PIDInfo(0): Opening filter for pid 0x0
2009-07-11 16:14:10.743 DVBSH(0): RemovePIDFilter(0x0)
2009-07-11 16:14:10.743 PIDInfo(0): Closing filter for pid 0x0
2009-07-11 16:14:11.262 DVBSH(0): RunTS(): begin
2009-07-11 16:14:11.262 DVBSH(0): AddPIDFilter(0x0) priority 2
2009-07-11 16:14:11.262 PIDInfo(0): Opening filter for pid 0x0
2009-07-11 16:14:11.262 DVBSH(0): AddPIDFilter(0x1ffb) priority 2
2009-07-11 16:14:11.262 PIDInfo(0): Opening filter for pid 0x1ffb

```
And then this is what happened when I stopped the recording manually a few seconds later.
```

2009-07-11 16:14:22.854 MainServer::HandleAnnounce Playback
2009-07-11 16:14:22.854 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:22.855 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:22.855 adding: purdymyth as a remote file transfer
2009-07-11 16:14:22.856 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:22.856 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:22.856 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:24.607 TVRec(21): Changing from RecordingOnly to None
2009-07-11 16:14:24.607 TVRec(21): ClearFlags(FrontendReady,CancelNextRecording,) -> RunMainLoop,WaitingForSignal,NeedToStartRecorder,SignalMonitorRunning,
2009-07-11 16:14:24.607 TVRec(21): Request: Program(no) channel() input() flags(CloseRec,KillRingBuffer,)
2009-07-11 16:14:24.607 TVRec(21): TeardownSignalMonitor() -- begin
2009-07-11 16:14:24.624 DVBSH(0): RemoveListener(0x22c6d88) -- begin
2009-07-11 16:14:24.624 DVBSH(0): RemoveListener(0x22c6d88) -- locked
2009-07-11 16:14:24.639 DVBSH(0): RunTS(): shutdown
2009-07-11 16:14:24.639 DVBSH(0): RemovePIDFilter(0x0)
2009-07-11 16:14:24.639 PIDInfo(0): Closing filter for pid 0x0
2009-07-11 16:14:24.639 DVBSH(0): RemovePIDFilter(0x1ffb)
2009-07-11 16:14:24.639 PIDInfo(0): Closing filter for pid 0x1ffb
2009-07-11 16:14:25.142 DVBSH(0): RunTS(): end
2009-07-11 16:14:25.143 DVBSH(0): RemoveListener(0x22c6d88) -- end
2009-07-11 16:14:25.143 TVRec(21): TeardownSignalMonitor() -- end
2009-07-11 16:14:25.143 TVRec(21): ClearFlags(SignalMonitorRunning,) -> RunMainLoop,WaitingForSignal,NeedToStartRecorder,
2009-07-11 16:14:25.143 TVRec(21): ClearFlags(WaitingForSignal,) -> RunMainLoop,NeedToStartRecorder,
2009-07-11 16:14:25.145 TVRec(21): FinishedRecording(Woodwright's Shop) in recgroup: Default
2009-07-11 16:14:25.147 Finished recording Woodwright's Shop "Screw Box for Wooden Threads": channel 1041
2009-07-11 16:14:25.147 TVRec(21): ClearFlags(PENDINGACTIONS,) -> RunMainLoop,
2009-07-11 16:14:25.147 TVRec(21): ClearFlags(CancelNextRecording,) -> RunMainLoop,
2009-07-11 16:14:25.149 Reschedule requested for id 0.
2009-07-11 16:14:25.236 MainServer::HandleAnnounce Playback
2009-07-11 16:14:25.237 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:25.238 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:25.238 adding: purdymyth as a remote file transfer
2009-07-11 16:14:25.240 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.240 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.240 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:25.341 MainServer::HandleAnnounce Playback
2009-07-11 16:14:25.341 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:25.342 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:25.342 adding: purdymyth as a remote file transfer
2009-07-11 16:14:25.343 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.343 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.343 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:25.398 Scheduled 121 items in 0.2 = 0.00 match + 0.24 place
2009-07-11 16:14:25.489 MainServer::HandleAnnounce Playback
2009-07-11 16:14:25.489 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:25.490 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:25.490 adding: purdymyth as a remote file transfer
2009-07-11 16:14:25.493 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.493 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.493 RingBuffer::RingBuffer(): Failed to open remote file ()
2009-07-11 16:14:25.590 MainServer::HandleAnnounce Playback
2009-07-11 16:14:25.590 adding: purdymyth as a client (events: 0)
2009-07-11 16:14:25.592 MainServer::HandleAnnounce FileTransfer
2009-07-11 16:14:25.592 adding: purdymyth as a remote file transfer
2009-07-11 16:14:25.593 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.593 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2009-07-11 16:14:25.593 RingBuffer::RingBuffer(): Failed to open remote file ()

```

_**Things I know:**_
[LIST]
[*]/video is writable by mythtv
[*]/video is setup as the storagegroup for 'purdymyth' (my box name)
[*]my box is a combined backend/frontend setup
[*]database access isn't a problem (entries are being written)
[*]it's not a tuner - I can watch live tv
[/LIST]

I've been banging my head against this problem for a while and I've upgraded my mythbuntu installation from 8.04 to 9.04 in the process, hoping that would help, but it hasn't (and it probably has made something worse). I get the feeling there's some sort of configuration thing I'm missing.

Thanks for any help you can provide!

---

### Post by frznlogic on 2009-07-12
I just had a similar problem, in the end, i turned off "strict commercial detection", and all of a sudden the recording function worked as expected. My problem was that none of the files where actually created on disk, when i turned off that setting, they started getting generated.  Mind you, this is the first time i ever set this up so it may be completely unrelated.

---

### Post by JPurdy on 2009-07-12
Thanks for the reply, frznlogic! I gave that a shot and that doesn't seem to make a difference.

I did a manual [FONT="Courier New"]mythbackend -v all[/FONT] to get more output - do these lines mean anything to anyone?

```
2009-07-12 14:44:31.259 RingBuf(): OpenFile(, 0)
2009-07-12 14:44:31.259 MythSocket(7f2c44033e40:18): new socket
2009-07-12 14:44:31.260 MythSocket(7f2c44033e40:18): attempting connect() to (0.0.0.0:65535)
2009-07-12 14:44:31.260 MythSocket(7f2c44033e40:18): connect() failed (ConnectionRefused)
2009-07-12 14:44:31.260 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2009-07-12 14:44:31.260 MythSocket(7f2c44033e40:18): DownRef: -1
2009-07-12 14:44:31.260 MythSocket(7f2c44033e40:-1): delete socket
```

Where is Myth getting the 0.0.0.0 and 65535 parts of the address?

Thanks!

---

### Post by NT4usB on 2009-07-20
Mine just sh!t the bed too. Been working fine all day (and for the last three years...) 
Messing with getting channels sorted on the slave. 
Restarted the master and...```
2009-07-19 23:20:50.024 MythSocket(a324838:13): connect() failed (ConnectionRefused)
2009-07-19 23:20:50.024 Connection to master server timed out.
2009-07-19 23:20:50.024 MythSocket(a324838:13): DownRef: -1
2009-07-19 23:20:50.024 MythSocket(a324838:-1): delete socket
2009-07-19 23:20:51.025 MythSocket(a317c80:13): new socket
2009-07-19 23:20:51.025 Connecting to master server: 192.168.0.103:6543
2009-07-19 23:20:51.025 MythSocket(a317c80:13): attempting connect() to (192.168.0.103:6543)
2009-07-19 23:20:51.025 MythSocket(a317c80:13): connect() failed (ConnectionRefused)
2009-07-19 23:20:51.025 Connection to master server timed out.
2009-07-19 23:20:51.025 MythSocket(a317c80:13): DownRef: -1
2009-07-19 23:20:51.025 MythSocket(a317c80:-1): delete socket
2009-07-19 23:20:52.026 MythSocket(a343238:13): new socket
2009-07-19 23:20:52.026 Connecting to master server: 192.168.0.103:6543
2009-07-19 23:20:52.026 MythSocket(a343238:13): attempting connect() to (192.168.0.103:6543)
2009-07-19 23:20:52.026 MythSocket(a343238:13): connect() failed (ConnectionRefused)
2009-07-19 23:20:52.026 Connection to master server timed out.
2009-07-19 23:20:52.026 MythSocket(a343238:13): DownRef: -1
2009-07-19 23:20:52.027 MythSocket(a343238:-1): delete socket
2009-07-19 23:20:53.028 MythSocket(a33f6d8:13): new socket
2009-07-19 23:20:53.028 Connecting to master server: 192.168.0.103:6543
2009-07-19 23:20:53.028 MythSocket(a33f6d8:13): attempting connect() to (192.168.0.103:6543)
2009-07-19 23:20:53.028 MythSocket(a33f6d8:13): connect() failed (ConnectionRefused)
2009-07-19 23:20:53.028 Connection to master server timed out.
2009-07-19 23:20:53.028 MythSocket(a33f6d8:13): DownRef: -1
2009-07-19 23:20:53.028 MythSocket(a33f6d8:-1): delete socket

```
Fun! Fun! Fun...!

ED:
Googled some more and diddlefscked around with the DB. 
MasterServerIP in the settings table was *NULL* (as it should be.) 
I unchecked and rechecked the checkbox, doubleclicked in the box where the hostname goes, found the MBE name in there so I selected it.
Restarted mysql and the MBE (again!) and it now works.
Checked MasterServerIP in settings and it's changed itself back to *NULL* but wtf...
If it works, don't fix it!

---

