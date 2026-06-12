---
title: "network &amp; internet have gone"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by charlie0440 on 2010-10-21
After a recent dist-upgrade I have lost my network.
There is no Network manager icon in the top corner
My switch and the RJ45 port on the PC are both lit green and connected. There is an internet connection from the other PC on the LAN

uname -r
2.6.32-25-generic

ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140264 (140.2 KB)  TX bytes:140264 (140.2 KB)

ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:26:18:23:0a:c5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:143264 (143.2 KB)  TX bytes:143264 (143.2 KB)

I have tried: sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0 up

ifconfig then gives me:
eth0      Link encap:Ethernet  HWaddr 00:26:18:23:0a:c5  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe23:ac5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540 (540.0 B)  TX bytes:4802 (4.8 KB)
          Interrupt:29 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148064 (148.0 KB)  TX bytes:148064 (148.0 KB)

I am now able to ping the other PC on the LAN but still no internet!
My router is at 192.168.0.1 so I have also tried:
sudo route add default gw 192.168.0.1
It did not appear to do anything.
Can someone please help!

---

### Post by zarqoon on 2010-10-23
Is your entire notification-area-applet gone? If yes try to add it to the panel again.
It looks like your network is just disabled. If you add the notification-area it might be just a matter of enabling it again.

If you enable it like you described and set the gw route you should have internet but you did not set dns servers which auto eth0 would have done for you with the help of your dhcp server. Iam guessing ip access would have worked.

---

