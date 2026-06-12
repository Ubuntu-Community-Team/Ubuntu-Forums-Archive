---
title: "wireless doesn't pick up one of the networks I need"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by b00mzi11a on 2011-04-11
Hi all,  

I just loaded 10.10 onto a stock hp pavalion zt3000 and everything is running fine except it won't detect my college's wifi network.  It picks up everything else and runs without a hitch.  (I'm actually on my work's wireless network atm)

The network is not hidden and doesn't have any encryption.  The wireless is on and has even detected other networks when it doesn't see the school's.  I searched but couldn't find much on this specific problem but Im guessing/hoping its something simple :D 

here's the hardware:  
Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

here's ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:02:3f:67:05:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x4000 

here's the network config:
      description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:84:41:bc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.9 latency=128 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: irq:5 memory:90000000-90000fff

---

### Post by g00f on 2011-04-11
The first thing I'd look at is what channel is your college's wifi network on? Then look at what country code your wireless adapter is set to and what channels it is capable of.

For more info on why this is relevant, look here: [http://en.wikipedia.org/wiki/List_of_WLAN_channels]("http://en.wikipedia.org/wiki/List_of_WLAN_channels")





.

---

### Post by b00mzi11a on 2011-04-14
I'll bug the tech center about what channel they're on, but could someone talk me through finding out what my devices channel limitations are?

---

