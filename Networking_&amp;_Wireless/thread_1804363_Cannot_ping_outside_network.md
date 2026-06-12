---
title: "Cannot ping outside network"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by jedan83 on 2011-07-14
i have problem ubuntu server network! internet works but 
#cant ping google.com  and outside ip  ??
#what your wrong

####################
igor@zoky:~$ ping 66.102.11.104
PING 66.102.11.104 (66.102.11.104) 56(84) bytes of data.
tanks

---

### Post by jedan83 on 2011-07-14
i have problem ping google.com server or outside network?
$ping google.com dont work or everside network why?
tanks

---

### Post by Iowan on 2011-07-14
Merged post with thread...
"Everside"?

Does it work to ping by IP address? (eg. 74.125.225.51)

---

### Post by jedan83 on 2011-07-14
#ping  ip address  dont ping  i have change mtu size but dont work! why ubuntu ping outside dont work! help me tanks -ping google.com ............................

---

### Post by pakidevil on 2011-07-16
make sure, firewall is blocking ... most of the time, this is the issue ..

---

### Post by jedan83 on 2011-07-16
firewall disable or router!

firewall default is ubuntu??
how to disable ubuntu firewall?
tanks

---

### Post by jmoorse on 2011-07-16
Please post the output of:

ifconfig -a

route -n

traceroute 8.8.8.8

---

### Post by jedan83 on 2011-07-17
ip ubuntu 192.168.2.2 gateway 192.168.2.1 etc/resolv.conf, but  primary dns 8.8.4.4 dont work network dns 192.168.2.1 dns 8.8.4.4 igor@zoky:~$ ping facebook.com PING facebook.com (69.63.189.11) 56(84) bytes of data.  #igor@zoky:~$ ifconfig -a eth0      Link encap:Ethernet  HWaddr 18:a9:05:2b:c5:ea             inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0           UP BROADCAST RUNNING MULTICAST  MTU:1480  Metric:1           RX packets:107130728 errors:0 dropped:0 overruns:0 frame:0           TX packets:123270024 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:993750824 (993.7 MB)  TX bytes:3752724524 (3.7 GB)           Interrupt:42 Base address:0xe000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:3072 errors:0 dropped:0 overruns:0 frame:0           TX packets:3072 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:693232 (693.2 KB)  TX bytes:693232 (693.2 KB) Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0  igor@zoky:~$ traceroute 8.8.4.4 traceroute to 8.8.4.4 (8.8.4.4), 30 hops max, 60 byte packets  1  192.168.2.1 (192.168.2.1)  0.698 ms  0.665 ms  0.638 ms  2  * * *  3  * * *  4  * * *  5  * * * tanks!

---

### Post by jmoorse on 2011-07-17
Can you fix the formatting on that?

---

### Post by jedan83 on 2011-07-17
ip ubuntu 192.168.2.2 gateway 192.168.2.1 etc/resolv.conf,  dns 192.168.2.1 dns 8.8.4.4 igor@zoky:~$ ping facebook.com PING facebook.com (69.63.189.11) 56(84) bytes of data.

---

### Post by jedan83 on 2011-07-17
[LEFT]#igor@zoky:~$
 ifconfig -a eth0      Link encap:Ethernet  HWaddr 18:a9:05:2b:c5:ea             inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0           UP BROADCAST RUNNING MULTICAST  MTU:1480  Metric:1           RX packets:107130728 errors:0 dropped:0 overruns:0 frame:0           TX packets:123270024 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:993750824 (993.7 MB)  TX bytes:3752724524 (3.7 GB)           Interrupt:42 Base address:0xe000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:3072 errors:0 dropped:0 overruns:0 frame:0           TX packets:3072 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:693232 (693.2 KB)  TX bytes:693232 (693.2 KB)[/LEFT]

---

### Post by jedan83 on 2011-07-17
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

igor@zoky:~$ traceroute 8.8.4.4
traceroute to 8.8.4.4 (8.8.4.4), 30 hops max, 60 byte packets
 1  192.168.2.1 (192.168.2.1)  0.698 ms  0.665 ms  0.638 ms
 2  * * *
 3  * * *
 4  * * *
[LEFT] 5  * * *
[/LEFT]

---

### Post by jedan83 on 2011-07-17
> **jmoorse said:**
> Can you fix the formatting on that?
can you fix formating????
tanks

---

### Post by jmoorse on 2011-07-17
> **jedan83 said:**
> 
igor@zoky:~$ traceroute 8.8.4.4
traceroute to 8.8.4.4 (8.8.4.4), 30 hops max, 60 byte packets
 1  192.168.2.1 (192.168.2.1)  0.698 ms  0.665 ms  0.638 ms
 2  * * *
 3  * * *
 4  * * *
[LEFT] 5  * * *
[/LEFT]

It looks like ICMP is being blocked either by your Router's firewall inbound, or by your service provider.  Please check your router (refer to manufacturer) or contact your ISP.

---

### Post by jedan83 on 2011-07-17
> **jmoorse said:**
> It looks like ICMP is being blocked either by your Router's firewall inbound, or by your service provider.  Please check your router (refer to manufacturer) or contact your ISP.
-isp provider dont block icmp protocol
# i have mikrotik router but disable firewall  !????????'
are dont now?   tanks!

---

### Post by jmoorse on 2011-07-17
> **jedan83 said:**
> -isp provider dont block icmp protocol
# i have mikrotik router but disable firewall  !????????'
are dont now?   tanks!

No, don't disable the firewall.  Just disable ICMP filtering if you really care about pinging out...

---

### Post by jedan83 on 2011-07-17
add chain=forward action=accept protocol=icmp icmp-options=0:0 
add chain=forward action=accept protocol=icmp icmp-options=3:0 
add chain=forward action=accept protocol=icmp icmp-options=3:1 
add chain=forward action=accept protocol=icmp icmp-options=4:0 
add chain=forward action=accept protocol=icmp icmp-options=8:0 
add chain=forward action=accept protocol=icmp icmp-options=11:0 
add chain=forward action=accept protocol=icmp icmp-options=12:0 
icmp

---

### Post by jmoorse on 2011-07-17
> **jedan83 said:**
> add chain=forward action=accept protocol=icmp icmp-options=0:0 
add chain=forward action=accept protocol=icmp icmp-options=3:0 
add chain=forward action=accept protocol=icmp icmp-options=3:1 
add chain=forward action=accept protocol=icmp icmp-options=4:0 
add chain=forward action=accept protocol=icmp icmp-options=8:0 
add chain=forward action=accept protocol=icmp icmp-options=11:0 
add chain=forward action=accept protocol=icmp icmp-options=12:0 
icmp

Make sure you are doing this on your router's firewall, not on Ubuntu.  Traceroute shows you receive ICMP TTL exceeded from your gateway just fine.
> **jedan83 said:**
> igor@zoky:~$ traceroute 8.8.4.4
traceroute to 8.8.4.4 (8.8.4.4), 30 hops max, 60 byte packets
1 192.168.2.1 (192.168.2.1) 0.698 ms 0.665 ms 0.638 ms


---

