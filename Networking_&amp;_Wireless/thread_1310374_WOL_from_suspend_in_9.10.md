---
title: "WOL from suspend in 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by jedavids on 2009-11-01
I have been trying to get WOL from suspend to work without any success.  I am using an intel PCI NIC and am able to WOL from shutdown if I configure ethtool as follows:

sudo ethtool -s eth1 wol u

WOL from suspend however will not work.  I have tried various things as described by a large number of threads on this topic but to no avail.  In looking at the dmesg output for the suspend, I see the following relating to the ethernet driver:

[131115.374194] e1000 0000:05:00.0: PCI INT A disabled
[131115.374201] e1000 0000:05:00.0: PME# enabled

Does this indicate that the NIC is not left fully enabled?  Anyone have experience with these message?  FWIW, my NIC lights stay on during the suspend.

Thanks,
Jeff

---

