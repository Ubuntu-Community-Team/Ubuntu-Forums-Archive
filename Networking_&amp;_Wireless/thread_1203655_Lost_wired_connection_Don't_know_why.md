---
title: "Lost wired connection? Don't know why"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by jb09 on 2009-07-03
I had the wired connection working with ubuntu. Right after installing it worked from the get go. But now it will not detect the connection. Using Windows on it right now to make this post. Have no wireless card for the computer.

---

### Post by 007casper on 2009-07-03
in the terminal write
> ifconfig

what does ifconfig show?

---

### Post by Iowan on 2009-07-03
Kinda sounds like what happened to my laptop, [here]("http://ubuntuforums.org/showthread.php?t=1156441").

---

### Post by jb09 on 2009-07-04
ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:40:ca:5b:c3:30  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe5b:c330/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:490 (490.0 B)  TX bytes:5362 (5.3 KB)
          Interrupt:18 Base address:0xd800 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28157 (28.1 KB)  TX bytes:28157 (28.1 KB)
virbr0    Link encap:Ethernet  HWaddr 16:ac:2a:e4:fd:5c  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::14ac:2aff:fee4:fd5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5362 (5.3 KB)

---

### Post by Iowan on 2009-07-04
> **jb09 said:**
> ifconfig shows:
...
virbr0    Link encap:Ethernet  HWaddr 16:ac:2a:e4:fd:5c  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::14ac:2aff:fee4:fd5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5362 (5.3 KB)This is a new one for me - but I haven't used bridging.

---

### Post by jb09 on 2009-07-04
I don't have a bridge. I have the dsl router connected the a wireless router with 4 ports. And the computer directly to the wireless router, just hard wired. 
 
If I'm correct a bridge is used with two wireless routers, I have one.

---

### Post by Iowan on 2009-07-04
In that case, the **virbr0** (virtual bridge??) might be part of the problem...

---

