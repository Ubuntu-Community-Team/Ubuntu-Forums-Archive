---
title: "Nvidia driver causing &quot;auto confiig&quot; message to repeat"
date: 2011-01-10
forum: Multimedia Software
---

### Post by JimGvo on 2011-01-10
I went into hardware drivers and selected the recommended driver for my nvidia card. I restarted the computer and got the login screen.  When I logged in, a box appeared saying "Auto config please wait".  The screen went blank a second later and came back with the same box.  It's still doing it, an hour later.  It appears to be stuck in a loop.  How do I get out of this?  I updated the driver trying to get opengl working.  My glxinfo command segfaults.  Can someone tell me how to get an nv driver to work with opengl?

Running 10.04 32 bit.  

 uname -a
Linux blackie 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

lspci | grep -i nvidi
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by JimGvo on 2011-01-10
Lesson learned, don't install the recommended driver.  I went back, destroyed the xorg.conf file that had been created and installed another driver.  It was version 173.  That made things work a bunch better.  I did have to adjust the resolution, however.  The default resolution left some of my desktop off the edge.  1600x900 fixed it however.

Jim.

---

