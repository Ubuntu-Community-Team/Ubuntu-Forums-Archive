---
title: "PCI-E X 1 nic."
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by Phoenixxl on 2012-03-02
Hi !

I'm setting up a new server which doesn't have pci slots .

The shop I go to has 3 options :

Broadcom NetXtreme Gigabit Ethernet Plus NIC
[http://h30094.www3.hp.com/product.asp?sku=3893162](http://h30094.www3.hp.com/product.asp?sku=3893162)
(Needs 1 week to order)

Intel Gigabit CT Desktop NIC
[http://h30094.www3.hp.com/product.asp?sku=3983653&mfg_part=FH969AA&pagemode=ca](http://h30094.www3.hp.com/product.asp?sku=3983653&mfg_part=FH969AA&pagemode=ca)
(available now)

Killer 2100
[http://www.killergaming.com/solutions/Network_Cards](http://www.killergaming.com/solutions/Network_Cards)
(available now)

That last one , looking at the site , doesn't seem to have any linux drivers for it , and on the ubuntu forums I can only find 1 thread.. It could be supported by now but I have no idea...

So which would give me the least problems running in Oneiric? (my main concern)

Any other comments on these cards are very welcome as well.

Kind regards
Phoenixxl

---

### Post by Phoenixxl on 2012-03-02
If anyone can provide a few links to pci-e X1 adapters they know do work well that would be appreciated as well, though I am hoping for a reply from someone who has experience with the ones I know I can get.

---

### Post by amuh on 2012-03-02
I know that Intel Gigabit CT Desktop NIC works on Ubuntu, i'm running it on a Ubuntu server. In my case the file transfer to the server is slow through that nic, but it might be something else than the nic thats causing that.

---

### Post by chili555 on 2012-03-02
Here is the Intel: [http://h30094.www3.hp.com/product.asp?sku=3983653&mfg_part=FH969AA&pagemode=ca](http://h30094.www3.hp.com/product.asp?sku=3983653&mfg_part=FH969AA&pagemode=ca)

As you can see here, it uses the quite reliable module *e1000e*: [http://cateee.net/lkddb/web-lkddb/E1000E.html](http://cateee.net/lkddb/web-lkddb/E1000E.html)> vendor: 8086 ("Intel Corporation"), device: 10f6 ("[COLOR="Red"]82574L[/COLOR] Gigabit Network Connection")I believe it will work out of the box.

The Broadcom uses the module *tg3* and also should work perfectly. Here is a reference: [http://ubuntuforums.org/showthread.php?t=1740738](http://ubuntuforums.org/showthread.php?t=1740738)> *-network
description: Ethernet interface
product: [COLOR="Red"]NetXtreme BCM5761e[/COLOR] Gigabit Ethernet PCIe
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
logical name: eth0
version: 10
serial: f0:4d:a2:86:fd:5d
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=tg3 [/COLOR]driverversion=3.116 duplex=full firmware=5761e-v3.73 ip=***.***.***.*** latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:43 memory:f2d10000-f2d1ffff memory:f2d00000-f2d0ffff

I have only found questions about the Killer; no answers.

I suggest you select the Intel and be happy. This laptop I'm answering on uses an Intel ethernet NIC and *e1000e* without drama.

---

### Post by Phoenixxl on 2012-03-03
I got one of those intel ones. 

Thnx for the reply.

---

