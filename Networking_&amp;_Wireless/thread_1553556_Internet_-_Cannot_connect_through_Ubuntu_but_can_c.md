---
title: "Internet - Cannot connect through Ubuntu but can connect through XP on VMware"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by e-meditator on 2010-08-15
Hello
I had put my computer on standby and when i restarted it, it powered off within a few seconds. I turned it back on and after that i've lost connectivity to internet on Ubuntu 10.04.
However I have VMware (XP) installed and internet/network works on that. I'm a newbie with Linux. 
here are some outputs:
$ ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:1f:c6:d0:02:d7 
inet addr:192.168.100.36 Bcast:192.168.100.255 Mask:255.255.255.0
inet6 addr: fe80::21f:c6ff:fed0:2d7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:17507 errors:1 dropped:0 overruns:0 frame:1
TX packets:6371 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:9503199 (9.5 MB) TX bytes:1115826 (1.1 MB)
Interrupt:27 
 
$ sudo route add -net 192.168.100.2 netmask 255.255.255.0 eth0
route: netmask doesn't match route address
 
I have tried to edit the connection using System>Preferences>Network Connections. I entered manual settings for IPV4, but whatever i enter there, it doesnt get reflected when i type ifconfig in the terminal window. I tried setting it to Automatic DHCP as well. Doesnt work. 
 
Could someone help me out please? Thanks so much.

---

### Post by e-meditator on 2010-08-15
Solved - had to add nameserver 8.8.8.8 to the /etc/resolv.conf file - got solution from #Ubuntu on IRC

---

