---
title: "pptp routing thing..."
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by firewalkswme on 2009-01-20
Hi!
i'm not a pptp/vpn expert and it's my first time being here so pls be patient.
here is my problem: i have slack 12.1. used to get online thru vpn tunnel but for whatever reason it stoped working. 
here is what my debug stuff looks like:

pppd debug call MYISP

Jan 20 14:50:22 naycmax pppd[3072]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5d718ad9> <pcomp> <accomp>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [LCP ConfReq id=0x1 <accomp> <pcomp> <asyncmap 0x0> <mru 1490> <magic 0x547a4bf9> <quality lqr 00 00 01 2c> <auth chap MD5>]
Jan 20 14:50:23 naycmax pppd[3072]: sent [LCP ConfRej id=0x1 <quality lqr 00 00 01 2c>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5d718ad9> <pcomp> <accomp>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [LCP ConfReq id=0x2 <accomp> <pcomp> <asyncmap 0x0> <mru 1490> <magic 0x547a4bf9> <auth chap MD5>]
Jan 20 14:50:23 naycmax pppd[3072]: sent [LCP ConfAck id=0x2 <accomp> <pcomp> <asyncmap 0x0> <mru 1490> <magic 0x547a4bf9> <auth chap MD5>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [CHAP Challenge id=0x1 <33353830323530303231353437383134>, name = ""]
Jan 20 14:50:23 naycmax pppd[3072]: sent [CHAP Response id=0x1 <e07b8c73287dfddb8d2475a358a82da0>, name = "MYNAME"]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [CHAP Success id=0x1 "Welcome!!"]
Jan 20 14:50:23 naycmax pppd[3072]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.11.207>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [CCP ConfReq id=0x1 <deflate 15> <predictor 1>]
Jan 20 14:50:23 naycmax pppd[3072]: sent [CCP ConfReq id=0x1]
Jan 20 14:50:23 naycmax pppd[3072]: sent [CCP ConfRej id=0x1 <deflate 15>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [IPCP ConfReq id=0x1 <addr 192.168.11.11> <compress VJ 0f 01>]
Jan 20 14:50:23 naycmax pppd[3072]: sent [IPCP ConfAck id=0x1 <addr 192.168.11.11> <compress VJ 0f 01>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [IPCP ConfNak id=0x1 <addr 10.11.27.61>]
Jan 20 14:50:23 naycmax pppd[3072]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 10.11.27.61>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [CCP ConfAck id=0x1]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [CCP ConfReq id=0x2 <predictor 1>]
Jan 20 14:50:23 naycmax pppd[3072]: sent [CCP ConfRej id=0x2 <predictor 1>]
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 10.11.27.61>]
Jan 20 14:50:23 naycmax pppd[3072]: Script /etc/ppp/ip-up started (pid 3081)
Jan 20 14:50:23 naycmax pppd[3072]: rcvd [CCP ConfReq id=0x3]
Jan 20 14:50:24 naycmax pppd[3072]: sent [CCP ConfAck id=0x3]
Jan 20 14:50:24 naycmax pppd[3072]: Script /etc/ppp/ip-up finished (pid 3081), status = 0x0

tunnel established alright.
my routing table:

route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.11   *               255.255.255.255 UH    0      0        0 eth0
192.168.11.0     *               255.255.255.0   U     0      0        0 eth0
loopback        *               255.0.0.0       U     0      0        0 lo
default         *               0.0.0.0         U     0      0        0 ppp0


i can ping vpn server 192.168.11.11:

ping -c 4 192.168.11.11

PING 192.168.11.11 (192.168.11.11) 56(84) bytes of data.
64 bytes from 192.168.11.11: icmp_seq=1 ttl=64 time=0.105 ms
64 bytes from 192.168.11.11: icmp_seq=2 ttl=64 time=0.090 ms
64 bytes from 192.168.11.11: icmp_seq=3 ttl=64 time=0.077 ms
64 bytes from 192.168.11.11: icmp_seq=4 ttl=64 time=0.082 ms

--- 192.168.11.11 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.077/0.088/0.105/0.014 ms

and my ifconfig output:

ifconfig 


eth0      Link encap:Ethernet  HWaddr 00:11:95:fe:54:7b  
          inet addr:192.168.11.207  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fefe:547b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146406 (142.9 KiB)  TX bytes:3707 (3.6 KiB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.11.27.61  P-t-P:192.168.11.11  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1490  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:66 (66.0 B)  TX bytes:574 (574.0 B)

a couple of months back i got it working by adding ip-up script:

#!/bin/sh
ip route  del 192.168.11.11 dev ppp0 src 192.168.11.207
ip route add 192.168.11.11 via 192.168.11.11 src 192.168.11.207
ip route replace default dev ppp0


...but now i'm stuck...

just a guess from my side: it probably has something to do with routing but...once again i'm not an expert...

ps. have no problems getting online in WinXP.

---

