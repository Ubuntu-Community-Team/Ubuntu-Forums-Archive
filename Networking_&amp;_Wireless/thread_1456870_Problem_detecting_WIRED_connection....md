---
title: "Problem detecting WIRED connection..."
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by bowarwick on 2010-04-17
Hi. If you can help me solve this problem I would really appreciate it.

I'm struggling to get my laptop (ubuntu 10.4) to detect  a wired internet connection. I'm not seeing the "auto eth0" drop down when I click on the network manager  up top.

The problem started after trying to share my wireless connection to another computer over the wired connection... and I did something that broke my ability to connect to ANY wired network.

I don't know much about networking, but I suspect I'm having problems with some sort of "interface" configuration. 

Here's some output (no idea what it means):

```
root@bigfoot:/home/bo# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:7e:d3:02:ba  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fed3:2ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316874 errors:0 dropped:0 overruns:0 frame:67798
          TX packets:330791 errors:553 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273008116 (273.0 MB)  TX bytes:140678948 (140.6 MB)
          Interrupt:17 Base address:0xc000 

eth1_rename Link encap:Ethernet  HWaddr 00:1c:23:87:c6:77  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1625525 (1.6 MB)  TX bytes:1625525 (1.6 MB)

root@bigfoot:/home/bo# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 01
       serial: 00:19:7e:d3:02:ba
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.0.6 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1_rename
       version: 02
       serial: 00:1c:23:87:c6:77
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:f9bfe000-f9bfffff
```

Any ideas would really help me out. Thanks.

Bo

---

### Post by Iowan on 2010-04-17
Dunno if it'll fix the problem, but you can edit */etc/udev/rules.d/70-persistent-net.rules* to re-define **eth1_rename** as **eth1**. (Making a backup first would be a good idea.)
Somewhere along the way, eth0 ended up as the wireless card...

---

### Post by bowarwick on 2010-04-17
Thanks for the tip. This file doesn't have  "eth1_rename" in it though.

Here are the contents of */etc/udev/rules.d/70-persistent-net.rules*:
```
# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:7e:d3:02:ba", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:23:87:c6:77", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:7e:d3:02:ba", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

Any other files I should check? 

And is it possible to reset my network configurations to the default-- like when I first installed Ubuntu?

I'm just trying to  get the  wired  "auto eth0" to show up when I click the network manager.

---

### Post by bowarwick on 2010-04-18
SOLVED. I don't remember doing anything to fix it... but it looks like it reset and renamed itself.

Thanks for all the help I received (sarcasm).

---

### Post by Iowan on 2010-04-18
Glad you got it going (no sarcasm)!
Hope it stays fixed...

---

### Post by Iowan on 2010-04-18
Glad you got it going (no sarcasm)!
Hope it stays fixed...

---

