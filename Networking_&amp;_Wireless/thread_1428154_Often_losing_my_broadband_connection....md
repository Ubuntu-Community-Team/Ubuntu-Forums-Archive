---
title: "Often losing my broadband connection..."
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2010-03-12
I am using ubuntu 9.04 and i am losing my internet connectivity often...Can someone tell me the cause for this problem?These are the the outputs.....


```
karthick@Learners-desktop:~$** ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:17:70  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:feab:1770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:946049 (946.0 KB)  TX bytes:119465 (119.4 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.92.122.66  P-t-P:59.92.112.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:916363 (916.3 KB)  TX bytes:100177 (100.1 KB)


karthick@Learners-desktop:~$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.


karthick@Learners-desktop:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.92.112.1     *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

```

---

### Post by karthick87 on 2010-03-14
Bump..

---

