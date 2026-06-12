---
title: "Strange LAN problem"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by tezer on 2009-02-24
Hello
Could you please help me to solve my LAN problem.
I have three computers (laptop - Mint 6, desktop - Mint 6, server - Ubuntu Server 8.10, btw Mint 6 is almost the same as Ububntu 8.10). All of them are connected through a router (laptop - wirelessly).

The problem is that both laptop and desktop can't see each other. No ssh connection:

```
ssh: connect to host 192.168.2.3 port 22: Connection refused
```

But all the computers can easily connect to the server and I can ping either of the computers from the other one. Port 22 is open on all computers.

What is the problem?

PS I can't ssh from the server either...

ifconfig for the desktop:
```
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:89:fb:14  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:264080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182314 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:191388866 (191.3 MB)  TX bytes:17373731 (17.3 MB)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:16 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          &#1042;&#1042;&#1045;&#1056;&#1061; LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1573 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:46457 (46.4 KB)  TX bytes:46457 (46.4 KB)
```

ifconfig for the laptop:
```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:9f:15:ca
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:dc:77:aa
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:398331 (398.3 KB)  TX bytes:121099 (121.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr
00-13-02-DC-77-AA-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by cariboo on 2009-02-24
Do you have openssh-server installed on the computers you are trying to connect to?

Jim

---

### Post by tezer on 2009-02-25
Thanks, Jim. I didn't even think that the server wasn't installed....

---

