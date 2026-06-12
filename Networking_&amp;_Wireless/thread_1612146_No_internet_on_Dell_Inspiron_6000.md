---
title: "No internet on Dell Inspiron 6000"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Meegle on 2010-11-02
Hi all, noob here. I installed Ubuntu 10.10 on a Dell Inspiron 6000 but when I connect the ethernet cable the computer detects that the cable was connected but doesnt connect to the internet. Can anyone help me?

---

### Post by Iowan on 2010-11-02
From a terminal (Applications>Accessories>Terminal) check **ifconfig -a** to see if the interface gets an IP address.

---

### Post by Meegle on 2010-11-03
Ok i did that, and this is what I got:


eth0      Link encap:Ethernet  HWaddr 00:12:3f:eb:98:a2  
          inet6 addr: fe80::212:3fff:feeb:98a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149228 (149.2 KB)  TX bytes:5049 (5.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:39:6b:36  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Meegle on 2010-11-04
Anyone? Please?

---

### Post by dineshs on 2010-11-05
post the result of```
sudo dhclient eth0
```

---

