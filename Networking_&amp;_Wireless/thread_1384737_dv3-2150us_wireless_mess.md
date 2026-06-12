---
title: "dv3-2150us wireless mess"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by Mezzfit on 2010-01-18
Alright, so I've tried just about everything I've seen on these and other forums about my wireless card. The wireless was working after a backdated driver i tried, but as soon as I rebooted the card wont work again. I am using 9.10 64 bit version. I have windows 7 dual booted so I know the card works. When it was working it was listed as eth2.

lspci:
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

idconfig: 
eth0      Link encap:Ethernet  HWaddr 00:23:5a:a8:1d:82  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fea8:1d82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4692618 (4.6 MB)  TX bytes:441660 (441.6 KB)
          Interrupt:29 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6346 (6.3 KB)  TX bytes:6346 (6.3 KB)


iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.


The ubuntu suggested STA driver at first just didn't work, now it makes my laptop hang up when I install it and open wicd. I even tried manually compiling and insmod the wl.ko from broadcom's website. I really want to use this for school this week! Any suggestions? I think it even worked with the live CD...:(

---

