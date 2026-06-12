---
title: "Unclaimed when working driver installed"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by jangozo on 2010-06-07
Hello,

I'm using a Dell with Broadcom bcmwl6.inf driver. I tried the guides using ndiswrapper, but they didn't work for me. What worked was simply going to System -> Administration -> Hardware drivers and activating the Broadcom STA proprietary driver. That sounds great, but every time I restart, I have to remove and install the driver from Hardware Drivers.

What should I do to keep the driver loaded and claimed at the start. This is my lshw -C network before and after removing and installing wireless card driver. 
```
vladimir@vladimir-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:41:17:56
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
vladimir@vladimir-laptop:~$ sudo pico /etc/modprobe.d/blacklist.conf
[sudo] password for vladimir: 
vladimir@vladimir-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:09:6f:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 ip=192.168.1.65 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:41:17:56
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)

```Thanks

---

### Post by jangozo on 2010-06-07
bumpy

---

### Post by purelinuxuser on 2010-06-07
> **jangozo said:**
> bumpy

Geesh, it's only been three hours :P

Press Alt+F2, type
```
gksudo gedit /etc/modules
```
and then click "Run."  At the bottom of the file that opens up, add
```
wl
```

Then hopefully wireless will work on reboot ;)

---

### Post by jangozo on 2010-06-07
Thanks, this fixed it! :) Impatience is a bad quality.

---

