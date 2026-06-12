---
title: "VDPAU for Atom+Ion Motherboard...How to install Nvidia  190.42"
date: 2010-04-16
forum: Multimedia Software
---

### Post by Kdar on 2010-04-16
How do I install Nvidia  190.42 driver with VDPAU on Ubuntu 9.10?

I have a Atom+Ion motherboard: ZOTAC IONITX A-U

I tried to add ppa of VDPAU: ppa:nvidia-vdpau/ppa

and installed following packages from Synaptic:
nvidia-190-modaliases
nvidia-190-kernel-source
nvidia-glx-190

What do I need to do?

----
Or should I get latest driver from Nvidia: 195.36.15?

---

### Post by cchhrriiss121212 on 2010-04-16
Install smplayer from synaptic and select vdpau output from preferences. The 190 driver should be fine for now. Here's a similar thread:
[http://ubuntuforums.org/showthread.php?t=1388656](http://ubuntuforums.org/showthread.php?t=1388656)
And here's what I followed to get it working:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

---

### Post by Kdar on 2010-04-16
This will work with XBMC?

or I will need to do some configuration in XBMC as well?

---

### Post by cchhrriiss121212 on 2010-04-16
Vdpau is supported in xine, mplayer, xbmc and a few others I think. It's not really configuration, you just open up video preferences and select vdpau output. You can check vdpau is working by looking at how much cpu usage you are using, around 20% is normal.

---

