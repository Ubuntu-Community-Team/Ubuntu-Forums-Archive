---
title: "mythtv 0.24 frontend hangs"
date: 2011-01-18
forum: Multimedia Software
---

### Post by rosbif on 2011-01-18
Running Ubuntu 10.04 on AMD Athlon X2 Dual Core 4600+, with mythtv fixes/0.24 from PPA mythbuntu repo.
I recently updated from 0.22 and now my frontend hangs in the following situation:
Start frontend
Select WatchTV
Watch for a bit (works fine), then exit to menu
Select WatchTV again and it hangs forever.

Last few lines from log show:
```
2011-01-18 13:53:07.143 TV: Attempting to change from None to WatchingLiveTV
2011-01-18 13:53:07.144 MythCoreContext: Connecting to backend server: 192.168.1.30:6543 (try 1 of 1)
2011-01-18 13:53:07.145 Using protocol version 63
2011-01-18 13:53:07.194 Spawning LiveTV Recorder -- begin
2011-01-18 13:53:07.516 Spawning LiveTV Recorder -- end
2011-01-18 13:53:07.530 We have a playbackURL(myth://192.168.1.30:6543/1015_20110118135307.mpg) & cardtype(DUMMY)
2011-01-18 13:53:07.530 We have a RingBuffer
2011-01-18 13:53:07.639 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-01-18 13:53:07.727 OSD: Base theme size: 1280x720
2011-01-18 13:53:07.727 OSD: Scaling factors: 0.5625x0.8
2011-01-18 13:53:07.795 OSD: Base theme size: 1280x720
2011-01-18 13:53:07.795 OSD: Scaling factors: 0.5625x0.8
2011-01-18 13:53:07.803 Player(1): Video timing method: USleep with busy wait
2011-01-18 13:53:07.803 TV: Changing from None to WatchingLiveTV
2011-01-18 13:53:07.803 TV: State is LiveTV & mctx == ctx
2011-01-18 13:53:07.806 TV: UpdateOSDInput done
2011-01-18 13:53:07.806 TV: UpdateLCD done
2011-01-18 13:53:07.806 TV: ITVRestart done
```

I've checked that I have the right audio driver and I've completely re-installed myth but no joy.....

---

### Post by rosbif on 2011-01-18
So, I've looked at the backend, also 10.04 (on a separate machine, I run split FE/BE) and this is what appears at the time of the crash:
```
2011-01-18 13:53:00.766 TVRec(10): Changing from WatchingLiveTV to None
2011-01-18 13:53:01.171 Finished recording Everwood "Blind Faith": channel 1015
2011-01-18 13:53:07.010 MainServer::ANN Playback
2011-01-18 13:53:07.038 adding: paul-desktop as a client (events: 0)
2011-01-18 13:53:07.060 TVRec(10): Changing from None to WatchingLiveTV
2011-01-18 13:53:07.076 TVRec(10): HW Tuner: 10->10
2011-01-18 13:53:07.345 **LoadFromScheduler(): Error, called from backend.**
2011-01-18 13:53:07.351 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-01-18 13:53:08.907 Finished recording Everwood "Blind Faith": channel 1015
2011-01-18 13:53:08.922 **LoadFromScheduler(): Error, called from backend**.
2011-01-18 13:53:08.927 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
```

Don't know the significance of the LoadFromScheduler error.  I'm running DVB-T from Freeview (UK) on a dual tuner Nova-T card.
And just for laffs, I installed an FE on my macbook and it shows exactly the same behaviour.

---

