---
title: "Video playback slow after video driver upgrade"
date: 2009-01-25
forum: Multimedia Software
---

### Post by gap on 2009-01-25
In the last few days I've been having trouble playing videos which I was able to play without difficulty before. None of the usual players (VLC, mplayer) can keep the video in sync. The video and the audio stutter to the point that I cannot watch anything.

I think this may be related to the recent upgrade of the xserver-xorg-video-intel package (from 2.4.1-1ubuntu10.1 to 2.4.1-1ubuntu10.3), because nothing else has changed in my setup (no other packages installed, no settings changed of any sort). However, downgrading the video driver (using force version from Synaptic) did not change anything.

I've looked at the active processes, to see if anything else might be eating up CPU cycles, but there's nothing unusual there. I've looked at the CPU frequency scaling monitor, to make sure the CPU is running at full speed when playing video (it is).

Does anybody else have this problem lately? Is there any way I could diagnose more precisely the source of this performance drop?

Thanks.

---

### Post by gap on 2009-01-26
Turns out it is related to the CPU frequency scaling. Please ignore this thread, it doesn't belong here.

---

