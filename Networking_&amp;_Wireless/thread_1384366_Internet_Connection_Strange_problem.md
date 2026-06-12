---
title: "Internet Connection Strange problem"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by waqarlatif on 2010-01-18
Hello 

 I am using Ubuntu 9.10 ...... and i am facing strange problem using my INTERNET..... having NIC of RealTek RTL8139 built-in in my Presario v5000........ when i use eth0  gets the ip from DHCP but i was unable to connect to internet even i couldn't ping my  dsl modem...... after that when i restart my network and network-manager many times ....luckly some times i get connect but most of the time i failed to connect ..........Plz do help me i am in very  strange problem........:(

ifconfig : output 


eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c3:1a:f3  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fec3:1af3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35713 (35.7 KB)  TX bytes:59985 (59.9 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I am waiting plzzzz reply what should i do

---

### Post by waqarlatif on 2010-01-19
Hey isn't there anyone who can solve my problem ....... i know its kind a weird problem so what u suggest....what should i do

---

### Post by evatw001 on 2010-01-19
try latest driver for your nic card.

---

### Post by waqarlatif on 2010-01-20
Thnx all of you ........... I solved my problem by myself

---

### Post by rayefrenzy on 2010-01-20
How did you solve it? I am having a similar problem with my compaq presario v5000.

---

