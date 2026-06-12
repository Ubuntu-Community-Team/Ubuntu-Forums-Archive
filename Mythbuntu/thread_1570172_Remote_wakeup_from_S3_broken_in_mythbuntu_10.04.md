---
title: "Remote wakeup from S3 broken in mythbuntu 10.04"
date: 2010-09-07
forum: Mythbuntu
---

### Post by bcully on 2010-09-07
Hi,

Up until I updated to mythbuntu 10.04, I could wake up my machine from S3 by pressing the power button on my remote (MCE, came with my Hauppage PVR-150). But this no longer works. Every single USB hub (USB0-USB3, USBE) is enabled for wakeup in /proc/acpi/wakeup, and if I physically unplug the IR receiver from the USB port, the system does wake up successfully. But the power button no longer has any effect when the system is asleep.

Any clues? Any other information I can provide?

Thanks!

---

### Post by slamhound on 2010-09-08
I think there was a bug in the kernel affecting wake from usb that was introduced a couple months ago. It might explain your problem.  Supposedly it is fixed but the fix hasn't made it into the ubuntu version yet.

Some detail here:

[http://forum.xbmc.org/showthread.php?t=76944](http://forum.xbmc.org/showthread.php?t=76944)

---

### Post by bcully on 2010-09-08
Thanks! That thread led me to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614632)

And the bug report contains:
> 
The issue has been adressed in the latest pre-proposed kernel 2.6.32-25.43~pre201008210902 from here: [https://launchpad.net/~kernel-ppa/+archive/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/pre-proposed)


That kernel does indeed fix the problem for me.

---

