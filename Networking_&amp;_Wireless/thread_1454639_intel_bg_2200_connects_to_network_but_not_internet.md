---
title: "intel bg 2200 connects to network but not internet (ubuntu 9.10 &amp; 10.04)"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by zbeefy on 2010-04-14
Hi guys, 

I'm forced to to this so I can resolve this problem :confused:, please bear with me... I've got:
-Dell XPS m140 laptop with wireless intel bg 2200
-Netgear WPN824 v3 wireless router
-Vonage telephone modem
-Comcast Cable internet
-Upgraded from Ubuntu 9.10 to 10.04 (thought it could resolve the problem)

Now comes the funky part:

I had to bypass Vonage modem and set the WPN824 v3 wireless router to obtain public DNS addresses manually from 208.67.220.220 and 208.67.222.222. My other computer (Windows 7) works without any problems with these settings, BUT my Dell XPS m140 laptop (Ubuntu 10.04) doesn't seem to be able to browse online. What I mean exactly is that the Network Manager will show the connection as estabilished, and will actually get the IP address from the router, but I still can't even open the google website. I tried setting the Network Manager to both Automatic DHCP, and Automatic DHCP (addresses only) to direct it towards DNS addresses the router provides; I also tried changing encryption from WEP to WPA & WPA2 PERSONAL... but no luck, even ping hangs on me. I don't know where the problem is. It started suddenly after a month or so with Karmic Koala. Both linux installations were post-format and clean. Cat5 cable connection will work perfectly...

I don't know if this will help, but here's my ifconfig. The confusing part is that it shows packets sent and received on eth1 (wireless), but I'm not able to browse....

root@laptop-laptop:/home/laptop# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:99:ba:5d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:47:ab:02  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe47:ab02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:2 dropped:2 overruns:0 frame:0
          TX packets:252 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33781 (33.7 KB)  TX bytes:24979 (24.9 KB)
          Interrupt:17 Base address:0xa000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1088 (1.0 KB)  TX bytes:1088 (1.0 KB)


Thanks a lot for any help and sorry if i sounded dumb, I just started learning a month ago.

---

### Post by zbeefy on 2010-04-26
Ok. I solved it. Turned out it was the Comcast issue with the wiring.

---

