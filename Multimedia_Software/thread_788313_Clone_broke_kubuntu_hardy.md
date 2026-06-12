---
title: "Clone broke kubuntu hardy"
date: 2008-05-09
forum: Multimedia Software
---

### Post by zcwalton10 on 2008-05-09
I tried to set up a hardware KVM switch so I can switch between XP and kubuntu hardy (32-bit).  Everything was working fine, other than the monitor.  So I found my way into the settings in kubuntu, selected the "clone" option, logged out, and chose to restart Xwindow.

Now it freezes, whether it's connected to the other monitor or not, every time it gets to "Running boot scripts...  /etc/rc.local [OK]"

This is pretty frustrating, since I wouldn't really expect cloning a monitor to break the system.  Anyone have any ideas?

---

### Post by blastfm on 2008-05-22
I'm not sure if this is the same issue, but I enebaled Cloning of video so I can see the same thing on two separate monitors at the same time. Everything worked OK except whenever I re-start my system, it just hangs. Shutting down is no problem, haven't tried Hibernate or sleep yet, but obviously re-start is messed up.

My video card is an on-board Nvidia 6150 with VGA and DVI output and I used the NVIDIA X Server Settings (/usr/bin/nvidia-settings) tool to get clone to work and modify the xorg.conf

---

### Post by blastfm on 2008-05-27
Anyone? This is getting to  be a pain especially when updates come in requiring a re-start. System would shutdown successfuly but when the re-start begins, it just freezes. I have to power down my PC and power it up again.

---

