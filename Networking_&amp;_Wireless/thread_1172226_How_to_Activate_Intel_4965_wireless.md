---
title: "How to Activate Intel 4965 wireless"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by cmon on 2009-05-28
Hi

I got an Intel 4965 wifi card that I've been using for quite some time now. It has been working great, I've had zero problems with it until a couple of weeks ago when I disabled my wireless connection via the right click menu of the network manager. I had it disabled for a while and now I can't activate it again. How can I get it up and running again?

Outputs from iwconfig and lshw -C Network:

```
simon@simon-laptop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```


```
simon@simon-laptop ~ $ lshw -C Network
*-network               
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:c2:c7:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=192.168.0.198 latency=0 module=tg3 multicast=yes
```

---

### Post by Gausian on 2009-05-28
try typing the following in a terminal window:

```
sudo modprobe iwl4965
```

---

