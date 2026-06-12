---
title: "Fullscreen Video Crashes Xorg"
date: 2009-01-17
forum: Multimedia Software
---

### Post by tdreyer1 on 2009-01-17
I have an odd situation. I am setting up an ubuntu 8.04 install to run XBMC. My main goal is to get it running though the S-video out on my ATI Radeon RV100 QY [Radeon 7000/VE]. 

Through the instructions found [here]("http://ubuntuforums.org/showthread.php?t=728157"), I finally succeeded in getting the tv-out to work. Unfortunately, whenever I play a video in any program, it only plays on the monitor, not the tv. 

To fix this, I run the command:
```
xrandr --output VGA-0 --off
```
to turn the monitor off, and leave only the tv on. This works to make the video play on the tv, but anytime I switch from windowed mode to full screen in totem, everything crashes and I get sent back to the login screen. 

I've noticed that this doesn't happen in VLC, or if I am already in full screen when I run
```
xrandr --output VGA-0 --off
```
it won't crash.

This is 100% reproduceable, so if you need more info, let me know and I'll get it for you.

---

