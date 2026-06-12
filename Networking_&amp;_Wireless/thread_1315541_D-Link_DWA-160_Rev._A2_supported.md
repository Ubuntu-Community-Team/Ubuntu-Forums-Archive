---
title: "D-Link DWA-160 Rev. A2 supported?"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by honestguvnor on 2009-11-05
I bought a D-Link DWA-160 today having looked up here to see that it is supported:

[http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)

but it failed to work when plugged in.

It has Rev. A2 on the box and identifies itself as 07d1:3a09. Googling this identifier leads to:

[http://dpkg.vireo.org/factoid.php?key=dwa160](http://dpkg.vireo.org/factoid.php?key=dwa160)

which suggests it is new hardware that has already been spotted.

Can someone confirm for certain that it is unsupported?

Or point me at some recent code to build that might work?

---

### Post by sonicb00m on 2009-12-05
I'm also keen to get support for this stick. If you get anywhere please post back here.

---

### Post by Zero79 on 2010-01-13
I bought also this usb stick and cannot get it to work. There's a patch in wireless driver and comment that the device works: [http://patchwork.kernel.org/patch/60613/](http://patchwork.kernel.org/patch/60613/)

I compiled latest compat-wireless (2009-12-11 which includes this patch) on top of 9.10 (2.6.31-17-generic), but there's still no life in the stick. dmesg/syslog shows that it is connected, but the driver is not loaded. If I modprobe ar9170usb manually, it doesn't even try to load the firmware, so apparently something is missing still from my system.

Device works fine under Windows, so it is a working unit.

---

### Post by Zero79 on 2010-01-13
Ok, I got it working after all. For some reason there was old version of ar9170usb.ko in updates/cw which didn't have the USB id for the A2 version. After deleting the old modules and reinstalling the compat-wireless package the device is now recognized and both 2.4GHz and 5GHz modes works.

The driver doesn't support yet the n-mode, so maximum speed is 54Mbps and for some reason I need to manually set that with iwconfig. Otherwise the mode is 6Mbps and actual speed when copying files from other computer was just about 600kBps. When I set the rate to 54M I get transfer speed about 3MBps which is ok for me now.

---

### Post by Leo_Alexander_Gesvantner on 2010-01-16
I also have a DWA-160 wireless USB adapter from D-Link and I was wondering if anyone has had any success with using it through ndiswrapper?  I am a Linux noob and I don't yet know how to operate ndiswrapper or the terminal.

---

### Post by Zero79 on 2010-01-18
I tried ndiswrapper, but it didn't work at least with the drivers that can be obtained from D-Link's website. There was some symbol lookup errors while loading the driver.

---

### Post by gwikstrand on 2010-01-26
I would like to see this support without all the hassle of rebuidling the kernel...

---

