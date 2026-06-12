---
title: "Internet connection lost (Ubuntu 10.10)"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by mreza69 on 2011-04-11
hi everyone!
I installed Ubuntu 10.10 in 2 days ago, everything was ok.
about 20 min ago I reboot the system and wireless connected, but I wasn't connected to the internet! all ping tell "Unknown host". I check my wi-fi modem and it was connected to the internet. I went to the Windows and everything was ok. I reboot 10 times and reboot my modem to, but internet is lost! even I connect Ethernet cable but similar! Network is work good, but cann't share internet for me. you can see information here:

ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:25:64:81:a8:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:66:dd:b7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe66:ddb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358 (358.0 B)  TX bytes:2964 (2.9 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5584 (5.5 KB)  TX bytes:5584 (5.5 KB)




route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1





can anybody help me? :(
thanks a lot

---

### Post by Iowan on 2011-04-11
> **mreza69 said:**
> hi everyone!
I installed Ubuntu 10.10 in 2 days ago, everything was ok.
about 20 min ago I reboot the system and wireless connected, but I wasn't connected to the internet! all ping tell "Unknown host". I check my wi-fi modem and it was connected to the internet...  Even pings to 192.168.1.1? Can you ping an internet address by IP (74.125.225.17)?

---

### Post by mreza69 on 2011-04-12
> **Iowan said:**
> Even pings to 192.168.1.1? Can you ping an internet address by IP (74.125.225.17)?

Last night that I wrote this Thread No. I couldn't ping Internet address, but could ping Ethernet address like 192.168.1.1. today I power on my modem and everything is ok :O I think this because of changing my Internet IP address!
thanks for your attention

---

### Post by Iowan on 2011-04-12
Glad it's working - give it a couple of days before marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

