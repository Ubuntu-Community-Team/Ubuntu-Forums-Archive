---
title: "SUPORT FOR AR242x 802.11abg Wireless PCI Express Adapter IS REQUESTED"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Nitrozzy7 on 2008-12-30
Hello I have an acer 5715z it's a 32 bit processor and I've installed ubuntu 8.10. I've posted before but I didn't had any lack. Please help me!!!!!!!!!!!!!!!!!!!!

---

### Post by 67GTA on 2008-12-30
Go to Menu>System>Administration>Hardware Drives. De-activate the driver for Atheros. Put in your 8.10 CD and add it as a repository. Then install ```
linux-backports-modules-intrepid-generic
``` from the CD. Go back to hardware drivers and make sure the new "5xxx" atheros driver is enabled and reboot.

---

