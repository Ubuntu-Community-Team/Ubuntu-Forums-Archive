---
title: "Broadcom BCM4311 : b43-pci-bridge keeps claiming card instead of ndiswrapper"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by kecker on 2009-12-09
I have a Broadcom Corporation BCM4311 802.11 b/g WLAN card in my Dell Inspiron 1520.  I was using the b43 driver until the upgrade to 9.10.

In the process of trying to switch over to ndiswrapper it seems that b43 is still grabbing the card before ndiswrapper does.  

root@Hermes:/home/kecker# lshw -C Network
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
       configuration: **driver=b43-pci-bridge** latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b0:35:57
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.115 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff

I've added b43 to the /etc/modprobe/blacklist.conf file but that doesn't appear to have helped. 

ndiswrapper appears to have a windows driver that makes it happy.

root@Hermes:/home/kecker# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4311) present (alternate driver: ssb)

I just can't seem to get ndiswrapper to take control.

Any thoughts?

---

### Post by kecker on 2009-12-09
I should point out the current driver is sort of working.  I can see the wireless networks I have access to but if I try to connect it very briefly connects before dropping the connection at which time it "forgets" the security key.

If I reenter the key it tries to connect but fails and immediately re-forgets the key.

So I guess if you know how to fix that problem instead I'd be very appreciative.

---

### Post by kecker on 2009-12-09
If I try to shut every thing down :

> 
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

Then ndiswrapper appears to take control

root@Hermes:/home/kecker# lshw -C Network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:53:39:ef
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,10/12/2006, 4.100. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b0:35:57
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.115 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff

But I still end up with the problem where when it tries to connect it does connect but then immediately drops the connection after "losing" the security key.

Any suggestions on how to make ndiswrapper load properly so it grabs control but does so in a way that it won't immediately drop the connection?

---

### Post by kecker on 2009-12-16
anything??  anyone???

---

### Post by kecker on 2009-12-17
Could someone provide some guidance?

---

### Post by dmizer on 2009-12-18
Add these lines to /etc/rc.local anywhere above "exit 0"
```
rmmod b43
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44
```

---

