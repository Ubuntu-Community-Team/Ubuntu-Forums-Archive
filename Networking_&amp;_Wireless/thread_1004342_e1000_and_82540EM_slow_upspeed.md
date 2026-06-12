---
title: "e1000 and 82540EM slow upspeed"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by brujoand on 2008-12-07
Hi, 
I have a 82540EM card using version  7.3.20-k3-NAPI of the e1000 driver and my kernel is 2.6.27-9-server.
I am behind a 100Mbps switch. I used to have up and down speeds around 10MB/s, but now, my upload speed is no more then 400Kbps usually below 100. This has been the case for about 4 months now. But i still have the 10MB/s downloadrate. I have tested other computers behind the same switch, they still have the same up and down speed. I tried sending files from my computer to a nother computer behind the same switch, still no more then 400kbps. My computer has 2Gb of ram, and no real load what so ever.

sudo lshw -C network, gives me
...
*-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth1
       version: 02
       serial: 00:08:74:f5:xx:xx
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A ip=129.241.***.*** latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s


Any help is appreciated.

Anders

---

