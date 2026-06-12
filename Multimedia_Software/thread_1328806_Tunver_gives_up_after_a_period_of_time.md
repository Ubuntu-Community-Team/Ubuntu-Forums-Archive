---
title: "Tunver gives up after a period of time"
date: 2009-11-16
forum: Multimedia Software
---

### Post by frugal on 2009-11-16
Hi,

I've been running Mythbuntu for about 6 months now and it's been working great overall but I've had a problem where after a period of time my tuner (a Hauppage WinTV-PVR-USB2) seems to stop responding and won't record anything. I was running 32-bit Jaunty but recently upgraded to 64-bit Karmic and have the same issue.

The only clue I have so far is from the backend log file:

```

2009-11-15 01:29:00.765 Reschedule requested for id 0.
2009-11-15 01:29:01.053 Scheduled 171 items in 0.3 = 0.04 match + 0.24 place
2009-11-15 01:29:29.124 TVRec(1): ASK_RECORDING 1 29 0 0
2009-11-15 01:30:02.134 TVRec(1): Changing from None to Watching RecordingOnly
2009-11-15 01:30:02.177 TVRec(1): HW Tuner: 1->1
2009-11-15 01:30:02.380 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-11-15 01:30:02.435 Started recording: Robot Chicken: channel 1044 on cardid 1, sourceid 1
2009-11-15 01:30:04.881 DevRdB(/dev/video0) Error: Poll giving up
2009-11-15 01:30:04.921 MPEGRec(/dev/video0) Error: Device error detected
2009-11-15 01:30:04.996 DevRdB(/dev/video0): Stop(): Not running.
2009-11-15 01:30:07.545 DevRdB(/dev/video0) Error: Poll giving up
2009-11-15 01:30:07.585 MPEGRec(/dev/video0) Error: Device error detected
2009-11-15 01:30:07.635 DevRdB(/dev/video0): Stop(): Not running.
```

Typically it's after about a week of uptime but yesterday I rebooted the system and it failed again after recording a few shows yesterday.

If it makes a difference, I leave the box running all the time (haven't setup any power saving yet).

Any help with solving this would be greatly appreciated.

---

