---
title: "jocke-gtk wont list b43 driver"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by mrfsrf on 2010-01-11
Hi all,

Im using HP mini with Broadcom wireless chipset. Currently STA drivers are installed and working, however i want to install alternative wireless driver (b43-fwcutter) to be able to enter monitor mode (which this driver is capable of) for using it in wireshark and kismet.

Now, jockey-gtk isn't listing it although i installed it using 
'sudo apt-get install b43-ffwcutter'. Why is that?

here is the output of sudo jockey-gtk -l
kmod:wl - Broadcom STA wireless driver (Proprietary, Enabled, In use)

i also tried sudo jockey-gtk -u (for updating driver databse but got same query)

does anyone know solution to this. thanks in advance!

---

### Post by mrfsrf on 2010-01-11
here i the list for network adapter

*-network
***************description: Wireless interface
***************product: Broadcom Corporation
***************vendor: Broadcom Corporation
***************physical id: 0
***************bus info: pci@0000:08:00.0
***************logical name: eth1
***************version: 01
***************serial: 00:26:82:1b:c0:0b
***************width: 64 bits
***************clock: 33MHz
***************capabilities: bus_master cap_list ethernet physical
wireless
***************configuration: broadcast=yes driver=wl0
driverversion=5.10.91.9 ip=10.0.1.6 latency=0 multicast=yes
wireless=IEEE 802.11
***************resources: irq:16 memory:e8000000-e8003fff




**eth1 ***Link encap:Ethernet *HWaddr 00:26:82:1b:c0:0b *
*********inet addr:10.0.1.6 *Bcast:10.0.1.255 *Mask:255.255.255.0
*********inet6 addr: fe80::226:82ff:fe1b:c00b/64 Scope:Link
*********UP BROADCAST RUNNING MULTICAST *MTU:1500 *Metric:1
*********RX packets:10676 errors:5 dropped:0 overruns:0 frame:18284
*********TX packets:11631 errors:6 dropped:0 overruns:0 carrier:0
*********collisions:0 txqueuelen:1000 
*********RX bytes:8297208 (8.2 MB) *TX bytes:2056069 (2.0 MB)
*********Interrupt:16

---

