---
title: "Xserver not working..."
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by hatman on 2007-01-17
All my fault, I was toying with putting xgl/compiz on and totally messed up... tried the dpkg reconfigure and copying the xserver.xorg backup file over the top but still the xserver wont start.  

The error I get is

GDM: Xserver not found:  /usr/bin/Xgl :0 :0 -fullscreen -ac -accel
glx: pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth - nolisten
tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM.

I'm pretty certain that I edited gdm.comf-custom and told it to look for Xgl rather than Xserver (dunno tho') but I dont know if there's a way of editing files without the Gui up (I usually use gedit but it needs a Gui)... The problems are on my work machine as luck would have it and not my home PC... any assistance would be much appreciated...

---

### Post by simonsimon on 2007-01-17
This was my thread for a very similar issue:

[http://www.ubuntuforums.org/showthread.php?t=335691](http://www.ubuntuforums.org/showthread.php?t=335691)

The end result was I reinstalled.  Hopefully someone can find a solution for you.  I'd like to see it too in case this happens to me again.  ;)

---

### Post by hatman on 2007-01-18
Sorted... I *had* changed something in gdm.conf-custom. I managed to discover a text editor I could use after pressing Alt-Ctrl-F1 and logging in.  Editied out my changes, rebooted and did a dpg-reconfigue of xserver-xorg and am up and running again. Hope that helps someone...

---

