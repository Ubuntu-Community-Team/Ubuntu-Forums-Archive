---
title: "TRENDnet TEW-643PI wireless adapter driver"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by RodogJR on 2010-03-16
My roommate broke the router in our dorm room and now I have to connect to my university's network. I was using ethernet through our router, but now I cannot do that. I recently installed the TRENDnet TEW-643PI and it works perfectly on the Windows 7 partition. Is there anyway to get the card working on Ubuntu without being connected to the internet?  Oh and I don't want to plug into the wall because I'll have to register my computer to the university and that wouldn't be a good thing.

---

### Post by stephenvbc on 2010-06-09
Did you ever find a solution?

---

### Post by berserkpi on 2011-05-17
Same problem here I'm on Ubuntu 11.04. The TEW-643PI is by no means working.

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
03:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

ndiswrapper says everything is ok...

```
net819xp : driver installed
	device (10EC:8190) present
```

ifconfig doesn't show a wlan:


```
eth0      Link encap:Ethernet  HWaddr e0:69:95:58:1f:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92497 (92.4 KB)  TX bytes:92497 (92.4 KB)
```

Thanks for your help.

---

### Post by Vanish00 on 2012-04-07
I got the exact problem, did anybody ever get an answer.  in my ifconfig I don't see my card label at all or even see the label "wlan".

If I come across an answer I"ll post here, any advice?

cmd$ lshw -C network

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:9f:bd:8e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.105 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:c000(size=256) memory:f6100000-f6100fff


```

here is my "ifconfig" but same as the one above.

```

eth0      Link encap:Ethernet  HWaddr c8:60:00:9f:bd:8e  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fe9f:bd8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2952028 (2.9 MB)  TX bytes:438308 (438.3 KB)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

