---
title: "Video Issues"
date: 2011-01-04
forum: Multimedia Software
---

### Post by JLFernald on 2011-01-04
All video is choppy. CPU spikes to 100% when trying to playback. Geforce 6800 using Nvidia drivers. I have enabled XvMC. Don't know what else to try.

Mostly trying to get MythTV working (live tv and recordings are both choppy) but having the same problems despite the player

---

### Post by JLFernald on 2011-01-04
Using 10.04 btw

---

### Post by BicyclerBoy on 2011-01-04
Exactly which Geforce 6800 model ?
Do you have the latest drivers ? Your card is still supported just..

This GPU is purevideo 1 & does full MPEG-1 MPEG-2 in hardware.
VC1 & H264 are not full decoded in h/w.

Get a new video card
GT220, 240 & 430 are recommended because of feature set C.

or do all decode on the CPU (change playback profile to CPU++).

[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)
quote "The latest NVidia driver packages support XvMC on hardware which supports XvMC instead of VDPAU."

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

[https://wiki.archlinux.org/index.php/Enable_XvMC_for_NVIDIA_video_cards](https://wiki.archlinux.org/index.php/Enable_XvMC_for_NVIDIA_video_cards)
this suggest that XvMC has little to offer & no future..

MythTV is dropping XvMC support come 0.25.

---

