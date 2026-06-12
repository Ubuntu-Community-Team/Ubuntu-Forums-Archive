---
title: "No access to wi-fi router. But ping is ok..."
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by tunasalat on 2011-06-20
Ubuntu 10.04 2.6.32
I have a wi-fi router dlink di-524.
I can ping it, but i can't access to it via the browser.
```
woody@woody-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.419 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.439 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.365 ms
^C
--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.365/0.407/0.439/0.039 ms


woody@woody-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:61:62:59:16  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe62:5916/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:7998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6631970 (6.6 MB)  TX bytes:1652839 (1.6 MB)
          Interrupt:19 Base address:0x9000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:406209 (406.2 KB)  TX bytes:406209 (406.2 KB)


woody@woody-desktop:~$ arp -v
&#1040;&#1076;&#1088;&#1077;&#1089; HW-&#1090;&#1080;&#1087; HW-&#1072;&#1076;&#1088;&#1077;&#1089; &#1060;&#1083;&#1072;&#1075;&#1080; &#1052;&#1072;&#1089;&#1082;&#1072; &#1048;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;
192.168.0.1              ether   00:13:46:50:87:1b   C                     eth0
&#1047;&#1072;&#1087;&#1080;&#1089;&#1077;&#1081;: 1    &#1055;&#1088;&#1086;&#1087;&#1091;&#1097;&#1077;&#1085;&#1086;: 0    &#1053;&#1072;&#1081;&#1076;&#1077;&#1085;&#1086;: 1
woody@woody-desktop:~$ 

woody@woody-desktop:~$ route
&#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1084;&#1072;&#1088;&#1096;&#1091;&#1090;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; &#1103;&#1076;&#1088;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1072; IP
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
woody@woody-desktop:~$ 
```

i also can't telnet it and i can't connect using dhcp.
I use network manager.
Please help me.

---

### Post by Iowan on 2011-06-20
What message is displayed when you attempt access via browser?
(Are you attempting via name - or IP?)

---

### Post by tunasalat on 2011-06-21
I have "connection timed out". I access it by IP. When i try to telnet it (I hope my router supports telnet) I also have "connection timed out".

---

### Post by tunasalat on 2011-06-21
That was a device problem. Firmware update was done wrong and router went bad. I reinstalled the firmware via tftp and now everything's ok.
Thank you.

---

