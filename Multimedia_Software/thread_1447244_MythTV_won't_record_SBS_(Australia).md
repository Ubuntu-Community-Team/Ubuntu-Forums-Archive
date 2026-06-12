---
title: "MythTV won't record SBS (Australia)"
date: 2010-04-05
forum: Multimedia Software
---

### Post by lexvictory on 2010-04-05
When I initially set up mythTV, the default settings would not find SBS for my area. After a bit of googling, I managed to get it tuned in.

The problem I am having now is that it will not record from any of the SBS channels.
When a program is scheduled, the light on my tuner stick lights up to indicate it's recieving a signal, and I can't see any errors in the log between when it says starting recording to when it says finished recording.
The problem is, the .mpg file never gets written to the hard drive, so when I go to watch a recording mythFrontend says the file is missing.


I'm not sure what info I'll need to supply to help diagnose, but I'll start with the backend log (part of it), including when a program is being scheduled/recorded and when a frontend is trying to access the "recorded" program.

Please note that I'm comfortable with the command line, etc - so don't worry about getting technical on me :)

> 2010-04-05 16:04:03.856 adding: XANDER-LAPTOP as a client (events: 0)
2010-04-05 16:04:03.918 MainServer::ANN Monitor
2010-04-05 16:04:03.986 adding: XANDER-LAPTOP as a client (events: 1)
2010-04-05 16:04:17.549 Reschedule requested for id 20.
2010-04-05 16:04:17.729 Scheduled 1 items in 0.2 = 0.10 match + 0.08 place
2010-04-05 16:04:17.945 TVRec(1): Changing from None to Watching RecordingOnly
2010-04-05 16:04:18.008 TVRec(1): HW Tuner: 1->1
2010-04-05 16:04:18.265 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-04-05 16:04:18.324 Started recording: Insight "Reviving The Health System": channel 1801 on cardid 1, sourceid 1
2010-04-05 16:04:18.551 TVRec(2): ASK_RECORDING 2 0 0 0
2010-04-05 16:04:38.059 Reschedule requested for id 21.
2010-04-05 16:04:38.184 Scheduled 2 items in 0.1 = 0.06 match + 0.06 place
2010-04-05 16:13:56.851 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-04-05 16:27:54.175 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-04-05 16:28:56.981 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-04-05 16:30:00.488 TVRec(1): Changing from Watching RecordingOnly to None
2010-04-05 16:30:00.597 Finished recording Insight "Reviving The Health System": channel 1801
2010-04-05 16:30:00.600 Reschedule requested for id 0.
2010-04-05 16:30:00.768 Scheduled 1 items in 0.2 = 0.09 match + 0.07 place
2010-04-05 16:43:57.093 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-04-05 16:45:39.723 MainServer::ANN Monitor
2010-04-05 16:45:39.770 adding: XANDER as a client (events: 0)
2010-04-05 16:45:39.834 MainServer::ANN Monitor
2010-04-05 16:45:39.895 adding: XANDER as a client (events: 1)
2010-04-05 16:45:47.686 ProgramInfo, Error: GetPlaybackURL: '1801_20100402192500.mpg' should be local, but it can not be found.
2010-04-05 16:45:47.750 ProgramInfo, Error: GetPlaybackURL: '1032_20100404212500.mpg' should be local, but it can not be found.
2010-04-05 16:45:47.808 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.043 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.172 MainServer::ANN Monitor
2010-04-05 16:45:48.230 adding: XANDER as a client (events: 0)
2010-04-05 16:45:48.294 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.358 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.414 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/lex-desktop/1801_20100405160400.mpg'
2010-04-05 16:45:48.473 MainServer: Failed to make preview image.
2010-04-05 16:45:48.527 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.651 ProgramInfo, Error: GetPlaybackURL: '1032_20100404212500.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.783 MainServer::ANN Monitor
2010-04-05 16:45:48.848 adding: XANDER as a client (events: 0)
2010-04-05 16:45:48.913 ProgramInfo, Error: GetPlaybackURL: '1032_20100404212500.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.979 ProgramInfo, Error: GetPlaybackURL: '1032_20100404212500.mpg' should be local, but it can not be found.
2010-04-05 16:45:48.979 ProgramInfo, Error: GetPlaybackURL: '1801_20100402192500.mpg' should be local, but it can not be found.
2010-04-05 16:45:49.032 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/lex-desktop/1032_20100404212500.mpg'
2010-04-05 16:45:49.141 MainServer: Failed to make preview image.
2010-04-05 16:45:49.152 MainServer::ANN Monitor
2010-04-05 16:45:49.266 adding: XANDER as a client (events: 0)
2010-04-05 16:45:49.323 ProgramInfo, Error: GetPlaybackURL: '1801_20100402192500.mpg' should be local, but it can not be found.
2010-04-05 16:45:49.379 ProgramInfo, Error: GetPlaybackURL: '1801_20100402192500.mpg' should be local, but it can not be found.
2010-04-05 16:45:49.426 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/lex-desktop/1801_20100402192500.mpg'
2010-04-05 16:45:49.492 MainServer: Failed to make preview image.
2010-04-05 16:45:50.897 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:51.626 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:45:51.682 ProgramInfo, Error: GetPlaybackURL: '1801_20100405160400.mpg' should be local, but it can not be found.
2010-04-05 16:46:09.295 Reschedule requested for id 21.
2010-04-05 16:46:09.416 Scheduled 0 items in 0.1 = 0.06 match + 0.06 place
2010-04-05 16:57:58.227 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-04-05 16:58:45.069 MainServer::ANN Monitor
2010-04-05 16:58:45.120 adding: XANDER as a client (events: 0)
2010-04-05 16:58:45.175 MainServer::ANN Monitor
2010-04-05 16:58:45.229 adding: XANDER as a client (events: 1)
2010-04-05 16:58:54.131 MainServer::ANN Playback
2010-04-05 16:58:54.179 adding: XANDER as a client (events: 0)

---

