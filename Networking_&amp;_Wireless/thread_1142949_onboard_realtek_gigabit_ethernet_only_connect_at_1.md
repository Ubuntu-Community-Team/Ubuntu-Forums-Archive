---
title: "onboard realtek gigabit ethernet only connect at 100mb/s"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by talz13 on 2009-04-29
I just installed jaunty last last weekend, and noticed that I'm not connecting at 1gb/s anymore.  Here is my lshw -C Network:
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:8a:05:af
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
```

I have everything hooked up to a netgear gs105 gigabit switch with cat6 cable.

---

### Post by talz13 on 2009-05-02
Any ideas to try on this one?  I believe it used to connect at 1gbps on hardy...

---

### Post by talz13 on 2009-05-02
ok, what's weird is I have another PC with a similar gigabyte motherboard, p35-ds3l (mine is a p45-ds3l I believe) and it connects fine at 1gbps.

Here's the output from the other PC that connects at 1gbps:```
eff@parents-ubuntu:~$ sudo lshw -C Network
[sudo] password for jeff: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:d0:57:5a:8f
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes module=r8169 multicast=yes port=MII speed=1GB/s
```

and my PC that connects at 100mbps:```
jeff@server:~$ sudo lshw -C Network
[sudo] password for jeff: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:8a:05:af
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
```The only difference I see is in the "version" field, where the p35 board has version 01 and my board has version 02.  Same driver, module, same everything else.

---

### Post by chili555 on 2009-05-02
Have you tried to set it explicitly?```
sudo ethtool -s eth0 speed 1000
```

---

### Post by talz13 on 2009-05-02
Ok, I just tried that and it just ended up disconnecting the network until I set it back to auto-negotiate.

It looks like I fixed it, too.  I ended up swapping ports on the netgear switch until the gigabit light lit up on the switch.  I'm really starting to have doubts as to the quality of these netgear switches... The first two ports only showed 100mb, it wasn't until the 3rd port that I got a gigabit connection!

---

