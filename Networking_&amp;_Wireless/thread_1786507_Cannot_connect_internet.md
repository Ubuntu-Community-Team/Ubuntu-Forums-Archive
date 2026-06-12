---
title: "Cannot connect internet"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by nickliutw on 2011-06-19
I'm using ubuntu 8.10. I used to connect the internet with wire and wireless. But some reason, I cannot connect internet with wire nor wireless. I'm not sure what happen. I already test the internet on Windows 7 and it just works fine. Can anyone help me solve this problem? By the way, I also change my router to cisco linksys e2000, and I have the internet and other stuff set up in windows, already. I just cannot connect the internet when I'm using ubuntu.

---

### Post by Iowan on 2011-06-19
Does the machine get an IP address? 
That information is available in a terminal (Applications>Accessories>Terminal) via **ifconfig -a**.

---

### Post by pdkta on 2011-06-19
upgrade to 11.04 could solve the problem!!!!!! :-)

---

### Post by nickliutw on 2011-06-20
This is what I have after I type ifconfig -a in the terminal. I'm not sure whether I do get teh ip address or not.

eth0      Link encap:Ethernet  HWaddr 00:18:f3:ae:5d:84  
          inet6 addr: fe80::218:f3ff:feae:5d84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4811 (4.8 KB)  TX bytes:1530 (1.5 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:07:4e:52  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-39-07-4E-52-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by clbaines on 2011-06-22
> **pdkta said:**
> upgrade to 11.04 could solve the problem!!!!!! :-)

It may not solve the problem. I am runnig 11.04 and I just got a new E2000 router. I cannot connect wireless. Only connect wireless as a guest.

---

