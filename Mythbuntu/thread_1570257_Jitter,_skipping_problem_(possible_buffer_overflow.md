---
title: "Jitter, skipping problem (possible buffer overflow?) pvr-250"
date: 2010-09-07
forum: Mythbuntu
---

### Post by stoobers on 2010-09-07
Hi,

Please re-direct me if I am posting in the wrong place.

I never had this skipping issue under jaunty.

I have built a new computer.  It is much faster than my old computer.  It has a much larger hard disk.  More memory.  Installed Lucid.  Life was good...

But my mythtv (Mythbuntu) recordings on this new computer now have an issue:  They seem to be "skipping".  Everything plays along just fine, then it looks like 5 or more seconds of video and audio race past within one second.  Its super annoying.

If I were to guess what is wrong, I would guess the system is dropping frames of video and audio.  I have played the MPG files back in mplayer on the command line, and I get the same problem, so I think the issue is in the record, not the playback.

I figure the problem could be the hard disk, or some sort of buffer overflow or heavens I have no idea!  

Here is an a blip from the log file showing the recording.:

2010-09-07 13:00:02.905 ProgramInfo(): Updated pathname '':'' -> '1008_20100907130000.mpg'
2010-09-07 13:00:02.958 TVRec(2): Changing from None to RecordingOnly
2010-09-07 13:00:02.968 TVRec(2): HW Tuner: 2->2
2010-09-07 13:00:04.025 ret_pid(0) child(20655) status(0x0)
2010-09-07 13:00:05.033 ret_pid(0) child(20655) status(0x0)
2010-09-07 13:00:06.257 ret_pid(0) child(20655) status(0x0)
2010-09-07 13:00:07.650 ret_pid(0) child(20655) status(0x0)
2010-09-07 13:00:09.034 ret_pid(0) child(20655) status(0x0)
2010-09-07 13:00:10.049 ret_pid(20655) child(20655) status(0x0)
2010-09-07 13:00:10.056 External Tuning program exited with no error
2010-09-07 13:00:10.110 TVRec(2): rec->GetFileName(): '/var/lib/mythtv/recordings/1008_20100907130000.m
pg'
2010-09-07 13:00:10.240 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-09-07 13:00:10.246 Started recording: Star Trek: Enterprise "Affliction": channel 1008 on cardid 2, sourceid 1
2010-09-07 13:05:23.472 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-09-07 13:20:23.555 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-09-07 13:35:23.641 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-09-07 13:50:23.727 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-09-07 13:59:00.236 Reschedule requested for id 0.
2010-09-07 13:59:00.755 Scheduled 372 items in 0.5 = 0.01 match + 0.50 place
2010-09-07 13:59:30.266 TVRec(2): ASK_RECORDING 2 29 0 0
2010-09-07 14:00:00.363 TVRec(2): Changing from RecordingOnly to None
2010-09-07 14:00:00.372 ProgramInfo(): Updated pathname '':'' -> '1008_20100907130000.mpg'
2010-09-07 14:00:00.379 Finished recording Star Trek: Enterprise "Affliction": channel 1008
2010-09-07 14:00:00.432 ProgramInfo(1008_20100907130000.mpg), Error: Unknown type, recording width was 0
2010-09-07 14:00:00.483 ProgramInfo(): Updated pathname '':'' -> '1008_20100907130000.mpg'
2010-09-07 14:00:00.673 ProgramInfo(): Updated pathname '':'' -> '1008_20100907130000.mpg'
2010-09-07 14:00:00.727 Finished recording Star Trek: Enterprise "Affliction": channel 1008


Where do I begin?

---

