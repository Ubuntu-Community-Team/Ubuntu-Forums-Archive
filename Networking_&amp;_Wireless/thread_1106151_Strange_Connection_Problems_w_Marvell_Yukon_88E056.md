---
title: "Strange Connection Problems w/ Marvell Yukon 88E056"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by kenotron on 2009-03-25
Background: a few days ago, I purchased an Asus M378A-T motherboard w/ an onboard Marvell Yukon 88E056 gigiabit ethernet card.  Ibex installed without a hitch, then the problems began.

When I boot into Intrepid, it is properly detected, and the GUI network manager shows that it has connected to the wired network.  I can select 'Connection info' and see that it acquired an IP address from the DHCP server, so I know that it *should* be working.  However, no network connections succeed: I can't ping the default gateway, DNS doesn't work, etc.

When I run 'ifconfig', it doesn't show an IP address for 'eth0', and it shows lots of TX and RX errors, so it appears that it's trying to send and receive data, but failing.  I see nothing in messages.log or dmesg to indicate hardware problems.  'route' shows no routes setup at all.  Something is amiss.

This card works great under ExpressGate and Windows (ugh), but not at all under Ibex.

I'm using the sky2 driver.  Other forum postings indicate problems with this driver not containing the PCI ID of other yukon-class cards, but my 88e056 is listed in 'modinfo sky2', and I'm getting an IP from DHCP, so I'm sure that's not the problem here.

Others have mentioned ACPI as the cause of the problem, preventing the card from receiving interrupts.  I have acpi=off in the kernel parameters, but it has no effect.

I have the source package for the sk98lin driver from marvell's website, but without net access I can't download the kernel source I need to compile it...I tried downloading the source '.deb' package from security.ubuntu.com, but then I just get header mismatch errors because I couldn't find precisely the same source package as my kernel (whatever the ibex default is 2.6.27-7-generic or something).

At this point I'm tending towards heading back to the store to find a cheap, well-supported PCI 10/100 ethernet card, so that I can download the updates necessary to compile the sk98lin driver, but even then there's no guarantee it would work, and I've had bad luck with incompatible network cards in the past, and I'd rather get this one working properly and save myself a PCI slot for the Next Big Thing (tm). 

So, this problem is complicated by the fact that I don't have net access in linux, and I have to go through a few dozen cycles of: boot into expressgate, download some deb's to a USB drive, boot into linux, try them out, fail, rinse, lather, repeat.  This was getting old a few days ago, right now it's just extremely frustrating.

Anyone have suggestions for me?  I hope I've provided enough information to identify the issue above, as it's rather troublesome for me to boot into linux to produce the output of lspci etc.

---

