---
title: "Hauppaage HVR-2200 second tuner and slow channel switch"
date: 2010-05-13
forum: Multimedia Software
---

### Post by jugglingcats on 2010-05-13
Hi, I'm running MythBuntu 10.04 32-bit on an ASUS DualCore Atom + NVidia ION chipset. It's taken me a while to get it all working (still not there yet on the remote!), but there are a couple of glitches with the tuner card.

10.04 appears to have the kernel modules already, so I installed the firmware following linuxtv.org instructions and got it working pretty quickly in MythTV. I've since built the latest stable kernel module and updated the firmware to v4l-saa7164-1.0.3-3.fw which appears to be the latest. Same issues in both cases anyway.

Problem 1: The picture using /dev/dvb/adapter1 breaks up / stutters like there's a poor signal, although it says 90+% and /dev/dvb/adapter0 is rock solid. When I try with mplayer it plays but gives lots of errors on the second tuner, but I guess that's not surprising. Example output:

```
[mpeg2video @ 0x3d466c0]ac-tex damaged at 29 102 17%  0%  1.2% 0 0 
[mpeg2video @ 0x3d466c0]concealing 45 DC, 45 AC, 45 MV errors
[mpeg2video @ 0x3d466c0]concealing 34 DC, 34 AC, 34 MV errors% 0 0 
[mpeg2video @ 0x3d466c0]concealing 7 DC, 7 AC, 7 MV errors1.2% 0 0 

```Problem 2: Switching channels takes a good 7-10 seconds even on tuner 1. The screen goes black, then you get a tiny fragment of the original channel before the new channel kicks in. It's quite jarring.

Am I looking at a dodgy card?

Any help much appreciated!
Alfie.

---

### Post by jugglingcats on 2010-05-14
Update on this - the second tuner seems ok. I plugged my aerial directly into the HVR-2200 and the stutter on the second tuner is gone (previously was going via my current PVR).

But the channel change is still maybe 5-8 seconds. Is that normal?

Thanks, Alfie.

---

### Post by jugglingcats on 2010-05-17
Bump - anyone ;)

---

