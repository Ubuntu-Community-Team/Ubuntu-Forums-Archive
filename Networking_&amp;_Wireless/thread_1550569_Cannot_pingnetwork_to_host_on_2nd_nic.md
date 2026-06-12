---
title: "Cannot ping/network to host on 2nd nic"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by dieterhund on 2010-08-11
Ok, I am a bit of a newb, so go easy on me.  I have a somewhat complicated network setup that I am testing on an internal network.  So any help would be appreciated.

I have the following route setup:

PC Client (192.168.2.100) --> Router (192.168.2.1) --> DSLAM (on our internal network) --> PPPOE Server (192.168.9.1) on Linux Ubuntu 8.04 on interface card eth2.

On the same Linux Ubuntu Machine on interface card eth1 (static IP 192.168.5.100), I have an Asterisk SIP server plugged into it. SIP Server = 192.168.5.101 (static)

I need the PC client (192.168.2.100) to register via SIP soft phone to register on the SIP server (192.168.5.101). From the PC client I can ping as far as the eth1 interface (192.168.5.100)...but cannot ping the SIP Server (.101).

From the SIP server (192.156.5.101)...I can ping 192.168.5.100, I can ping 169.254.5.228 (Eth2:avahi), but not sure what that is. I cannot ping the pppoe default gateway (192.168.9.1), which I think you cannot anyway.

No firewalls are running. My IPtables I cleaned out totally. I think it might be as simple as a route add, but I really have no clue. Tried building a virtual bridge using brctl LINUX betweeh eth1 and eth2, but that made things worse (could not ping anything after that)


Route table: 

   [FONT=Verdana][SIZE=2]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]192.168.9.100   *               255.255.255.255 UH    0      0        0 ppp0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]192.168.5.0     *               255.255.255.0   U     0      0        0 eth1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]link-local      *               255.255.0.0     U     0      0        0 eth2[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]link-local      *               255.255.0.0     U     1000   0        0 eth1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]default         *               0.0.0.0         U     1000   0        0 eth2[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Ifconfig:
[/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]root@esus:/home/testadmin# ifconfig[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]eth1      Link encap:Ethernet  HWaddr 00:04:75:9d:e0:5e  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]inet addr:192.168.5.100  Bcast:192.168.5.255  Mask:255.255.255.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]inet6 addr: fe80::204:75ff:fe9d:e05e/64 Scope:Link[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX packets:342 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]TX packets:388 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]collisions:72 txqueuelen:1000 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX bytes:251766 (245.8 KB)  TX bytes:70778 (69.1 KB)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]Interrupt:9 Base address:0x2000 [/SIZE][/FONT]
  
  
  [FONT=Verdana][SIZE=2]eth2      Link encap:Ethernet  HWaddr 00:01:02:a7:9a:4d  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX packets:2530 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]TX packets:120 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]collisions:0 txqueuelen:1000 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX bytes:214935 (209.8 KB)  TX bytes:9740 (9.5 KB)[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]Interrupt:5 Base address:0x6000 [/SIZE][/FONT]
  
  
  [FONT=Verdana][SIZE=2]eth2:avahi Link encap:Ethernet  HWaddr 00:01:02:a7:9a:4d  [/SIZE][/FONT]  
  [FONT=Verdana][SIZE=2]          inet addr:169.254.5.228  Bcast:169.254.255.255  Mask:255.255.0.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]Interrupt:5 Base address:0x6000 [/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2]
lo        Link encap:Local Loopback  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX packets:3596 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]TX packets:3596 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]collisions:0 txqueuelen:0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX bytes:179800 (175.5 KB)  TX bytes:179800 (175.5 KB)[/SIZE][/FONT]
  
  
  [FONT=Verdana][SIZE=2]ppp0      Link encap:Point-to-Point Protocol  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]inet addr:192.168.9.1  P-t-P:192.168.9.100  Mask:255.255.255.255[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX packets:2429 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]TX packets:25 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]collisions:0 txqueuelen:3 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]RX bytes:155317 (151.6 KB)  TX bytes:1784 (1.7 KB)[/SIZE][/FONT]



[FONT=Verdana][SIZE=2]I do not understand why I cannot ping 192.168.5.100, but not .101[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]I have opened the Asterisk Sip Server to accept connections from 192.168.2.0, 192.168.5.0, and 192.168.9.0 subnets.[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Any help would be appreciated.[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by dieterhund on 2010-08-12
Was a gateway problem on the SIP server.

---

