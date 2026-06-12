---
title: "Wireless Breaks after &quot;Disabling it&quot;"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by domefavor95 on 2012-08-23
Hello! I have recently broke my Ubuntu's entire wireless install by going to the performance options and clicking on "Disable Wireless".

Good thing I have more than one laptop and a Windows partition on the other side of Ubuntu just in case. :lolflag:

Anyways, I have just installed ndiswrapper to try and fix my blinking network light. It worked just fine. I could connect to any network just like before I installed the drivers and stuff. This was before I tried the "Disable Wireless" feature. Now my wireless is all messed up. :( I have a Acer Aspire 4720z with 12.04 Ubuntu installed. I have a Atheros AR5007EG. 

The drivers I downloaded: [http://tinyurl.com/99n27xn](http://tinyurl.com/99n27xn)

Any solutions? I hate my Windows. I wanna be using Ubuntu. );

---

### Post by Kirk Schnable on 2012-08-23
Can you give us the output of these commands...

```
lshw -C network
```

```
iwconfig
```

```
rfkill list
```

Thanks
Kirk

---

### Post by domefavor95 on 2012-08-23
LSHW -C NETWORK:
```
  *-network UNCLAIMED
description: Ethernet controller
product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0
resources: memory:80800000-8080ffff
  *-network
description: Ethernet interface
product: NetLink BCM5787M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 02
serial: 00:1b:24:e1:d0:64
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5787m-v3.23 latency=0 link=no multicast=yes port=twisted pair
resources: irq:46 memory:80300000-8030ffff
```

IWCONFIG:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

RFKILL LIST:
```
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

