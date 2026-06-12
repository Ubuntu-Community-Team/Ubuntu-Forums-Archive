---
title: "Unable to start internet connection"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by chahat on 2012-05-22
I am having problems in connecting to internet.i have installed ubuntu 12.04 and even when my ethernet cable is connected,it says that the wired connection is disconnected,and i am offline.I haven't done any internet connection setup as of now.I have a broadband connection.
Please help me in connecting to internet,as i want some important updates,thanks.

---

### Post by MichaelGld on 2012-05-22
Open a terminal and type** ifconfig -a** and post the results.

---

### Post by chahat on 2012-05-23
Thanks for the quick reply.
Here are the ifconfig -a  results:

eth0      Link encap:Ethernet  HWaddr 00:24:54:82:bf:bc   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB) 

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:6e:b3:ab   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

Please help anyone,thanks.

---

