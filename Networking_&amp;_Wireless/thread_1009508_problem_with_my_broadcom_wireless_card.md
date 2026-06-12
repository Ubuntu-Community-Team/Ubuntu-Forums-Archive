---
title: "problem with my broadcom wireless card"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by abu-sakaria on 2008-12-12
Hi 

I've followed many different toturial here from the forum, than followed the hardware search in hardy it asked for the installation cd .. but then this message came: 

> W: Failed to fetch cdrom:[Ubuntu 8.04.1 _harry Heron_ - Release i386 (20080702.1)]/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb

What do I do now?

---

### Post by Ayuthia on 2008-12-12
You can open up your cd and go to pool/main/b/b43-fwcutter/.  There should be a file called b43-fwcutter_011-1_i386.deb.  Copy the file to your Desktop then go to the Terminal and do the following:
```
cd ~/Desktop
sudo dpkg -i b43-fwcutter_011-1_i386.deb
```
That should install the package for you.

---

