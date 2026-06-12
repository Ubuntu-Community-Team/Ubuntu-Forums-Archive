---
title: "Terrible wifi connection with 12.04"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by tehwizardd on 2012-08-31
I have 100 Mbps link and I get only 1Mbps tops, usually half of that and it's not stable.

I have HP G5000 laptop, wich has broadcom wifi, but this is not working. I accendently did cut the wire.. Oops. 

But, I have Buffalos, little tiny N standard USB wifi. Ubuntu tells me that it's ralink. EDIT: It's Ralink usb 3070

```
$ lsusb | grep Ralink
Bus 001 Device 002: ID 0411:015d BUFFALO INC. (formerly MelCo., Inc.) WLI-UC-GN Wireless LAN Adapter [Ralink RT3070]

```Could this be driver issue, the usb wifi is bought 2010, so it's not new hardware.

Any tips?

Otherwise Ubuntu 12.04 with Gnome 3 is running fine. It's bit heavy, but alright for this light use. I just need to get that wifi working.

Ohh, and with other PC the connection was just fine.

Disabling IPv6 is not helping.

---

### Post by tehwizardd on 2012-09-01
Anyone??

---

### Post by tehwizardd on 2012-09-01
Alright, updated kernel to 3.4.0 and card seems to be working better. I got up to 48 Mbps wich is around same with W7 PC. But connection still is tricky, it can suddenly start dropping really low and then soon boost back up.

---

### Post by tehwizardd on 2012-09-03
Could this waving kind of behaviour be related of having many access points at same channel?

---

### Post by kurt18947 on 2012-09-03
> **tehwizardd said:**
> Could this waving kind of behaviour be related of having many access points at same channel?

I know that having many wifi networks on the same channel can cause problems, yes.  If you're using your own router, you may be able to change the channel on the router.  Your wifi adapter will use that channel.  In the U.S. channel 6 seems to be the most popular so you could try channel 1 or channel 11.  I have mine set to 'auto' and get a good consistent signal.

---

