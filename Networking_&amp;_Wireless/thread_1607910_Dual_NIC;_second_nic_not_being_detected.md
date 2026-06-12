---
title: "Dual NIC; second nic not being detected"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by stromdal on 2010-10-28
Hi, I'm a semi-n00b

I got my hands on an old BorderWare MXtreme MX-200 mail firewall and decided to install Ubuntu 10.04.1 on it and use it as a regular firewall - just for funzies. It's basically just a vanilla P4 PC in a 1U rack casing, so the hardware is not too exotic.

After adding some RAM (and hooking up a CD-ROM to be able to boot from CD), Ubuntu installed and works fine, except for the second NIC.

The NIC is there, enabled in BIOS and detected by Ubuntu:

```
$ lspci
...
01:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)
01:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)
```

But it is not active:

ifconfig output:

```
$ ifconfig
eth0     Link encap:Ethernet  HWaddr 00:...

lo       Link encap:Local Loopback...
```

I tried modifying /etc/network/interfaces:

```
auto eth1
iface eth1 inet dhcp
```

This only results in the following error msg:

```
$ sudo /etc/init.d/networking restart

...

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1
```

I looked into /etc/udev/rules.d/70-persistent-net.rules, but there was only the one entry for eth0

Any suggestions?

---

### Post by Iowan on 2010-10-28
What is revealed by **sudo lshw -C network** ?

---

### Post by stromdal on 2010-11-01
```

$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 10
       serial: 00:e0:81:62:20:b0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ed040000-ed040fff ioport:c000(size=64) memory:ed020000-ed03ffff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
       resources: memory:ed041000-ed041fff ioport:c400(size=64) memory:ed000000-ed01ffff memory:20000000-2000ffff(prefetchable)

```

---

### Post by Iowan on 2010-11-01
Unfortunately, brain is getting foggy tonight, but eth1 is not recognized. Dunno the trick to get a driver assigned... You *might* be able to edit one into */etc/udev/rules.d/70-persistent-net.rules*, but I suspect the system is having a different problem. 

Hope this at least serves as a bump...

---

### Post by stromdal on 2010-11-02
Well, if I knew the MAC address I might have been able to add an entry in /etc/udev/rules.d/70-persistent-net.rules, but since neither the BIOS or the lshw -C network command provides that informations it seems I'm screwed.

---

### Post by stromdal on 2010-11-03
Is there some way to find the MAC addy of the second NIC?

---

### Post by stromdal on 2010-11-09
Bump!

---

### Post by bala150985 on 2011-11-21
I had a similar problem, I edited the file /etc/network/interfaces and added the lines as shown below

 	Code:
 	auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp

Now I restarted my Network sudo /etc/init.d/networking restart

Wola both my interfaces are up and running :-)

---

