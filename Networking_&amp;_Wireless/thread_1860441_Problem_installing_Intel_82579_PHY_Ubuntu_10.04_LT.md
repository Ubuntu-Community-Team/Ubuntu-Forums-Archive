---
title: "Problem installing Intel 82579 PHY Ubuntu 10.04 LTS"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by ellux on 2011-10-14
Good Evening,

I am trying to install an Intel 82579 network card from an Intel S1200BTL wich has two network cards:

One Gigabit Ethernet device 82574L connect to PCI-E x1 interfaces on the PCH
One Gigabit Ethernet PHY 82579 connected to PCH through PCI-E x1 interface

After installing Ubuntu 10.04 LTS Server 64 bit i noticed that the drivers were only loaded for the Intel 82547L network card. 

```
root@server:~$ sudo lshw -C network

  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:c1a00000-c1a1ffff memory:c1a70000-c1a70fff ioport:3040( size=32)

  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:1e:67:1e:66:2e
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=2.1-0 ip=192.168.0.254 latency=0 link=yes multi                                                                                                                     cast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:c1900000-c191ffff ioport:2000(size=32) memory:c1920000-c1923fff
```

I downloaded and installed the last version of the Intel driver (e1000e), and managed to make it work. Unfortunately after restart it is all gone.

Basicly after i restart the server in order for me to use the 82579 network card i must do the following:

```
rmmod e1000e
```
```
modprobe e1000e
```
After doing this 

```
root@server:~$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: 00:1e:67:1e:66:2f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-NAPI duplex=full firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:c1a00000-c1a1ffff memory:c1a70000-c1a70fff ioport:3040(size=32)
```
so it detects some generic drivers for my card. After that I only activate it using ...
```
ifconfig eth1 up
```
And it works until the next restart.


What can i do? Has anyone encountered this problem so far?

---

### Post by dityo32 on 2012-08-23
I have the same problem on my intel S1200BTS server board. Gone after restart and everytime I have to do rmmod e1000e and modprobe e1000e also. Anybody solve it yet?

---

