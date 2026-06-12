---
title: "Switching between single/dual-head/big-desktop modes"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by djf on 2006-10-10
I'm using the fglrx driver. All my configs have been mostly created automatically by aticonfig and work reliably.

Is there an easy way to have single-head, dual-head and big-desktop configured in a single xorg.conf? And more importantly I'm looking for an easier way to switch between these modes. 
Right now, I've got three different xorg config files, one for each mode. If I want to use big-desktop, for example, I symlink the big-desktop config file to /etc/X11/xorg.conf and restart the X server. 
This works ok, but since I have to restart X I'm forced to close all my programs. Does someone know a better alternative?

TIA, djf

---

### Post by wieman01 on 2006-10-10
As far as I can tell, there is no other way than you have described. I am using "Xinerama" and have to do exactly that every time I connect my projector or external display. I am afraid you'll have to live without such functionality.

But perhaps there is a person out there that's smarter than we are. :-)

---

