---
title: "How do I connect to a wired LAN."
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by bwallum on 2010-02-28
Hi

I'm running 9.10 on a new build AMD64 platform. Well the motherboard is new. Existing hard drives including the 9.10 system were reconnected to the new mb. Everything fired up nice and bright except the wired network connection. I presume this is because the network adapter changed with the new mb and I have a new MAC address for the ethernet device.

I have found the new MAC address and attempted to modify my old connection with it but still no connection. The port on the motherboard has the usual orange and green lights, the router sees the mb adapter but still no connection.

Any ideas on how to get the ethernet adapter working?

---

### Post by chili555 on 2010-02-28
Please open a terminal and tell us what kind of ethernet device it is:```
sudo lshw -C network
```> I have found the new MAC address and attempted to modify my old connection with itDo you recall what you modified? It shouldn't be needed.

---

### Post by bwallum on 2010-02-28
Hi, thanks for your help. I found out that the network adapter on the motherboard is a gigabit adapter. In the cmos menu I could choose 'Pin Strap', 'MII' or 'RGMII'. I understand the Pin Strap to be an auto sensing configuration, MII specifically for 100Mb/s and RGMII for gigabit connection. Both Pin Strap and MII failed to allow me to connect. I then put a 10/100 Mb/s ethernet card into a pci slot and bingo, it had connected before the Desktop came up.

So I think the issue lies with the kernel recognising the particular embedded ethernet hardware that I have on the motherboard and controlling it to work on a 10/100 Mb/s network (if indeed, that can be done).

I changed the MAC address by right clicking on network icon, choosing Edit Connections, select wired tab, select connection, click on Edit button and enter the MAC address under the wired tab.

It would be good to get the motherboard ethernet connector going. This is the piece of relevant hardware, MAC address 0'd out by me.

> description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth2
          version: a2
          serial: 00:00:00:00:00:00
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:27 memory:fe02d000-fe02dfff ioport:ec00(size='8')

and this is the pci ethernet card that is currently providing my network connection:- 

 > description: Ethernet interface
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:01:06.0
             logical name: eth3
             version: 08
             serial: 00:00:00:00:00:00
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.69 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
             resources: irq:18 memory:fdfff000-fdffffff ioport:bc00(size=64) memory:fde00000-fdefffff memory:fdc00000-fdcfffff(prefetchable)

Loses me, i have to say.

---

