---
title: "Wireless disabled"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by pollian on 2006-06-05
In trying to troubleshoot my wireless configuration (under Dapper Server), I ran lshw and got two network items

*-network
description: Card
product: ISL37300P
vendor: NETGEAR MA401RA Wireless PC
physical id: 0
version: Eval-RevA
slot: Socket 1
resources: irq:4

*-network DISABLED
description: Wireless Interface
physical id: 1
logical name: eth1
serial: 00:09:5b:26:b3:4b
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.6 link=no multicast=yes wireless=IEEE 802.11b

Why, in the first place, are there two entries for the same card (00:09:5b:26:b3:4b is the MAC address of the MA401)? And why, beyond that, is one of them disabled? Any suggestions on how I might correct this?

pollian

---

### Post by pollian on 2006-06-06
Some Further Information.

I ran an lsmod and noticed that hostap_cs and orinoco_cs were both running. I have in the past been able to get this card working in other distros by making it bind to orinoco_cs rather than hostap_cs (which for some reason seems to be the default.)  In this case, I added hostap_cs to /etc/modprobe.d/blacklist so that it wouldn't run at startup. Unfortunately, that didn't fix the problem. Hostap_cs doesn't load--and orinoco_cs does--but I still get the two network entries from lshw (as above), and one of them is still disabled.

Any thoughts?

---

