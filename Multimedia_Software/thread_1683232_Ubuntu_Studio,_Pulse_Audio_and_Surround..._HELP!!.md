---
title: "Ubuntu Studio, Pulse Audio and Surround... HELP!!"
date: 2011-02-07
forum: Multimedia Software
---

### Post by btdave on 2011-02-07
Got a slight problem, i'm sure there is an easy fix but I can't find it on here or anywhere else.

What the issue is, is that PulseAudio has incorrectly mapped the rear left and right channels and the center channel

In the pulseaudio manager under the devices tab I open up the only sink i've got there
alsa_output.pci-0000_00_1b.0.analog-surround-51
and it shows the channel map to be
front-left,front-right,rear-left,rear-right,front-center,lfe

However is needs to be
front-left,front-right,front-center,rear-left,rear-right,lfe

Any ideas? I've tried adding the channel map parameter to the default.pa and the daemon.conf files but then it won't work connect at all.

Quiet annoying really :(

I know there is no problem with the hardware side of things as it does work in windows correctly.

---

### Post by btdave on 2011-02-07
OK never mind, it seems to be a problem with mythtv videos :S

---

