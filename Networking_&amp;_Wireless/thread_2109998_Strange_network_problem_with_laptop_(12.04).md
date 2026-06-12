---
title: "Strange network problem with laptop (12.04)"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by NilPointer on 2013-01-29
I didn't boot into Ubuntu 12.04 on laptop for about 1.5 months. When I did, network didn't work. Neither wired, nor wireless. I tried to configure wired connection manually instead of DHCP, it connected but something was still wrong. Wired network when in DHCP mode doesn't want to connect. When wired network configured manually, it connects, but nothing works - cannot go to any address with browser, including router's IP address. Wireshark shows some laptop-router ARP activity, so apparently link should work, but nothing useful can be done. Pinging router doesn't work, but pinging another machine in network does. I guess something prevents laptop from connecting to router (that would explain why DHCP connection fails).

---

### Post by NilPointer on 2013-01-29
Still no success. Network seems to work, laptop can be pinged from desktop and laptop can ping desktop. But router can't be accessed.

---

### Post by TOMBSTONEV2 on 2013-01-29
Please determine your network adapters with lspci

---

### Post by Bucky Ball on 2013-01-29
Better still:

```
sudo lshw -C network
```

Post the output, please.

---

### Post by Grinage on 2013-01-29
What is your laptop breed?  Make?  Model?
What network interfaces does the computer think is has?

---

### Post by NilPointer on 2013-01-29
lspci output (only network adapters):

```
02:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```

It shows Broadcom combo Bluetooth/Wi-Fi module and Realtek Ethernet NIC.

Here is lshw output:

```
  *-network DISABLED      
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c0:18:85:bb:fc:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.55.19 (r300276) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:f1500000-f1507fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 5c:f9:dd:3f:08:92
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.241 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
```

P.S: Yes, I know hardware switch for Wi-Fi was "off" when I ran lshw.

Laptop is Dell 17r-5720. It came with Ubuntu 11.10, but I upgraded it to 12.04 LTS.
It has loopback interface, eth0 (Ethernet) and eth1 (Wi-Fi).

---

### Post by Bucky Ball on 2013-01-29
Ok. Do an update via a cable and look in Additional Drivers. Is there anything in there named b43 or STA? You have a Broadcom wireless card in there and they are generally very well supported. It appears to have the wrong driver installed ...

driver=wl0

... which may need to be blacklisted. Let's persevere. Also provide the output of 

```
iwconfig
```

---

### Post by NilPointer on 2013-01-29
Uh, looks like problem is solved... When I booted into Windows and there still was no connection (neither wired, nor wireless), I decided to look closely to router configuration... Looks like I've accidently banned laptop's MAC-address. I feel like an idiot. :oops:

By the way, wlan driver is manually compiled Broadcom STA, named wl.ko with support for Broadcom device 4365.

---

### Post by Bucky Ball on 2013-01-29
All good then. Mark as 'Solved' from Thread Tools to help others if all working. Enjoy!

---

