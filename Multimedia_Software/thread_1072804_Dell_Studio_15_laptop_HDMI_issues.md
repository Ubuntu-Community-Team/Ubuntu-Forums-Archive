---
title: "Dell Studio 15 laptop HDMI issues"
date: 2009-02-17
forum: Multimedia Software
---

### Post by mpuz on 2009-02-17
I have been using Ubuntu 8.10 for several months on my laptop.  I recently purchased a Samsung LN46A650 LCD HDTV and I tried connecting the laptop via HDMI.  I have two problems that I have been unable to solve:

1. HDMI audio does not work.  After configuring the Sound Preferences to HDMI and restarting, I was able to hear the Sound Preferences test sound through HDMI.  However, all other sounds (DVD, websites, etc.) went through the laptop speakers.

2. HDMI video does not work if the HDMI cable is connected when I start the computer.  I'm shooting for single monitor here - laptop closed and video on the TV.  It works fine if I start the computer, plug in HDMI, and adjust the video settings.  However, when I boot up with the HDMI cable plugged in, the TV video is severely distorted - it looks like sync rates are all messed up.  

Here is the lspci info on the graphics card:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Any ideas?

---

### Post by mpuz on 2009-02-20
Here is some more info.  When X starts, the TV detects the HDMI video as 1360x768, 60Hz.  xrandr doesn't say that that resolution is supported.  

I added an xrandr script to configure it for 1280x1024 in gdm and in init, but none of those change the 1360x768 detection by the TV.

---

### Post by d1ma5 on 2010-09-10
Hey, 

I've been running into same problems with Dell Studio 15. I can get image sometimes, but it flickers and disappears when I need it the most. Has anyone found a solution?

---

### Post by coolleo83 on 2010-10-02
This is still happening to me. I am on LUCID 10.04 dell inspiron 1525 - INTEL HDMI
Video works just fine, i even tried switching the hardware from analog to HDMI or Analog+ HDMI, but still no luck. has anyone able to resolve it yet??

---

