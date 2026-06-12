---
title: "Ethernet cable not connected"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by blenox on 2011-01-22
Basically ubuntu doesn't think my cable is connected (even though it is).  I'm not using a router, it is connected directly to my modem.  

I've searched these forums like crazy and have been unable to find a working solution. 

I've tried the fix in this thread ([http://ubuntuforums.org/showthread.php?t=1022411&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1022411&highlight=r8168)).  But it didn't work :(

I'm using the lastest version of Ubuntu (10.10).  Here is some network info: 

```
ubun@ubun-System-Product-Name:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:26:18:96:da:46
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.020.00-NAPI duplex=full latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:51 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbcf0000-fbcfffff

```

I hope that someone can help me out in finding a solution :(

---

### Post by Iowan on 2011-01-22
Is this a new connection to modem... that is, has the machine connected to modem before. Some modems "lock onto" a MAC address and must be reset before they'll work with another machine.

---

### Post by blenox on 2011-01-23
> **Iowan said:**
> Is this a new connection to modem... that is, has the machine connected to modem before. Some modems "lock onto" a MAC address and must be reset before they'll work with another machine.

Thanks for the reply lowan but I have managed to find a solution.

The problem was the speed and duplex.  I was having the same connectivity problem once I installed windows on my other partition. 

I ran the following command to set my speed and duplex to 10mbs which fixed the problem:

```

sudo mii-tool -F 10baseT-FD

```

---

