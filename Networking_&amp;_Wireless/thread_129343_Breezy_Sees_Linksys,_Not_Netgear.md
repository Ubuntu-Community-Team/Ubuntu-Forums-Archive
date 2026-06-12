---
title: "Breezy Sees Linksys, Not Netgear"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by ORF1000 on 2006-02-13
I have no trouble running my Linksys WPC54GS PCMCIA card (wireless g), but when I tried to add my Netgear WG111T (also wireless g) using the networking tools, Breezy won't recognize the dongle at all.  The "Wireless Network Drivers" tool made a "netwg11t" configuration using the Windows CD, and placed the drivers in an /etc/ndiswrapper directory alongside a directory for the Linksys card.  However, nothing shows up in "Networking."

I got the drivers from a folder on the CD labeled "ndis5" which seemed to be Linux oriented.

It seems that ndiswrappers is configured and working fine, otherwise the Linksys card wouldn't work.  But it won't recognize the device on the USB port.  

Before upgrading from Hoary to Breezy, my MA111 (wireless b) worked fine alongside the Linksys PCMICA card.

One thought -- the USB port is 1.1, but the wireless device is designed for USB 2.0.  Could this be the problem?  I'd think it would be backward compatible.

Any ideas would be appreciated.

Dave

---

### Post by ORF1000 on 2006-02-13
Update -- I tried using a different driver from the CD -- athfmwdl.  Now, at least, the "Wireless Network Drivers" tool reports "Hardware Present: Yes."  But nothing shows up in the "Network Settings" tool.  (Well, eth0 shows up, and if I put the PCMCIA card in, it'll show up too.)

Any help would be appreciated.

Dave

---

