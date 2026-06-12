---
title: "On and off Wired connection established / disconnected"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by Gelupah on 2011-12-07
Hi,

I'm having a very strange problem with my system lately; wifi works fine (stable etc), but as soon as I plug in my RJ45 to use ICS, I get continuous messages, at regular intervals, quoting "Wired network - connection established" and "Wired network - disconnected".

Usually the change occurs every 10-20seconds, but sometimes as fast as 3 seconds; but it's always at regular intervals (appears to be anyway). I have the same problem connecting to another device, so it's not the target device the cause. I find it very unlikely the cable is the cause, since it used to work just fine, and nothing has changed since.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2337611 (2.3 MB)  TX bytes:587659 (587.6 KB)
          Interrupt:42 Base address:0x2000 
```

What could be causing this?

Thanks,

Tony

---

### Post by praseodym on 2011-12-07
Hi,

you want to share from LAN to wireless or cell phone? Which encryption do you use? Only WEP works fine (in general)

---

### Post by Gelupah on 2011-12-08
> **praseodym said:**
> Hi,

you want to share from LAN to wireless or cell phone? Which encryption do you use? Only WEP works fine (in general)

The idea is to use the internet, on my desktop, coming through the wifi, to be shared via RJ45 to another PC without a wifi card. It used to work fine, no idea what changed it, a distribution update, or some updates along the line, who knows?

The wifi is indeed in WPA - could that be an issue for internet connection sharing?

---

### Post by HeavyDC223 on 2011-12-08
Apparently this isn't a new issue:
[http://ubuntuforums.org/showthread.php?t=1175601](http://ubuntuforums.org/showthread.php?t=1175601)

My Lenovo ThinkPad R61i did the same thing all morning, then stopped immediately after I ran lshw -C Network. Now it's working properly. I added my issue at the end of the above post.

this is what lshw gave me on the Ethernet card:

*-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:86:60:a7:48
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v2.11 ip=10.42.43.1 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:48 memory:fe000000-fe00ffff

---

### Post by Gelupah on 2011-12-10
I'll give that a go when I have a minute, thanks for sharing !


> **HeavyDC223 said:**
> Apparently this isn't a new issue:
[http://ubuntuforums.org/showthread.php?t=1175601](http://ubuntuforums.org/showthread.php?t=1175601)

My Lenovo ThinkPad R61i did the same thing all morning, then stopped immediately after I ran lshw -C Network. Now it's working properly. I added my issue at the end of the above post.

this is what lshw gave me on the Ethernet card:

*-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:86:60:a7:48
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v2.11 ip=10.42.43.1 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:48 memory:fe000000-fe00ffff

---

### Post by Gelupah on 2011-12-10
No luck for me unfortunately - did you need to reboot or anything? I ran that command line before plugging the RJ45, and after - and still getting the disconnects...

Thanks

Tony


> **HeavyDC223 said:**
> Apparently this isn't a new issue:
[http://ubuntuforums.org/showthread.php?t=1175601](http://ubuntuforums.org/showthread.php?t=1175601)

My Lenovo ThinkPad R61i did the same thing all morning, then stopped immediately after I ran lshw -C Network. Now it's working properly. I added my issue at the end of the above post.

this is what lshw gave me on the Ethernet card:

*-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:86:60:a7:48
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v2.11 ip=10.42.43.1 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:48 memory:fe000000-fe00ffff

---

### Post by sjs2357 on 2011-12-11
I had the same problem. ICS worked fine until recently (maybe when I updated to Oneiric, not sure), then suffered from the continuous connect/disconnect problem. What fixed it for me was, in the ipv6 settings tab (same area as where for ipv4 you set "shared to other computers") change "automatic" to "ignore".

---

### Post by Gelupah on 2011-12-11
That solved it.

Thank you thank you :D

> **sjs2357 said:**
> I had the same problem. ICS worked fine until recently (maybe when I updated to Oneiric, not sure), then suffered from the continuous connect/disconnect problem. What fixed it for me was, in the ipv6 settings tab (same area as where for ipv4 you set "shared to other computers") change "automatic" to "ignore".

---

### Post by ryann2k1 on 2013-03-27
> **sjs2357 said:**
> I had the same problem. ICS worked fine until recently (maybe when I updated to Oneiric, not sure), then suffered from the continuous connect/disconnect problem. What fixed it for me was, in the ipv6 settings tab (same area as where for ipv4 you set "shared to other computers") change "automatic" to "ignore".

I have the same problem and after trying your solution, the problem still remain, connect and disconnect issue. Any idea to solve?
Thanks.

---

### Post by wildmanne39 on 2013-03-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

