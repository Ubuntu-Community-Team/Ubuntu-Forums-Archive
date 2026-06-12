---
title: "Ubuntu doesn't recognise an atheros chipset"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Noentry on 2009-01-06
Hey,

I've just installed ubuntu 8.10 on my laptop. The laptop has a SB600 chipset + atheros wireless chipset. But ubuntu doesn't recognise it. What should I do? I need a madwifi driver there... I googled out that madwifi is in ubuntu by default, so what's wrong?

---

### Post by timcredible on 2009-01-06
try using ndiswrapper (ndisgtk) - that works on my friend's hp laptop.  also, installing linux-backports worked for another friend's toshiba laptop.

---

### Post by Noentry on 2009-01-06
*-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

Some details.

I can't use that driver because of the monitor mode. I need a driver with monitor mode. On Backtrack everything works just fine, in Mint I got it working with ndiswrapper, but I need madwifi. I tried installing it in Mint, but I gave up and got back to Ubuntu.

---

### Post by superprash2003 on 2009-01-06
try this.. hope it helps [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

