---
title: "Loss of Wireless After a Couple of Hours"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by biomedtek on 2010-03-08
I have a hp dv3 laptop which dual boots Win7 and Ubuntu 9.1 64 bit. I have no issues with my wireless adapter in Win7, but I lose connection after a couple of hours in Ubuntu. When connection is lost it is not possible to view any wireless signals, the adapter is basically turned off. The only way to restore the connection is to reboot, then Ubuntu will again automatically connect to my WP2 encrypted router.
My wireless adapter is a AR928X made by Atheros.
Does anyone have any ideas on this issue?

---

### Post by Sonic Boom on 2010-03-08
Im having pretty much the exact same problem

---

### Post by kb1 on 2010-03-09
Yep same problem here, with the exact same network controller

anybody got any ideas?

---

### Post by cfurlin on 2010-03-09
I have the same issue with an Intel Link 5000AGN adapter. My wireless signal drops for no reason, but I have noticed that sometimes it doesn't completely drop but only loses my WEP key. Rebooting fixes the issue without re-entering the key.

None of this happens on Windows, BTW.

---

### Post by coffeecat on 2010-03-09
> **biomedtek said:**
> My wireless adapter is a AR928X made by Atheros.
Does anyone have any ideas on this issue?

Yes, very easy fix.

Open Synaptic and install the packages:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

...and reboot.

Or, if you prefer the terminal:

```
sudo apt-get install linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic
```

...and reboot.

This installs a number of updated drivers, including the Atheros one for this chipset. You'll find it much more stable. I'm posting from a machine running Ubuntu with the AR928X chipset. It's working just fine. :wink:

---

