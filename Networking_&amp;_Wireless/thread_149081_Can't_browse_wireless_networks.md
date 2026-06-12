---
title: "Can't browse wireless networks"
date: 2006-03-23
forum: Networking &amp; Wireless
---

### Post by peschkaj on 2006-03-23
I have a Linksys Instant Wireless card (WPC11 version 3) and on my XP laptop it is capable of scanning for available wireless networks.  However, when I plug it into my linux laptop (Dell Latitude c800) network-manager tells me that this card is not capable of scanning for networks.

The card appears as device eth1, does this have anything to do with it, or is there a different aspect of the wireless configuration that I have missed?

Thanks,

jeremiah

---

### Post by peschkaj on 2006-03-24
Is it possible that this situation could be fixed by using ndiswrapper instead of the orinoco drivers?

---

### Post by Yimmy on 2006-03-29
I'm experiencing the same problem.  Any thoughts here?  Does anybody have the ability to scan for networks using the linksys WPC11 ver 3 card?  I can hard code everything in, but it won't scan.  Is it a card issue or a driver issue?  Surely the card has the ability to scan?

James

---

### Post by peschkaj on 2006-03-29
The card itself can scan under Windows XP, but I'm not sure what the issue under Linux is.  The drivers page lists the card as using the Prism/Intersil chipset, but the driver that gets loaded is the orinoco/orinoco_cs driver.  When I've attempted to configure the prism drivers, I can't even get the card to show up, so I'm not sure what the issue is.

---

