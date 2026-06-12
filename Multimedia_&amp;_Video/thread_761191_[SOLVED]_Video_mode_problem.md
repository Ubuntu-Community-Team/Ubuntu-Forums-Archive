---
title: "[SOLVED] Video mode problem"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by 1915flyer on 2008-04-21
I just installed Ubuntu 7.1. Afterwards, I changed the screen resolution. When I rebooted, the splash screen is OK, but when it gets to the username/password, I get about 4 images of the login screen, all interlaced and virtually unreadable. I can manage to login without reading what's on the screen but once the "desktop" is displayed, I can't do or read anything. Everything's fuzzy and 4 of everything. I suspect it is a screen resolution problem, probably too high.

Is there a way to boot into "safe mode" or force a video mode that will enable me to read the screen?

Thanks.

Tyler

---

### Post by overdrank on 2008-04-21
> **1915flyer said:**
> I just installed Ubuntu 7.1. Afterwards, I changed the screen resolution. When I rebooted, the splash screen is OK, but when it gets to the username/password, I get about 4 images of the login screen, all interlaced and virtually unreadable. I can manage to login without reading what's on the screen but once the "desktop" is displayed, I can't do or read anything. Everything's fuzzy and 4 of everything. I suspect it is a screen resolution problem, probably too high.

Is there a way to boot into "safe mode" or force a video mode that will enable me to read the screen?

Thanks.

Tyler

Hi and you can try and use the ctrl, alt, F1 keys and reach the command line, login and use this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then use the command sudo reboot. What is the model of the graphics card?

---

### Post by 1915flyer on 2008-04-21
The video card is an ATI Rage 128 (I believe). No problems before I screwed up the refresh rate. When I selected my monitor, I didn't notice that the refresh rate went to 85hz and needed to be 75 or 60.

Your solution got me back into a readable login and desktop and I was ablle to fix the problem.

Thanks.  :popcorn:

---

