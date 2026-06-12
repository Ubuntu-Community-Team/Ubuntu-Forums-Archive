---
title: "Master volume does not adjust USB headphones."
date: 2010-01-30
forum: Multimedia Software
---

### Post by asdfqwertyasdf on 2010-01-30
Ever since upgrading to Karmic, I haven't been able to adjust master volume when my USB headphones are chosen as the output device. If I try to adjust my master volume (via the media keys on my keyboard or gnome-volume-control), the output volume doesn't change until it's entirely muted. I can adjust the master volume fine when I'm outputting through internal audio.

I am able to adjust the volume fine on an application-specific basis, but this becomes quite a nuisance, especially when I switch between internal audio (where master volume is regulated) and USB audio (where master volume is always at full-blast).

This worked fine in Jaunty, and stopped working once I updated to Karmic.

My USB headphones are listed as "Storm HP-USB500 5.1 Headset". Thanks for your help!

---

### Post by sumix on 2011-09-19
Hi, I've been experiencing nearly exactly the same problem, with the only difference that I use an external USB DAC (working through snd_usb_audio), which is in fact technically the same as USB headphones concerning this issue.

Bad for me, I can't remember when this problem appeared so I can hardly trace an event that could relate to it (upgrade between Ubuntu versions - now running on 11.04 - or migration to xfce from gnome, which are two only actions that I think might have started this behavior).

I haven't paid much attention to it for quite a long time but now it really began to drive me up the wall so I've been searching for a solution, however haven't found any yet. Another thing not directly related to this topic (but I think dated to the same time as the first issue) is that after resuming from suspend, not only the default selected sound device is the integrated soundcard in my netbook (instead of the USB DAC as before), but it is also muted.


So if anybody knows what may be the cause(s), please let me know. Thanks!

---

