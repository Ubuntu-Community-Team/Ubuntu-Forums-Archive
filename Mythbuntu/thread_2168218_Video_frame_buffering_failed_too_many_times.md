---
title: "Video frame buffering failed too many times"
date: 2013-08-16
forum: Mythbuntu
---

### Post by drewdin on 2013-08-16
I am running 12.04 .26 with an HD homerun prime. , everything has been fine until today when no matter what i watch i get the following error and myth jumps back to the main screen. The recording are fine, it is just with live tv. 

```
Video frame buffering failed too many times
```

Here is my mythbackend log, does anyone have any suggestions on what I can try to get it working again? Thanks

```
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120409223000.mpg): GetPlaybackURL: '1165_20120409223000.mpg' should be local, but it can not be found.Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120409223000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120409230000.mpg): GetPlaybackURL: '1165_20120409230000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120409230000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410095604.mpg): GetPlaybackURL: '1165_20120410095604.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410095604.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410100000.mpg): GetPlaybackURL: '1165_20120410100000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410100000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410103000.mpg): GetPlaybackURL: '1165_20120410103000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410103000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410110000.mpg): GetPlaybackURL: '1165_20120410110000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410110000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410113000.mpg): GetPlaybackURL: '1165_20120410113000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410113000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410120000.mpg): GetPlaybackURL: '1165_20120410120000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410120000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1165_20120410123000.mpg): GetPlaybackURL: '1165_20120410123000.mpg' should be local, but it can not be found.
Aug 16 21:35:14 mythbackend mythlogserver: mythbackend[1990]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbackend/1165_20120410123000.mpg. File doesn't exist.  Database metadata will not be removed.
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mythbackend as a client (events: 0)
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mythbackend as a client (events: 1)
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Playback
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mythbackend as a client (events: 0)
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: E ProcessRequest mainserver.cpp:3778 (HandleRecorderQuery)  MainServer::HandleRecorderQuery() Command GET_FREE_INPUTS for unconnected encoder 7
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(2): Changing from None to WatchingLiveTV
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: I TVRecEvent tv_rec.cpp:3562 (TuningCheckForHWChange) TVRec(2): HW Tuner: 2->2
Aug 16 21:35:46 mythbackend mythlogserver: mythbackend[1990]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 16 21:35:47 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler dtvsignalmonitor.cpp:321 (HandlePAT) DTVSM(1312C3AE-0): Program #0 not found in PAT!#012Program Association Section#012 PSIP tableID(0x0) length(13) extension(0x0)#012      version(3) current(1) section(0) last_section(0)#012      tsid(0) programCount(1)#012  program number 10853 has PID 0x0034
Aug 16 21:35:47 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler dtvsignalmonitor.cpp:326 (HandlePAT) DTVSM(1312C3AE-0): But there is only one program in the PAT, so we'll just use it
Aug 16 21:35:47 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler hdhrstreamhandler.cpp:211 (UpdateFilters) HDHRSH(1312C3AE-0): UpdateFilters called in wrong tune mode
Aug 16 21:35:47 mythbackend mythlogserver: mythbackend[1990]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 16 21:35:47 mythbackend mythlogserver: mythbackend[1990]: E TVRecEvent recorderbase.cpp:166 (SetStrOption) RecBase(2:1312C3AE-0): SetStrOption(...recordingtype): Option not in profile.
Aug 16 21:35:48 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest recorderbase.cpp:395 (GetKeyframePositions) RecBase(2:1312C3AE-0): GetKeyframePositions(16,9223372036854775807,#1) out of 3
Aug 16 21:35:48 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest recorderbase.cpp:395 (GetKeyframePositions) RecBase(2:1312C3AE-0): GetKeyframePositions(16,9223372036854775807,#2) out of 4
Aug 16 21:36:07 mythbackend mythlogserver: mythbackend[1990]: E ProcessRequest mainserver.cpp:3778 (HandleRecorderQuery)  MainServer::HandleRecorderQuery() Command GET_FREE_INPUTS for unconnected encoder 7
Aug 16 21:36:07 mythbackend mythlogserver: mythbackend[1990]: I TVRecEvent tv_rec.cpp:3562 (TuningCheckForHWChange) TVRec(2): HW Tuner: 2->2
Aug 16 21:36:07 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler hdhrstreamhandler.cpp:211 (UpdateFilters) HDHRSH(1312C3AE-0): UpdateFilters called in wrong tune mode
Aug 16 21:36:07 mythbackend mythlogserver: mythbackend[1990]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 16 21:36:07 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler dtvsignalmonitor.cpp:321 (HandlePAT) DTVSM(1312C3AE-0): Program #0 not found in PAT!#012Program Association Section#012 PSIP tableID(0x0) length(13) extension(0x0)#012      version(5) current(1) section(0) last_section(0)#012      tsid(0) programCount(1)#012  program number 10803 has PID 0x0031
Aug 16 21:36:07 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler dtvsignalmonitor.cpp:326 (HandlePAT) DTVSM(1312C3AE-0): But there is only one program in the PAT, so we'll just use it
Aug 16 21:36:08 mythbackend mythlogserver: mythbackend[1990]: E HDHRStreamHandler hdhrstreamhandler.cpp:211 (UpdateFilters) HDHRSH(1312C3AE-0): UpdateFilters called in wrong tune mode
Aug 16 21:36:08 mythbackend mythlogserver: mythbackend[1990]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 16 21:36:08 mythbackend mythlogserver: mythbackend[1990]: E TVRecEvent recordinginfo.cpp:984 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1508_20130817013607.mpg): channame(WFXTDT (WFXT-DT)) startts(Sat Aug 17 00:00:00 2013) endts(Sat Aug 17 03:00:00 2013)#012             recstartts(Sat Aug 17 01:36:07 2013) recendts(Sat Aug 17 03:00:00 2013)#012             title(NFL Preseason Football)): recording already exists...
Aug 16 21:36:09 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest recorderbase.cpp:395 (GetKeyframePositions) RecBase(2:1312C3AE-0): GetKeyframePositions(49,9223372036854775807,#2) out of 6
Aug 16 21:36:10 mythbackend mythlogserver: mythbackend[1990]: I ProcessRequest recorderbase.cpp:395 (GetKeyframePositions) RecBase(2:1312C3AE-0): GetKeyframePositions(49,9223372036854775807,#4) out of 8
```

---

### Post by drewdin on 2013-08-16
ok, so i was browsing around and I found 4 files in the livetv folder that had weird extensions. They were 4-5 character extensions in all caps. They were different from everything else, they looked like files that didnt finish getting created. I deleted them and now everything works. Go figure

---

