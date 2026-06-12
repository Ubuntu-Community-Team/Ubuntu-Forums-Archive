---
title: "How do I Claim and Unclaimed Network Device?"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by jcb081584 on 2009-05-20
After digging around I think I've discovered that my wireless is not working because it is "Unclaimed" As shown here:

*-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list

Anybody know how to get it back?  If I can help it I don't want to use the NDISwrapper or the MadWiFi drivers but rather the drivers that came with Ubuntu 9.04.  I know they're there because it worked for about three weeks before I had problems.  And help would be appreciated.  Thanks in advance.

---

### Post by superprash2003 on 2009-05-20
try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by jcb081584 on 2009-05-20
> **superprash2003 said:**
> try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

I have done all those in the tutorial but with no success.  The only driver listed in the hardware drivers is the madwifi driver and trying to activate I get an error saying the device was just disabled but is still in use.  Any help would be much appreciated.

---

