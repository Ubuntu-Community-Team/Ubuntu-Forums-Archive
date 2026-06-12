---
title: "HD live tv better than recorded TV - Firewire"
date: 2008-05-08
forum: Mythbuntu
---

### Post by volkswagner on 2008-05-08
I am trying to discover the cause of playback issues. 
I am running mythbuntu 7.10/mythtv .21 (desktop), and UUE 1.6/mythtv .21 (laptop).
Master backend is mythbuntu 7.10AMD64/mythtv .21

I have two frontends, laptop wifi(ati mobile 200) and wired desktop (nvidia 6200).  Both exhibit the same problem.  I have SA3250HD connected via firewire to master backend.  I can usually view live HDTV without visible issues.  Most often I can not play recordings.  Oddly this is not 100% on fail or positive playback.

I will try to break it down.

I can view live HD on both frontends 99% of the time.  I do however see the frontend.log filled with the following during successful playback.
```

2008-05-08 19:06:06.480 audio stream changed
2008-05-08 19:06:06.495 audio stream changed
2008-05-08 19:06:06.531 audio stream changed
2008-05-08 19:06:06.563 audio stream changed
2008-05-08 19:06:06.595 audio stream changed
2008-05-08 19:06:06.631 audio stream changed
2008-05-08 19:06:06.664 audio stream changed
2008-05-08 19:06:06.696 audio stream changed
2008-05-08 19:06:06.733 audio stream changed
2008-05-08 19:06:06.764 audio stream changed
2008-05-08 19:06:06.796 audio stream changed
2008-05-08 19:06:06.834 audio stream changed
2008-05-08 19:06:06.864 audio stream changed
2008-05-08 19:06:06.879 audio stream changed
2008-05-08 19:06:06.913 audio stream changed
```

I rarely can play an HD recording.  The sound outputs in bursts and the video freezes when sound drops out.

Here is what I see in the frontend.log when this happens.
```

2008-05-08 19:31:05.205 audio stream changed
2008-05-08 19:31:05.255 audio stream changed
2008-05-08 19:31:05.546 NVP: prebuffering pause
2008-05-08 19:31:05.582 audio stream changed
2008-05-08 19:31:05.599 audio stream changed
2008-05-08 19:31:05.652 audio stream changed
2008-05-08 19:31:05.712 audio stream changed
2008-05-08 19:31:05.727 audio stream changed
2008-05-08 19:31:05.752 NVP: prebuffering pause
2008-05-08 19:31:05.780 audio stream changed
2008-05-08 19:31:05.816 audio stream changed
2008-05-08 19:31:05.863 audio stream changed
2008-05-08 19:31:05.924 audio stream changed
2008-05-08 19:31:05.957 audio stream changed
2008-05-08 19:31:05.959 audio stream changed
2008-05-08 19:31:05.990 audio stream changed
2008-05-08 19:31:06.298 NVP: prebuffering pause
2008-05-08 19:31:06.340 audio stream changed
2008-05-08 19:31:06.359 audio stream changed
```

The two scenarios hold true for both frontends.  Whenever the log displays "NVP: prebuffering pause", the video freezes and sound skips. 

Today without  making any changes, was the first time I was able to play an HD recording with the same result as above with live HD.  It was just a fluke I guess.

Since this happens to both frontend machines, I can assume this is a problem with the backend?  I do not see any issues in the backend.log when I have these playing.

---

