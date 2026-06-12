---
title: "Windows network won't work"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Pendaws on 2009-06-07
Hi there, first post. :) Please bear with me.

I have just finished installing Ubuntu 9.04 and I must say I am REALLY impressed, lot better than the last time I tried it 6 years ago.

I cannot access my network at all. I am using a mixture of Win7, Server 2008 and XP
One of my housemate's comps has his network set as Workgroup and I have mine set as a made up name. I don't use DHCP and all of this is run through a Linksys router to a Motorola SB5100 cable modem.

My mates machine can be seen by this Ubuntu one but not my other PC's. I saw another post like this and a guy said to add a couple of files and so I am doing that.

```
george@E8400:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:21:58:4d  
          inet addr:136.xxx.xxx.xxx  Bcast:136.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe21:584d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137207452 (137.2 MB)  TX bytes:5030122 (5.0 MB)
          Interrupt:250 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1f:d0:21:3a:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
``````
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:21:58:4d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=136.xxx.xxx.xxxlatency=0 module=r8169 multicast=yes
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:d0:21:3a:cd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:f6:dc:f8:cf:b5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```


Hope that helps?

---

### Post by Iowan on 2009-06-07
> **Pendaws said:**
> I cannot access my network at all...
My mates machine can be seen by this Ubuntu one but not my other PC's.Sorry, I confuse easily - no access suggested hardware problem, but sounds more like a file sharing problem.  [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a good How-To, and [another]("http://ubuntuforums.org/showthread.php?t=288534") one on mounting shares.

---

### Post by Pendaws on 2009-06-07
Thank you Iowan for your help :)

---

