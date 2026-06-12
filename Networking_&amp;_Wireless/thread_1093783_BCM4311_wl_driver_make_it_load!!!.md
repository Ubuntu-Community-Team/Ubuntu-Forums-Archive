---
title: "BCM4311 wl driver make it load!!!"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by thinking2loud on 2009-03-11
I got my installation of 8.04.2 too screwed up in the process of 'learning' about Linux...so I upgraded to 8.10 and I promise I'm not going to keep tweaking it ;).

I've had the worst problems with wireless BCM4311, networkmanager applet, wicd, wifi-radar, ndiswrapper, ....  I had it sort of working with ndiswrapper and manual configuration.  Now, I upgraded to 8.10 and I got the proprietary wl driver.  I get one of 2 answers when I reboot:

Works perfectly.  Connects fast, with WPA2:
```

% lshw -C network
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7d:c6:9b:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.115 latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

Doesn't work.  Doesn't even show that it has wireless networking.  Really not happy:
```
% lshw -C network
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```

I get each case about 1/2 the time.  This is what I have in /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
# boris was here
wl

```

The /etc/modprobe.d/blacklist has bcm43xx, b43, and b43legacy in it.  I don't have ndiswrapper (or b43) in the system.

How do I get it to load wl.ko every time.  Then it will work.  And I will be happy.

---

