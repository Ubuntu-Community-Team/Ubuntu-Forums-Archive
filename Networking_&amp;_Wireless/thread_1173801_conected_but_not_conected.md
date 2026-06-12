---
title: "conected but not conected"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by simon dew on 2009-05-30
I'm having a weird issue with the wireless connection on my Asus Eee. It has recently developed an issue where it says its connected to the wireless network but I can't access the net or transfer data vi any other program. It's not the network itself as that is working fine on my XP laptop. It has worked flawlessly up until this evening and I could use some help. 
Regards

Simon

---

### Post by superprash2003 on 2009-05-30
are you able to ping websites during this time?? post output of ifconfig from the terminal

---

### Post by roman_platonov on 2009-05-30
check ip setting and signal strength.

---

### Post by simon dew on 2009-05-30
simon@simon-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:1e:22:85  
          inet6 addr: fe80::21f:c6ff:fe1e:2285/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:384679 (384.6 KB)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7076 (7.0 KB)  TX bytes:7076 (7.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:81:dd:0b  
          inet addr:10.1.1.34  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::215:afff:fe81:dd0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8223 (8.2 KB)  TX bytes:30363 (30.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-81-DD-0B-64-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

simon@simon-laptop:~$ 

Thanks for the assistance

S.

---

### Post by superprash2003 on 2009-05-31
try pinging website like
1)ping google.com
2)ping 208.67.222.222

---

### Post by simon dew on 2009-06-01
simon@simon-laptop:~$ ping google.com
ping: unknown host google.com
simon@simon-laptop:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

a mixed result?
s

---

### Post by superprash2003 on 2009-06-01
in your terminal type
1)sudo ifdown eth0
2)sudo ifdown wmaster0

 now type in commands in post no 5 , and post output again

---

### Post by simon dew on 2009-06-03
hi again. I did as you said but got the same result as before:
simon@simon-laptop:~$ ping google.com
ping: unknown host google.com
simon@simon-laptop:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

S.

---

### Post by superprash2003 on 2009-06-03
post output of the following
1)sudo iptables -L
2)route -n

---

### Post by simon dew on 2009-06-05
simon@simon-laptop:~$ sudo iptables -L
[sudo] password for simon: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
simon@simon-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     2      0        0 wlan0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0
simon@simon-laptop:~$

---

### Post by simon dew on 2009-06-17
sorted! It was some form of wireless router problem which I have now fixwd by resetting up the router. Thanks for all the help.
Cheers
Simon

---

