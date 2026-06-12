---
title: "No Networks Found After Ubuntu Karmic Install"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by wfarr_09 on 2010-04-01
Hi Ubuntu Forums Community

I Just Upgraded my Laptop from Ubuntu 9.04 to Ubuntu 9.10 and Before I upgraded to 9.10, My Network Was Working Fine, But i've tried installing/upgrading to Ubuntu 9.10 and no such luck.

thanx in advance,

WFarr_09

---

### Post by Iowan on 2010-04-01
You'd think what used to work wtill would, but...
Check (post if possible) **sud lshw -C network** to see if interfaces are recognized and **ifconfig -a** to see if they have IP address (probably won't...)

---

### Post by Xmat on 2010-04-07
> **Iowan said:**
> You'd think what used to work wtill would, but...
Check (post if possible) **sud lshw -C network** to see if interfaces are recognized and **ifconfig -a** to see if they have IP address (probably won't...)

Dear Iowan,

I have the same problem after upgrading to Karmic.

My interface is recognised. This is the results from **sudo lshw -C network**:

```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:23:ae:8e:19:57
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5754-v3.24 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:78 memory:f7cf0000-f7cfffff

```

And this is the result of **ifconfig -a**:

```
eth0      Link encap:Ethernet  HWaddr 00:23:ae:8e:19:57  
          inet6 addr: fe80::223:aeff:fe8e:1957/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20480 (20.4 KB)  TX bytes:2568 (2.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

It'd been working well for almost 1 year with Ubuntu 9.04...

Thanks for your help...
Matteo

---

### Post by wfarr_09 on 2010-04-07
here's the result from the code posted

---

### Post by Xmat on 2010-04-08
> **Xmat said:**
> Dear Iowan,

I have the same problem after upgrading to Karmic.



...I'm sorry, forget my post.

Apparently it was a network problem here in the office (the DHCP server was down). It was just bad luck that it happened when I upgraded Ubuntu....

:)

---

### Post by wfarr_09 on 2010-04-11
> **Xmat said:**
> ...I'm sorry, forget my post.

Apparently it was a network problem here in the office (the DHCP server was down). It was just bad luck that it happened when I upgraded Ubuntu....

:)

@Xmat:it's all good. @everybody!:I posted the logs a couple of days ago and it should have some info for all you UBUNTU Superheros....thx

*EDIT* I Upgraded to Lucid 04/30/10 or last night. *Note* Ubuntu 10.04 actually found my Linksys Wireless-B Network

---

