---
title: "Can't set up my LAN Internet connection!"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by pan4o16 on 2009-09-10
Hi :) I am new in Ubuntu. I have just instaled Ubuntu OS on my PC. Now I have 2 OS on that PC - Windows XP and Ubuntu. On my Windows There is no problems with my Internet settings. But on Ubuntu :( :( :( I have no problem entering my Internet settings (IP,DNS, MAC) .when I do that it shows me that i am connected BUT I still DONT HAVE INTERNET. PLS help me ASAP!!!

---

### Post by Iowan on 2009-09-10
Post results of **ifconfig -a** (from a terminal)

---

### Post by pan4o16 on 2009-09-10
panteley@ubuntu:~$ ifconfig -a
eth3      Link encap:Ethernet  HWaddr 00:20:ed:43:b7:27  
          inet addr:192.168.16.109  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe43:b727/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1380 (1.3 KB)  TX bytes:16916 (16.9 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 42:05:24:f8:34:35  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

(BTW these settings are not my correct internet settings - HWaddr 00:20:ed:43:b7:27  
          inet addr:192.168.16.109  Bcast:192.168.16.255. NOT CORRECT!!!)

---

### Post by pan4o16 on 2009-09-10
Bump!! PLS HELP!

---

### Post by Iowan on 2009-09-10
> **pan4o16 said:**
> Bump!! PLS HELP!Patience... It might take more than an hour to get results.
Are you getting an IP address via DHCP, or did you enter it manually in Network Manager or */etc/network/interfaces*? 
The eth3 is kinda curious - I'd expect eth0.

---

### Post by pan4o16 on 2009-09-10
I enter my IP manualy trough Network connections wwindow (not terminal or other way)

---

### Post by pan4o16 on 2009-09-11
Bump! Bump!

---

