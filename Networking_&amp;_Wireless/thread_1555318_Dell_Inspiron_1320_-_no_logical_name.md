---
title: "Dell Inspiron 1320 - no logical name"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by ivanp on 2010-08-17
Hi,

I've a dell 1320 with a ubuntu 9.10 + several upgrades. I've got the need now to have the wireless card working, so I activated the broadcom sta wireless driver though system - administration - hardware drivers

my card is BCM4312
```
ivan@ubuntu:~$ lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

the system rebooted but couldn't find my wireless network. and I'm standing over the router. i checked the interface but is not up. ifconfig just listed lo and eth0.

my /etc/network/interfaces file reads
```
auto lo
iface lo inet loopback
```

first I tried the following to start it up
```
ivan@ubuntu:~$ echo b43 | sudo tee -a /etc/modules
b43
```

but didn't work. so I taught I coul add it manually to the /etc/network/interfaces file, but I can't see the interface's logical name
```
ivan@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: **BCM4312 802.11b/g**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
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
       **logical name:** eth0
       version: 02
       serial: 00:21:9b:d9:04:20
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v3.04 ip=192.168.10.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fe5f0000-fe5fffff
```

so I have not wireless.
```
ivan@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

At the hardware drivers screen stands at the bottom a legend warning "the driver is activated but not in use"

Here's the info asked in the HOWTO post wireless.

This codes didn't return any answer
```
sudo lspci -nn | grep 'Wireless Brand'
lsmod | grep "wlan_module_name"
```

any ideas on how to fix this?
Thanks in advance

---

