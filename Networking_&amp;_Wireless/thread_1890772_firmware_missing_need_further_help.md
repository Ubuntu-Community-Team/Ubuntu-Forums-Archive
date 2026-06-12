---
title: "firmware missing need further help"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by ke4qfb on 2011-12-04
I have gone through the forum and have found no answers. This was easy to fix on 11.4, I just might have to drag this tower case to the router and hard wire it for updates and to see if it can fix it self.:confused:

my system:  01:0b.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329](rev 01)
Subsystem:Linksys Device[1737:0060]
Flags: bus master, fast devsel, latency 32,irq16
Memory at e5004000 (32-bit, non-prefetchable) [size=16k]
Kernel Driver in use:b43-pci-bridge
Kernel modules:ssb

---

### Post by 2F4U on 2011-12-04
If you want to check for additional drivers through the Ubuntu utility, you would need a working internet connection, if that is your question.

---

### Post by ke4qfb on 2011-12-04
.

---

### Post by bluexrider on 2011-12-04
There are answers out there. I got 24 threads in [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) 

> **ke4qfb said:**
> I have gone through the forum and have found no answers. This was easy to fix on 11.4, I just might have to drag this tower case to the router and hard wire it for updates and to see if it can fix it self.:confused:

my system:  01:0b.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329](rev 01)
Subsystem:Linksys Device[1737:0060]
Flags: bus master, fast devsel, latency 32,irq16
Memory at e5004000 (32-bit, non-prefetchable) [size=16k]
Kernel Driver in use:b43-pci-bridge
Kernel modules:ssb

Broadcom does have driver issues


Hope one of them helps

---

### Post by praseodym on 2011-12-04
Hi,

for this device you need the Broadcom-STA-driver. Install it via "jockey" (additional drivers) and a working wired connection. Without connection, install the packages dkms, patch, fakeroot, and bcmwl-kernel-source from the instalaltion CD by double clicking them.

---

### Post by ke4qfb on 2011-12-04
[QUOTE=praseodym;11513218]Hi,

for this device you need the Broadcom-STA-driver. Install it via "jockey" (additional drivers) and a working wired connection. Without connection, install the packages dkms, patch, fakeroot, and bcmwl-kernel-source from the instalaltion CD by double clicking them.[/QUOTE

Is it the same if I'm installed from a usb drive, because i cannot get wired network to work either.
thanks

---

