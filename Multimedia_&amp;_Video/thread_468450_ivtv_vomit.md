---
title: "ivtv vomit"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by ijustam on 2007-06-08
So, I apparently broke something today.  Case in point is attached.

I use a Hauppauge PVR-150.  It worked fine until I started playing with MythTV again... apparently I did something that borked ivtv.  I keep ivtv tuned to channel 3 to use TiVo (I have a subscription that I'm going to run out, I've been setting up MythTV so that it will work right when I'm ready for it).

I use standard US cable from the wall, into the TiVo, to the VCR/DVD, to my computer.  It worked flawlessly until I unplugged the TiVo to test MythTV, and then when I plugged the cable straight from the wall ivtv got all antsy.  I do not use MythTV to watch TV at the moment, rather mplayer.

The component inputs display fine, no problems at all.

Is my tuner input messed up, or perhaps a hardware issue (god forbid) ?

One last thing, my device name recently got changed from video1 to video0.  My webcam used to be video0 but I unplugged it and the tuner took over video0 since then, but I have corrected mplayer and ivtv to use video0.

mplayer command: mplayer -vo xv /dev/video0
session command: ivtv-tune -c 3 -d /dev/video0 (to tune to TiVo)

Any help would be appreciated :)

---

### Post by ijustam on 2007-06-10
Bump

---

