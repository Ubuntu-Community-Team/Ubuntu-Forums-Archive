---
title: "Wired Connection Slow Connecting"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by wnodrog on 2013-01-06
Hi - not sure is this post should be here or in Hardware but..............Wired Connection very slow to connect to my ZyXEL ADSL modem, will eventually connect after a long time.  (12.10)

---

### Post by wnodrog on 2013-01-07
I am really out of realm here but here goes. I have found that I can get a connection right away after computer  reboot most of the time if I reboot my modem, otherwise it will either  not connect at all or take a long time to connect. Wireless works  perfectly with same ZyXEL ADSL modem. Prior to recent installation of 12.10 wired connection was never a problem on Crunchbang.
It looks like I have an Intel 82579V Gigabit Network Connection adapter - is this supported for 12.10?  

Any suggestions or ideas as to where I might start with this would be much appreciated -  thanks.

```
gw@gw:~$ sudo lshw -class network
[sudo] password for gw: 
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 38:60:77:20:89:88
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fe600000-fe61ffff memory:fe628000-fe628fff ioport:f080(size=32)
  *-network

```

---

### Post by Pjotr123 on 2013-01-07
Is there a Windows boot in between? If so, it may be this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-No-wired-or-wireless-internet-on-a-dual-boot-computer](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-No-wired-or-wireless-internet-on-a-dual-boot-computer)
(item 3, right column)

---

### Post by wnodrog on 2013-01-07
No dual boot, Ubuntu only.  I will keep fumbling away.  Thanks for the links.

---

