---
title: "Ethernet card doesn't work. Wireless does."
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Athunye on 2009-07-20
Notebook Acer Aspire 5516
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

ifconfig shows only eth0 and lo.
Broadcom BCM4312 is the wireless card, wich is recognized as eth0.
I know that because if I moprobe -r wl (the module for this card),
or ifconfig eth0 down, the wireless connection stops.

Attansic Techonology is the ethernet card, for the wired network. This
one is not working. I have read that atl1e is the module for this card, but I am not sure if it really is the correct module for this card...
atl1e is not loaded at boot time. It does not show up in lsmod.
If I modprobe atl1e, nothing happens. The card does not "wakes up".


nando Fri Jul 17 16:35:57 ~ $ 
bash >>> modprobe -l | grep atl
kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/input/misc/atlas_btns.ko

modinfo atl1e (just the relevant part)
filename:       /lib/modules/2.6.28-13-generic/kernel/drivers/net/atl1e/atl1e.ko
version:        1.0.0.7-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Atheros Corporation, <xiong.huang@atheros.com>, Jie Yang <jie.yang@atheros.com>

ATHEROS ??? I don't understand... I have read that in Windows, this card
shows up as atheros and in Linux as attansic.

I'm really lost. I'm out of ideas. Any help is welcome.

---

### Post by hawkbane47 on 2009-07-20
I have the exact same problem on  my vostro 1500, my wireless is recongized as eth0 and no ethernet.....I've seen several forums on this type of thing, it seems to be a regression from hardy/intrepid

---

### Post by Athunye on 2009-07-20
Why do you mean "regression"? Did it work in those versions of Ubuntu ?

---

