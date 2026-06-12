---
title: "Broadcom BCM4312 .inf issue"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by peteypeppep on 2010-01-24
I'm trying to get my wireless lan to work but the only thing holding me back is my inability to find the driver for the Broadcom BCM4312 in .inf format. Any suggestions?

---

### Post by bkratz on 2010-01-24
> **peteypeppep said:**
> I'm trying to get my wireless lan to work but the only thing holding me back is my inability to find the driver for the Broadcom BCM4312 in .inf format. Any suggestions?

Obviously you are trying to use ndiswrapper.  Did you try the native driver STA and not have luck?

Here is the link just in case

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by efflandt on 2010-01-25
Under Hardware Drivers, activating Broadcom STA should work for BCM4312 (if you have a temporary ethernet connection), or otherwise temporarily checking the box add install CD to Synaptic sources and installing bcmwl-kernel-sources.

However, if you are using Ubuntu iso from bootable USB (USB Startup Disk Creator), it does not load automatically.  After you reboot you may have to do sudo modprobe wl.  But for a "regular" installation, even to USB flash or external drive, the wl module should load automatically (once Broadcom STA has been activated).

Something peculiar to new Dell laptops is that the function keys work in reverse of normal, so it is easy to accidentally toggle wireless hardware off and there is no LED to tell you on/off.  For example if F2 key shows a radio tower, just pressing F2 toggles wireless on/off, but if you actually want to enter F2 you have to press Fn+F2.

---

