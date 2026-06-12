---
title: "Lost Atheros wireless support in Hardy with kernel 2.6.24.23"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by mfox on 2009-02-08
I have lost support of my wireless card (Atheros 242x in Gigabyte b/g) with the latest kernel upgrade in Hardy, and I haven't been able to figure out how to activate it.  Ubuntu is supposed to provide native support for this card, and it has up until this latest upgrade.  When I look for the driver under the Hardware Drivers administration panel, it shows the Atheros driver, but not enabled.  I have tried to enable it by checking the box, but the box won't check and nothing happens.  When I examine the network with lshw, it lists the wireless controller, but the configuration is latency=0 and with the network unclaimed.  Going back to the previous kernel (2.6.24.22), everything is as it should be and the wireless works.  Is there something I can do to enable the driver, or am I best off to assume this is a bug and stick with with 2.6.24.22 until it's fixed in the next kernel upgrade?

Note: I have Ubuntu Intrepid installed on the same laptop (MSI Wind), and the card has been detected by every kernel upgrade.

---

