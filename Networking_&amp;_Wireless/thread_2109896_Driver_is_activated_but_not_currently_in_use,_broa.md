---
title: "Driver is activated but not currently in use, broadcom"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by Pocc on 2013-01-28
Hi all,

I have a Dell Vostro 1400 and cannot get the computer to connect to the internet wirelessly.

[**sudo lshw -C network**]:

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fa:8b:6f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v3.04 ip=192.168.1.87 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe5f0000-fe5fffff
 
[**lspci -nn | grep 0280**]:

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

[**rfkill list all**]:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

If you need more information, feel free to ask.

Thanks in advance!

---

### Post by chili555 on 2013-01-30
Please see here. You have the same device and require the same solution.

[http://ubuntuforums.org/showthread.php?t=2110664](http://ubuntuforums.org/showthread.php?t=2110664)

---

### Post by Pocc on 2013-02-25
Thank you for your reply; I couldn't find the usb stick: I'm going to mark this as solved.

---

