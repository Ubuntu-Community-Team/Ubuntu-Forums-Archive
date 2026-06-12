---
title: "Connection issues with Ubuntu 11.04"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by schattengarde on 2011-07-07
I have an Asus 1005HA netbook. Previously to upgrading, I was running Netbook remix, but was told that it wasn't supported anymore (and it was coming time to reinstall everything anyway) so I put regular Ubuntu 11.04 on it. Since I upgraded, I've been unable to access the internet.  I finally got it to recognize that there was a connection at all by disabling DHCP and giving it a static IP address. Now it will act like it's connected to the ethernet, but cannot get to the internet. I've also tried pinging it from another machine on the network and the request times out.

Help?

---

### Post by schattengarde on 2011-07-07
To make things easier, here's the results from ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:26:18:80:99:af   
           inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::226:18ff:fe80:99af/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:288 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1071 errors:0 dropped:0 overruns:0 carrier:3  
           collisions:0 txqueuelen:1000  
           RX bytes:57257 (57.2 KB)  TX bytes:85378 (85.3 KB)  
           Interrupt:45  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:825 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:825 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:82633 (82.6 KB)  TX bytes:82633 (82.6 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:25:d3:38:cc:78   
           inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::225:d3ff:fe38:cc78/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:2690 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:120 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:599343 (599.3 KB)  TX bytes:31425 (31.4 KB)

---

### Post by schattengarde on 2011-07-07
Update: The wireless works, it's apparently only the ethernet connection that's screwy.

---

