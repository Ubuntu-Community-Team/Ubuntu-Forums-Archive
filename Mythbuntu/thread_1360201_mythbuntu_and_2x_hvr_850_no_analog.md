---
title: "mythbuntu and 2x hvr 850 no analog"
date: 2009-12-20
forum: Mythbuntu
---

### Post by zombu2 on 2009-12-20
hi
i m trying to get some analog out of my hvr-850 cards but to no avail in mythbuntu
i have tried to see in vlc with good success using v4l-2 the regular v4l gives me a can t open error

here is the log i got from the backend 
```
2009-12-20 16:22:21.897 adding: rossi-desktop as a client (events: 0)
2009-12-20 16:22:21.949 TVRec(1): Changing from None to Watching WatchingLiveTV
2009-12-20 16:22:22.001 TVRec(1): HW Tuner: 1->1
2009-12-20 16:22:30.578 Channel(/dev/video1) Error: InitPictureAttribute(    colour): failed to query controls.
                        eno: Invalid argument (22)
2009-12-20 16:22:30.878 Channel(/dev/video1) Error: InitPictureAttribute(    colour): failed to query controls.
                        eno: Invalid argument (22)
2009-12-20 16:22:30.966 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
strange error flushing buffer ...
2009-12-20 16:22:31.009 TVRec(1): Changing from Watching WatchingLiveTV to None
2009-12-20 16:22:31.128 Unknown type, recording width was 0
2009-12-20 16:22:31.324 Finished recording How to Lose a Guy in 10 Days: channel 1052
2009-12-20 16:22:31.383 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffb0601678)
2009-12-20 16:22:31.442 MythSocket(ffffffffb0601678:-1): writeStringList: Error, socket went unconnected.
                        We wrote 0 of 10 bytes with 1 errors
2009-12-20 16:22:51.494 Expiring 0 MBytes for 1052 @ Sun Dec 20 16:00:00 2009 => How to Lose a Guy in 10 Days
2009-12-20 16:23:36.520 MainServer::ANN Playback
2009-12-20 16:23:36.585 adding: rossi-desktop as a client (events: 0)
2009-12-20 16:23:36.628 TVRec(1): Changing from None to Watching WatchingLiveTV
2009-12-20 16:23:36.688 TVRec(1): HW Tuner: 1->1

```

if somebody would help me out with that i would apreciate it

---

### Post by zombu2 on 2009-12-20
BUMP

anyone any idea

---

