---
title: "Wireless Adapter Not Working"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by tew88 on 2010-08-26
As the title reads. My wireless adapter does not work when I boot from the Ubuntu 10.04 LiveCD.

The adapter in question... tricky. It's this one: [http://www.amazon.co.uk/Wireless-150Mbps-802-11n-Mini-Adapter/dp/B002755QJG/ref=sr_1_5?ie=UTF8&s=computers&qid=1282826985&sr=8-5](http://www.amazon.co.uk/Wireless-150Mbps-802-11n-Mini-Adapter/dp/B002755QJG/ref=sr_1_5?ie=UTF8&s=computers&qid=1282826985&sr=8-5) - however, aside from a mention in one of the comments to a "Ralink RT2780", I don't see any reference to a make/model.

The software that ships with this product is indeed Ralink-branded, but again there's no mention of a specific make/model.

So I assume it's just a driver issue, however I've no idea where to begin in my search for one as I can't identify its model number.

Any ideas?

Thanks!

---

### Post by dineshs on 2010-08-26
If you can post the outputs of the following commands someone can help```
sudo lshw -C network
```
```
iwconfig
```

---

### Post by tew88 on 2010-08-26
Thanks for the reply, dineshs.

Output as follows:

**~$ sudo lshw -C network**
```
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:24:8c:df:43:f4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbfc0000-fbfdffff(prefetchable)
```

**~$ iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

**~$ lsusb**
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 047d:2048 Kensington 
Bus 003 Device 002: ID 045e:00b4 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:3370 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by dineshs on 2010-08-26
Is it a USB wireless adaptor?
Have you seen this?
[http://ubuntuforums.org/showthread.php?p=9629785](http://ubuntuforums.org/showthread.php?p=9629785)

---

### Post by tew88 on 2010-08-26
It is a USB adapter and I hadn't seen that post, no.

I'll give it a try and see what happens. Thank you for the link!

---

### Post by tew88 on 2010-08-26
I followed the instructions in the recommended post, but it's still not working. Any other suggestions?

---

### Post by dineshs on 2010-08-26
what about ```
iwconfig
```

---

### Post by tew88 on 2010-08-26
Still the same:

**$ iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by dineshs on 2010-08-26
No idea.Let us wait for experts

---

### Post by tew88 on 2010-08-26
Sounds like a plan. Thank you for your help.

---

