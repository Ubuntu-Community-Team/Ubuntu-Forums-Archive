---
title: "Upgrade to Natty Beta 2 Broke My Wireless"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 1roxtar on 2011-04-24
Wireless Card: (PCI) Dynex DX-WGPDTC

This PCI wireless card worked flawlessly and out-of-the-box with Ubuntu 10.04 and 10.10.  I did an upgrade to Natty Beta 2 via LiveCD with no internet connection.  Everything works fine but since the upgrade, my computer no longer sees my wireless card.  I've tried the Additional Drivers but will not pick it up.  I've even installed the Broadcom drivers through Synaptic.  Still nothing.  It detects and connects wifi with my USB dongles (Netgear and Linksys) but I can't get my computer to see my PCI card anymore.  

:(

---

### Post by Elfy on 2011-04-24
moved to natty

---

### Post by arpanaut on 2011-04-24
Try this thread from post #14 on it seems to work for many with that wifi adapter.
Hope it helps.  It is working for me.

[http://ubuntuforums.org/showthread.php?t=1700897&highlight=broadcom&page=2](http://ubuntuforums.org/showthread.php?t=1700897&highlight=broadcom&page=2)

---

### Post by 1roxtar on 2011-04-24
Ugh!!!  I could kick myself....

The fix was so easy.  I uninstalled everything broadcom through Synaptic and just installed "firmware-b43-installer" which installed "b43-fwcutter" and Voila! I got my wireless back.

---

