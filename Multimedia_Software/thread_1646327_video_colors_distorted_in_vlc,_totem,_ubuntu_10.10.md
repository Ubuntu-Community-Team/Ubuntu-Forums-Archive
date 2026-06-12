---
title: "video colors distorted in vlc, totem, ubuntu 10.10 x64"
date: 2010-12-15
forum: Multimedia Software
---

### Post by pythonscript on 2010-12-15
I just upgraded to Ubuntu 10.10 x64, and the colors in my videos are distorted. Blue seems to be the primary tint over everything. This problem occurs regardless of video format (avi, mkv, flv, etc) and regardless of video player I use (banshee, totem, vlc, etc). However, no other colors in my operating system are distorted; it's only for these movies. I also have an NVidia video card, which I installed the latest driver for through the restricted drivers pop up. 

Any help here? I'm not liking the bluish tint over everything. 

Thank you!

---

### Post by no2498 on 2010-12-16
the problem is in totem set the saturation to 0
try a few video's reset the sliders to default

---

### Post by pythonscript on 2010-12-16
The saturation was already set to 0 (in the middle of the bar, that is) but I moved the Hue slider all the way to the left and it fixed the problem. Why do the settings in totem affect the system-wide settings, even for external applications like VLC?

---

### Post by pickarooney on 2010-12-16
Hard to know, but I get this kind of thing all the time

---

### Post by no2498 on 2010-12-16
its just something someone missed in trying to incorporate like 3 things into 1
a . makes it a big deal lol
enjoy a nice video

---

### Post by mc4man on 2010-12-16
If you have an nvidia card these is known to happen due to an old bug.

I haven't had it occur in a long time with any nvidia installs here, *possibly* because of  - 
After  install I always open nvidia setting and then save  the non xserver (xorg) settings to the default of ~/.nvidia-settings-rc 
You don't need to change anything though I usually lower the gamma a little.
(Xserver Color Correction)

These settings are saved thru "nvidia-settings Configuration" on bottom left

I believe in lucid, maverick or natty that 'Nvidia X Server Settings' should be in your startup applications and enabled. Having this so will also load the ~/.nvidia-settings.rc when booting up/login

YMMV

---

