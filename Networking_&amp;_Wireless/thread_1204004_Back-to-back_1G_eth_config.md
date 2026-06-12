---
title: "Back-to-back 1G eth config"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by gurt on 2009-07-04
I have 2 ubuntu 9.04 64-bit Desktops. They are connected via an ethernet cable which is pinned out for 1G. It works. I can ping, NFS, etc.
But the performance isn't that great. The MTU is 1500 and Network Tools says the Link Speed is "not available". Both are onboard Realtek 81xx.

These PCs used to run XP Pro and I set up the connection to be 1G duplex with 7k MTU.
I want to do the same thing with ubuntu. Can someone point me in the right direction?

Ta!

---

### Post by gurt on 2009-07-04
I found some posts and tried this...

edited /etc/network/interfaces, on both side (different ip addresses)
```
iface eth0 inet static
address 8.8.8.9
netmask 255.255.255.0
mtu 7000

pre-up ethtool -s eth0 autoneg off speed 1000 duplex full
auto eth0
```

Questions...
1. How can I see if the config took?

My wireless connection was wiped out and eth0 is no longer listed in Network Connections.
2. Once I use etc/network/interfaces does that mean all my interface configs need to be listed there now?

Thanks!

---

### Post by gurt on 2009-07-04
Needed to add sudo...

```
iface eth0 inet static
address 8.8.8.9
netmask 255.255.255.0
mtu 7000

pre-up sudo ethtool -s eth0 autoneg off speed 1000 duplex full
auto eth0
```

The way to confirm is....
```
gurt@mingus:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:8c:d6:e0
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=8.8.8.9 latency=0 link=yes module=r8169 multicast=yes port=MII speed=1GB/s
```

The 'size' is what's configured; 'capacity' is what's possible on this hw.
Note 'capabilities' vs 'configuration'

What fun!!

---

