---
title: "Ubuntu10.04 Wired network problem"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by sharethl on 2010-05-04
I installed Ubuntu10.04, It can not driver Wired network and wireless.

Later I installed linuxMint9, wireless is ok, but wired network doesn't work.

I am sure the lan cable is ok. It works in Windows.

How to solved it?

Thanks.

---

### Post by Iowan on 2010-05-04
From a terminal (Applications>Accessories>Terminal) **sudo lshw -C network** should (hopefully) reveal some information about your interface(s).

---

### Post by sharethl on 2010-05-06
I have interface information for my network card

>   *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:1d:10:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:41:50:0f
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)


---

### Post by Iowan on 2010-05-06
Nothing obvious...
Try (from a terminal):```
sudo dhclient eth0
```

If both interfaces access the same DHCP server, probably only one will get an address. Another option: turm off wireless and see if wired gets an address.

---

