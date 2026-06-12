---
title: "No wired connection"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by eventhorizonof on 2010-06-03
I am trying to connect to the internet on ubuntu and it seems that I am unable. I have been perusing for solutions but have not found any. The lights in the back blink and I can see autoeth0 in the network manager. 

for
**sudo lshw -C network**

I get:

         
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:8e:9a:08
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff(prefetchable) memory:febc0000-febdffff(prefetchable)

Any ideas?

---

### Post by eventhorizonof on 2010-06-03
Please help I desperately need to get on the internet is there anything in particular I should do? Thanks

---

### Post by Iowan on 2010-06-03
What happens if you try (from a terminal) **sudo dhclient eth0**

---

### Post by eventhorizonof on 2010-06-03
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/40:61:86:8e:9a:08
Sending on   LPF/eth0/40:61:86:8e:9a:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Iowan on 2010-06-03
[Here]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is an option that may/not help...

---

### Post by eventhorizonof on 2010-06-08
It seems that option is more geared towards some issue with GRUB, I have installed 10.04 on a fresh machine no windows no GRUB.

I want to try to manually configure my internet connection so I have been following the getting started with ubuntu 10.04 manual and it says I should get the system information (IP address, DNS, etc) by right clicking on the network manager icon in the taskbar and clicking connection information. the connection information choice is shaded gray and I cannot click it. 

So is there a terminal command that will allow me to extract this information in an attempt to try this manual method?

---

