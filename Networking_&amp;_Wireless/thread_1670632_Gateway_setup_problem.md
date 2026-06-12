---
title: "Gateway setup problem"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by Sergei_K on 2011-01-19
Hi everyone.
Need help. 
Initiall: 1. Ubuntu 10.10 gateway
2. Ubuntu 10.10 client
3. DIR-300
Computer 1 connects to internet through usb modem ADU-100, I've set up the connection via gnome-ppp. Via eth1 computer 1 connected to DIR-300 LAN port. The 2nd computer connected through eth0 to another LAN port of DIR-300. I've set up masquarading on computer one, dnsmasq, so everything seems to work fine. I've got my internet sharing working fine. But after a few minutes the ppp connection on computer 1 starts to disconnect time after time. When I put eth1 on computer 1 down, connection works fine again.
It doesn't happen when I connect to the gateway via DIR-300 wifi using windows laptop.
 
Here's my route -n
Destination Gateway Genmask Flags Metric Ref Use Iface
91.149.120.19 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.0.0 192.168.0.1 255.255.255.0 UG 0 0 0 eth1
0.0.0.0 91.149.120.19 0.0.0.0 UG 0 0 0 ppp0
 
ifconfig
eth1 Link encap:Ethernet HWaddr 00:e0:52:98:64:7b 
inet addr:192.168.0.1 Bcast:192.168.0.0 Mask:255.255.255.0
inet6 addr: fe80::2e0:52ff:fe98:647b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:7867 errors:0 dropped:763 overruns:0 frame:0
TX packets:7624 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:811007 (811.0 KB) TX bytes:2132238 (2.1 MB)
Interrupt:23 Base address:0xe800 
 
lo Link encap:loopback (Loopback) 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:901 errors:0 dropped:0 overruns:0 frame:0
TX packets:901 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:59568 (59.5 KB) TX bytes:59568 (59.5 KB)
 
ppp0 Link encap:Protocol PPP (Point-to-Point Protocol) 
inet addr:91.149.121.91 P-t-P:91.149.120.19 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1
RX packets:3311 errors:0 dropped:0 overruns:0 frame:0
TX packets:3420 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:2338052 (2.3 MB) TX bytes:490613 (490.6 KB)
 
would appreciate any help
thanks in advance

---

