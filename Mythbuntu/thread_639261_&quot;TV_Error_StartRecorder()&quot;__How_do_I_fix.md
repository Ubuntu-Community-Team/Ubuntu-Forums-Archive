---
title: "&quot;TV Error: StartRecorder()&quot;  How do I fix this?"
date: 2007-12-13
forum: Mythbuntu
---

### Post by Braedley on 2007-12-13
Just installed Mythbuntu (7.10) on my old computer today (Gutsy is on my relatively new computer), and I can't get any video.  Full error message returned in terminal is
```
2007-12-13 00:30:20.594 TV Error: StartRecorder() -- timed out waiting for recorder to start
2007-12-13 00:30:20.594 TV Error: LiveTV not successfully started
2007-12-13 00:30:20.600 TV: Deleting TV Chain in destructor

```

I'm using a Diamond XtremeTV PVR550 PCI tuner and an ATI Radeon 9800 Pro.

I've tested video and audio playback with an avi file, and it works fine.  Any help would be appreciated, my roommates and I would like to be able to watch some tv in the not to distant future.

---

### Post by DaBearsDaBearsDaBears on 2008-02-15
I have exactly the same video card and tuner card as you. 

Radeon 9800 Pro 256mb video Card
Diamond XtremeTV PVR550 PCI tuner

Run mythtv-setup and change the card type to "MPEG encoder: PVR-x50"

---

