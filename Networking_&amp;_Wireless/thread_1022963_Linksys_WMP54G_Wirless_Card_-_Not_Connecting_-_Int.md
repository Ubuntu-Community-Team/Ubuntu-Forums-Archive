---
title: "Linksys WMP54G Wirless Card - Not Connecting - Intrepid 8.10"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by umechanism on 2008-12-27
I'd like to add my post to the heap of posts stating trouble getting the Linksys wireless WMP54G card to connect.

My setup:

Old Compaq Presario desktop - dual boot with XP
Linsys WMP54G Wirless PCI card (which works perfectly in Win XP)
Ubuntu 8.10 (Intrepid)

Network setup is:

> sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.2.114
netmask 255.255.255.0
gateway 192.168.2.1

auto wlan0
iface wlan0 inet static
address 192.168.2.114
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key s:79DBFD5FD3E018***
wireless-essid Trojan

#auto wlan0

auto eth0

***************************

Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:60:08:42:19:78  
          inet addr:192.168.2.114  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45832 (45.8 KB)  TX bytes:45832 (45.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:b6:99:d3:39  
          inet addr:192.168.2.114  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-99-D3-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**********************


I would really appreciate any help.

Thanks.

Mike

---

