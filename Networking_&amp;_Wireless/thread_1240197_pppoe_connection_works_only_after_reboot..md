---
title: "pppoe connection works only after reboot."
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by kaushlesh on 2009-08-14
I have wicd as network manager. It detects my wifi fine. But i fail to connect to internet even after running pppoeconf and getting everything proper. Then I reboot and get connected to internet without even running pppoeconf. This happens everytime my brother has logged in just before me using his own account which has limited privileges.

---

### Post by superprash2003 on 2009-08-14
post output of **ifconfig** from the terminal when your internet works and also when it doesnt

---

### Post by kaushlesh on 2009-08-16
[SIZE=4]**When internet dowsn't works.....**[/SIZE]
ppp0      Link encap:point-to-Point Protocol  
          inet addr:117.198.37.37  P-t-P:117.198.32.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:514 (514.0 B)  TX bytes:54 (54.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:27:c2:71:11  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:27ff:fec2:7111/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21440 (21.4 KB)  TX bytes:34609 (34.6 KB)

[SIZE=4]**When internet works.....**[/SIZE]

ppp0      Link encap:point-to-Point Protocol  
          inet addr:117.198.36.219  P-t-P:117.198.32.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:2404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2196092 (2.1 MB)  TX bytes:361313 (361.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:27:c2:71:11  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:27ff:fec2:7111/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2251011 (2.2 MB)  TX bytes:459286 (459.2 KB)


They both look the same to me.....

---

### Post by harry2006 on 2009-08-16
rebooting autodetects the networks and hence it works fine....and limited-priv acc seems to mess around with that

---

### Post by superprash2003 on 2009-08-17
post output of **ping 192.168.1.1 **, when you are not able to connect

---

