---
title: "PPP Not Enabled"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by mikecanada on 2009-05-29
Could anyone please spare a minute to help me get on line ? The os is 9.04 Ubuntu and it dials out but will not connect properly,it states.... ppp not enabled...............This prevents the last part to connect.What do I need to do to correct this ? Thanks Mike

---

### Post by superprash2003 on 2009-05-30
is this a DSL connection?? in your terminal type ifconfig and post output

---

### Post by mikecanada on 2009-05-30
Hi and thabks for helping it is a dial up internal hardware modem.I did what you said and this is it.....mike@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:d8:0b:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4652 (4.6 KB)  TX bytes:4652 (4.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.73.4.154  P-t-P:204.101.237.225  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1497923 (1.4 MB)  TX bytes:326434 (326.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:5b:3b:81:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-3B-81-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mikecanada on 2009-06-02
Bump

---

