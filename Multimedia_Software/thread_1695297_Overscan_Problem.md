---
title: "Overscan Problem"
date: 2011-02-25
forum: Multimedia Software
---

### Post by TPrime on 2011-02-25
Anyone know how I can fix my overscan issues on a pansonic viera tc-p42c1 plasma tv? I've seen the word 'modeline' come up frequently in searches, but I have no idea what that is or how to use it.

---

### Post by bance on 2011-02-26
The simplest way is to make sure the TV is set to PC mode. My LG plasma required me to rename an input to PC, I use HDMI to connect.

If you have an Nvidia card there is a slider in NVIDIA X Server settings that you can use to adjust overscan.

I know that it is possible to edit X11.conf to include modelines.... but maybe try the other options first!

HTH Steve.

---

### Post by doas777 on 2011-02-26
what kind of vid card do you have? make/model please. what driver do you have installed (or how did you install a driver)? 

modelines are pretty old school, and don't quite mesh with newer ubuntus (at least the gnome versions), because the xorg.conf is largely deprecated at this point. I have tried modelines to deal with underscan on some boxes in the past but it only worked correctly with some vid cards (cards that had under/overscan control in the driver config gui). if the driver won't support an xorg config statement, it will usually be ignored, so setting "TVOverscan 1.0" in the xorg for a card/driver that does not support scaling will do nothing.

---

### Post by TPrime on 2011-02-26
The video source is the onboard hdmi output on an asus p7q57-m do motherboard. Pretty sure it's a intel chip. The driver is whatever was autodetected during the install. It was perfect for about a day before the overscan problem started. I'll try renaming the tv input to PC, but other than that I can't find any options relating to the display dimensions.

---

### Post by TPrime on 2011-02-26
Still no luck. Any ideas?

---

