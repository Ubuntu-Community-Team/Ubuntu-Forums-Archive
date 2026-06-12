---
title: "Had sound and lost it(kind of)"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by flowheat on 2006-07-02
As someone who has just recently made my first attempt at Linux, let me first say that I have been very pleased thus far.  Even going straight to a 64 bit version of ubuntu and running into a few problems here and there, I have been able to solve all my problems just from browsing this forum and using the Ubuntu wiki.

I guess that's where my problem begins.  My onboard sound card(Nvidia CK8S) was detected automatically and worked from day one.  However, I noticed that the sound was very fuzzy on mp3 playback.  Upon searching the forums I found a few possible fixes and somewhere in attempting to fix the fuzzy problem I ended up killing sound on everything but Rhythmbox music player which still plays, but still plays fuzzy.

I went through the process of trying to compile alsa drivers as an attempt to fix the problem but to no avail.  Now, i'm pretty much out of possible fixes.

Mplayer plays the video portion of video files but gives the error "Coukd not open/initialize Audio device -> No Sound."

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Why it shows up twice, but differently is beyond me.

Any help would be greatly appreciated.

---

