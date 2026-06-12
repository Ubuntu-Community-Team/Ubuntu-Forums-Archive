---
title: "pci id grabber script for wireless (need feedback/help)"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by Zelut on 2006-02-22
I've put together a very basic script that grabs the appropriate pci id for wireless cards.  I think this could be helpful for newbies trying to get wireless to work but aren't terribly comfortable sorting thru output from lspci, dmesg, etc.

I would like some feedback from other machines/hardware to know the most effective strings to search for.  If anyone has a second, could you post the appropriate output from your lspci/dmesg/lsusb, etc?  (example output from my machine below).  

NOTE: I mainly need feedback for finding listings using methods OTHER THAN 'lspci/lsusb/dmesg | grep 802.11'

easy search (lspci | grep 802.11)
> 0000:00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


hard search ('unknown device' is the difficulty)
> 0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)


Cheers

---

