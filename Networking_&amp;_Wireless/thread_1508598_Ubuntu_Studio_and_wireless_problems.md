---
title: "Ubuntu Studio and wireless problems"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by Aggienator on 2010-06-13
I have just installed Ubuntu Studio on my old Acer Aspire 3003 and all is going well except that I can't get the wireless to switch on (it was working fine under XP). After searching the forums and with much help I have got the drivers installed for the Broadcom b43, but I still can't seem to get the wireless adapter to switch on. Many of the posts on this refer to System > Preferences > Network Connections, but I don't seem to have that option, just Network Tools and Network.

Any help gratefully received!

Output of some commands that may help below.

Cheers Aggie.

```
sudo ifconfig -a
[sudo] password for geoff: 
eth0      Link encap:Ethernet  HWaddr 00:16:36:0d:1e:d2  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe0d:1ed2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132651867 (132.6 MB)  TX bytes:3647023 (3.6 MB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:79:f3:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
lspci

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


```

```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:0d:1e:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.66 latency=173 maxlatency=11 mingnt=52 multicast=yes
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:58000000-5801ffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2000000-e2001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:79:f3:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by chili555 on 2010-06-13
What does this tell us?```
dmesg | grep b43
```Thanks.

---

### Post by Aggienator on 2010-06-13
Thanks Chili,

Got it sorted by installing Network Manager. I don;t know if I somehow missed this in the installation phase or if it isn't in the base installation for studio, but once installed it all came to life :)

Cheers Aggie

---

### Post by cchhrriiss121212 on 2010-06-15
Studio doesn't come with network manager as it interferes with the audio processing, so if you need to use a wireless connection a lot then reboot before doing any audio work.

---

### Post by Aggienator on 2010-06-26
Thanks for the warning. Wil network manager not automatically start hen I reboot?

Cheers Aggie

---

### Post by cchhrriiss121212 on 2010-06-28
> **Aggienator said:**
> Thanks for the warning. Wil network manager not automatically start hen I reboot?

Cheers Aggie
Yes it will. What I do is uncheck it from the System>Startup Applications menu, then if I need to use it I open a terminal and run nm-applet.

---

### Post by Aggienator on 2010-06-30
Thanks, I'll do that as I can use it on a wired network or even off network for quite a lot of the time I think

---

### Post by nilentropy on 2010-07-17
i am having this same problem. the b43 drivers were installed using the fwcutter just like in the regular version of Ubuntu but i still am having wireless problems in ubuntu studio. i installed network manager and enabled it but there is still no connections tab in the network. help!

---

