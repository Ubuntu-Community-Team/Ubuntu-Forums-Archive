---
title: "Can't connect to the internet"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by takakia on 2006-06-29
I have been using Ubuntu since Jun 01.  But from yesterday I am having problems connecting to the internet.  I connect to the internet via our office LAN using DHCP setting.  It worked without any problem but now I am not able to connect.

[[IMG]http://img131.imageshack.us/img131/8579/noconnection7th.th.jpg[/IMG]](http://img131.imageshack.us/my.php?image=noconnection7th.jpg)
"
I think, this happened after I installed the rp-pppoe program for connecting to ADSL (at home) and ran the program from my office LAN connection.  

ifconfig eth0 shows the network is working, all hardware is detected.
From graphical control panel I could see everything is working fine.
[[IMG]http://img235.imageshack.us/img235/4358/noconnection2m7qw.th.jpg[/IMG]](http://img235.imageshack.us/my.php?image=noconnection2m7qw.jpg)

[[IMG]http://img209.imageshack.us/img209/3747/noconnection44qh.th.jpg[/IMG]](http://img209.imageshack.us/my.php?image=noconnection44qh.jpg)

I can ping to 127.0.0.1 - showing tcpip is working.

My network card is  RTL-8139 which is at eth0 
my wireless card card is Intel PRO/Wireless 2200BG

"lshw -C network" gives :
```

*-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:b9:28:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=radio off
       resources: iomemory:e0204000-e0204fff irq:10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:a1:6b:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too ip=147.8.76.128 multicast=yes
       resources: ioport:3000-30ff iomemory:e0206800-e02068ff irq:10

```

In network tools it shows eth0 is active but still I cannot go into the internet.  
[[IMG]http://img235.imageshack.us/img235/8641/noconnection3m2wz.th.jpg[/IMG]](http://img235.imageshack.us/my.php?image=noconnection3m2wz.jpg)

I tried disconnecting eth0 and connectiong again, but still the problem presists.  

I could not figure out what is the problem and how to solve it ??

---

### Post by sanjeev on 2006-06-29
how about checking the dns in network settings?

---

### Post by takakia on 2006-06-29
Usually the DNS is automatically resolved as there is none mentioned by your CC administrators

---

