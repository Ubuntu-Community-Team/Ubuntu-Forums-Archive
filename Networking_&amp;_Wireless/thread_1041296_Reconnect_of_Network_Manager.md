---
title: "Reconnect of Network Manager"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by zelfeed on 2009-01-16
Hello. I have an unstable internet connection. I use Network Manager 0.7.0 (Ubuntu 8.10), dsl-modem connecting to pc's ethernet card. Then internet connection lost, NM goes to disabled mode and don't try to reconnect. How do I have to do that NM try to reconnect (if connection lost) periodical (example, one try of every 30 sec)?

---

### Post by mikewhatever on 2009-01-16
Can you post the output of <ifconfig>. Sometimes, disconnections are  simply an MTU problem which is easily corrected.

---

### Post by zelfeed on 2009-01-18
> **mikewhatever said:**
> Can you post the output of <ifconfig>. Sometimes, disconnections are  simply an MTU problem which is easily corrected.

eth0      Link encap:Ethernet  HWaddr 00:0d:61:b6:c2:19  
          inet6 addr: fe80::20d:61ff:feb6:c219/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130856 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:54456999 (54.4 MB)  TX bytes:13491715 (13.4 MB)

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          &#1042;&#1042;&#1045;&#1056;&#1061; LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117266 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:22127517 (22.1 MB)  TX bytes:22127517 (22.1 MB)

ppp0      Link encap:&#1055;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083; PPP (Point-to-Point Protocol)  
          inet addr:10.x.x.x  P-t-P:217.x.x.x  Mask:255.255.255.255
          &#1042;&#1042;&#1045;&#1056;&#1061; POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:8631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10411 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:3 
          RX bytes:6713604 (6.7 MB)  TX bytes:1540823 (1.5 MB)

-=-=-=-=-=-=-=-=-=-

But I thought, that was an option (like "persist" in /etc/ppp/peers/dsl-provider) in /etc/NetworkManager/nm-system-settings.conf... :roll:

---

