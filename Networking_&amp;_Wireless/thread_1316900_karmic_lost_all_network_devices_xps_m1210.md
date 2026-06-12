---
title: "karmic lost all network devices xps m1210"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by xboxbman on 2009-11-06
I just updated to Karmic on my XPS M1210 laptop this morning, and upon reboot, i have lost all network devices. Under Hardware drivers, it lists the broadcom STA wireless driver, sasy it is activated, but not currently in use.  my wireless card is a broadcom BCM4328 a/b/g/n rev 01, and my network adapter is a broadcom BCM4401-B0 rev 02.

ifconfig only shows lo, which is useless, and iwconfig shows lo no wireless extensions

any ideas how i get them to reappear?

EDIT:  I selected Keep current menu.lst, which effed everything up.  I updated grub and everything is great now

---

### Post by xboxbman on 2009-11-06
> **xboxbman said:**
> I just updated to Karmic on my XPS M1210 laptop this morning, and upon reboot, i have lost all network devices. Under Hardware drivers, it lists the broadcom STA wireless driver, sasy it is activated, but not currently in use.  my wireless card is a broadcom BCM4328 a/b/g/n rev 01, and my network adapter is a broadcom BCM4401-B0 rev 02.

ifconfig only shows lo, which is useless, and iwconfig shows lo no wireless extensions

any ideas how i get them to reappear?

After deactivating and reactivating the sta driver, the wireless now works, but the wired connection is still absent.  All help is greatly appreciated.

---

