---
title: "screen resolution"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by krishnath on 2006-06-24
hi,i'm new user 4 ubuntu.i installed newest version of ubuntu.but my motherboard is intel D101GGC.so the chipset couldnt support for screen resolution.now my default resolution is 640*480.

**[SIZE="5"]"how can i change the screen resolution?"[/SIZE]**

pls give me a easy way.

---

### Post by RESmonkey on 2006-06-24
Open xorg file:

(IN terminal) sudo gedit /etc/X11/xorg.conf
Go to Monitor section

add

HorizSync *-*
VertRefresh *-*

Replace the *'s with the correct numbrs (search your monitor's potential).  
 Also, make sure you have the correct resolutions per depth option in that file.  Don't remove any.  Just add if you want.

EDIT= MAKE SURE YOU REBOOT AFTER.  To have the changes...

Hope it helps.

---

### Post by jonny on 2006-06-24
There is an easier way that almost always works.  Simply type ```
sudo dpkg-reconfigure xserver-xorg
``` in a terminal session and answer the questions.  If that still fails, try installing the package 915 resolution (this is a special tool that's only appropriate for Intel graphics solutions) and run the configuration script again.

Dpkg-reconfigure is the best solution for any Debian based linux system like Ubuntu.  It's the official way to configure the system and, if you use it, your answers are much more likely to survive upgrades.  Note that many other packages have dpkg-reconfigure scripts to get you on your way.

---

### Post by jonny on 2006-06-24
Note that RESmonkey's warning about rebooting still applies.  There are ways to get around the rebooting requirement, but that's a tutorial for another day.

---

