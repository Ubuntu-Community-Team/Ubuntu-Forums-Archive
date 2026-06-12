---
title: "Wireless broadcom adapter in ubuntu 8.10"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by edcol on 2009-05-22
My wireless broadcom adapter model bcm4311 rev 1 does not work in ubuntu 8.10.
I have a laptop Lenovo model 0768. 
The test says that "this driver is activated but not currently in use".
What should I do to have wireless connection? Could anybody help me?

---

### Post by Ayuthia on 2009-05-22
> **edcol said:**
> My wireless broadcom adapter model bcm4311 rev 1 does not work in ubuntu 8.10.
I have a laptop Lenovo model 0768. 
The test says that "this driver is activated but not currently in use".
What should I do to have wireless connection? Could anybody help me?

Have you tried activating the driver by going into System->Administration->Hardware Drivers and activate the Broadcom STA option?  The 4311 rev 01 chipset should work pretty well with it.  If you want to use the open source version, you will need to select the Broadcom b43 option and you will need a working internet connection in Ubuntu to make it work because it will need to download some firmware to make it work.

---

### Post by superprash2003 on 2009-05-22
if you still face issues [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

