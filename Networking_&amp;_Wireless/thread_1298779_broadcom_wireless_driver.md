---
title: "broadcom wireless driver"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by m1d4s on 2009-10-23
Please help me find the driver for
Broadcom Corporation:BCM4306 802.11b/g Wireless LAN Controller: Wireless 1350 WLAN Mini-PCI Card

---

### Post by t0mppa on 2009-10-23
[B43]("http://linuxwireless.org/en/users/Drivers/b43") (or b43legacy depending on the revision) supports it and is probably there by default. You'll have to install the firmware though, since that's not open source (unless you use the one from [OpenFWWF]("http://www.ing.unibs.it/openfwwf/")).

---

### Post by kevdog on 2009-10-23
what revision # is your 4306 card?

check lspci -nnm

---

### Post by m1d4s on 2009-10-23
> **t0mppa said:**
> [B43]("http://linuxwireless.org/en/users/Drivers/b43") (or b43legacy depending on the revision) supports it and is probably there by default. You'll have to install the firmware though, since that's not open source (unless you use the one from [OpenFWWF]("http://www.ing.unibs.it/openfwwf/")).
i  went on the openFWWF website but but i don't understand what to do then
 
sorry i'm a true newbie  :p

---

### Post by bkratz on 2009-10-23
> **m1d4s said:**
> Please help me find the driver for
Broadcom Corporation:BCM4306 802.11b/g Wireless LAN Controller: Wireless 1350 WLAN Mini-PCI Card




Here is some pretty good info.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Good Luck!

---

### Post by t0mppa on 2009-10-24
> **m1d4s said:**
> i  went on the openFWWF website but but i don't understand what to do then
 
sorry i'm a true newbie  :p

Well, open source isn't really a necessary requirement on Linux, most people use the proprietary firmware, fust put the notice there, in case you'd be willing to go the extra mile (it really isn't rocket science) and try it out.

Before any of that though, did you read through the b43 page? You need to figure which revision of the chip you have, since that determines whether you use b43 (rev 03) or b43legacy (rev 02) and thus which version of firmware you need. Or if you're lazy, I suppose you can simply install both versions like the link bkratz provided instructs.

---

