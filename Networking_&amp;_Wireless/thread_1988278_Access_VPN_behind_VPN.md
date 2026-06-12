---
title: "Access VPN behind VPN"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by Martje_001 on 2012-05-27
Hi all,

OK, so the title is a bit vague, but let me explain. I have a server which connects to a VPN using ppp. All traffic for a specific network range (130.89.0.0) it routed through it. This works fine, as you can see here [COLOR="Silver"](Although the IP is publicly accessible, the service running on that particular machine is only available for computers within the said range. And yes, it functions :-).)[/COLOR]:

```
Martje_001@desktop:~$ ssh server 
Martje_001@server:~$ ping 130.89.163.107
PING 130.89.163.107 (130.89.163.107) 56(84) bytes of data.
64 bytes from 130.89.163.107: icmp_req=1 ttl=61 time=3.66 ms

```

My server, in its turn, runs an OpenVPN service providing a secure internet connection for its users. However, when I try to connect to an IP-address within the range 130.89.0.0 when connected to my own VPN, nothing happens. For example, ping hangs on:

```
Martje_001@desktop:~$ ping 130.89.163.107
PING 130.89.163.107 (130.89.163.107) 56(84) bytes of data.

```

When I *don't* use a VPN connection (on my desktop), I can ping just fine to 130.89.163.107. I have no idea what to do next. Maybe you can help me?

**Graphical representation:**
[IMG]https://www.mbastiaan.nl/users/martijn/Afbeeldingen/Ubuntu.Forum/VPNBehindVPN.png[/IMG]

[B]Extra info:
[/B]```
Martje_001@server:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         82.94.167.1     0.0.0.0         UG    100    0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
82.94.167.0     0.0.0.0         255.255.255.128 U     0      0        0 eth0
130.89.0.0      130.89.98.25    255.255.0.0     UG    0      0        0 ppp0
130.89.254.237  82.94.167.1     255.255.255.255 UGH   0      0        0 eth0
130.89.254.238  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

Martje_001@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e6:66:6f:26:ab:f7  
          inet addr:82.94.167.xx  Bcast:82.94.167.255  Mask:255.255.255.128
          inet6 addr: fe80::e466:6fff:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22275951 errors:0 dropped:5783 overruns:0 frame:0
          TX packets:26409581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13520095332 (13.5 GB)  TX bytes:26214719061 (26.2 GB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11232507 (11.2 MB)  TX bytes:11232507 (11.2 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:130.89.98.25  P-t-P:130.89.254.238  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:100463 (100.4 KB)  TX bytes:26285 (26.2 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:324641 (324.6 KB)  TX bytes:1945492 (1.9 MB)


```

---

### Post by Martje_001 on 2012-05-27
I solved it! :-)

Turns out I had to use NAT to translate traffic coming from the VPN to the ppp tunnel. This is how I did it:

```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -A FORWARD -s 10.8.0.0 -d 130.89.0.0 -o ppp0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 130.89.0.0 -d 10.8.0.0 -i ppp0 -j ACCEPT

```

Breaking it down:
[LIST=1]
[*]Enable nat for ppp0 (create a translation table);
[*]Forward all traffic coming from 10.8.0.0 (the address range given to VPN clients) and forward it to pp0, if the destination equals 130.89.0.0;
[*]Forward traffic coming from 130.89.0.0 and pp0, and send it to the original source (130.89.0.0);
[/LIST]

I really couldn't be happier right now :-)!

---

