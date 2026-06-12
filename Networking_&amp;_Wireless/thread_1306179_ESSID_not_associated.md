---
title: "ESSID not associated"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by MarcoPau on 2009-10-30
Hello, just dist-upgraded to karmic and iwconfig says wlan0 is not associated to my essid NETGEAR.

I've got an ASUS wl-138g with Marvell W8300 chipset which has always been working with ndiswrapper 1.55. Even tried recompiling and reinstalling the driver but no result.

Lspci shows it correctly, ndiswrapper -l says drivers installed and hardware present. Iwconfig wlan0 essid "NETGEAR" done manually won't have any effect.

Iwlist scan detects the ESSID.

Any hint?

TIA

---

### Post by MarcoPau on 2009-10-30
Uninstalling networkmanager solved the problem.

Thanks all the same

---

