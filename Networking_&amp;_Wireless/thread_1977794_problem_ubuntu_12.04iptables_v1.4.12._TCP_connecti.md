---
title: "problem: ubuntu 12.04/iptables v1.4.12. TCP connections are cut by my Linux_routerNAT"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by mafeuser on 2012-05-10
Hallo newsgroup members.

my configuration is: <= internet => eth0 [Linux Router NAT] eth1 <=> network behind the NAT: 192.168.10.0/24

Experience of end user sitting behind the NAT is that his browser after sending the request, waits on and on and page is never loaded.

notebook_behind_the_NAT$ elinks [www.bmw.com](www.bmw.com) #just to remind: elinks is text browser.

Linux_router$ sudo tcpdump -nN port 80 -i eth1 #eth1 - interface from nat side.
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
08:56:23.281011 IP 192.168.10.130.57196 > 23.61.248.65.80: Flags [S], seq 2777447089, win 5840, options [mss 1460,sackOK,TS val 25390 ecr 0,nop,wscale 6], length 0
08:56:23.291543 IP 23.61.248.65.80 > 192.168.10.130.57196: Flags [S.], seq 3924108416, ack 2777447090, win 14480, options [mss 1460,sackOK,TS val 650310770 ecr 25390,nop,wscale 2], length 0
08:56:23.291656 IP 192.168.10.130.57196 > 23.61.248.65.80: Flags [.], ack 1, win 92, options [nop,nop,TS val 25393 ecr 650310770], length 0
08:56:23.291940 IP 192.168.10.130.57196 > 23.61.248.65.80: Flags [P.], seq 1:194, ack 1, win 92, options [nop,nop,TS val 25393 ecr 650310770], length 193
08:56:23.303989 IP 23.61.248.65.80 > 192.168.10.130.57196: Flags [.], ack 194, win 3888, options [nop,nop,TS val 650310782 ecr 25393], length 0

#Now I issued following "sudo cat /proc/net/ip_conntrack | grep 192.168" and closed browser.

08:56:30.602665 IP 192.168.10.130.57196 > 23.61.248.65.80: Flags [F.], seq 194, ack 1, win 92, options [nop,nop,TS val 27220 ecr 650310782], length 0
08:56:30.654202 IP 23.61.248.65.80 > 192.168.10.130.57196: Flags [.], ack 195, win 3888, options [nop,nop,TS val 650318129 ecr 27220], length 0
^C
7 packets captured
7 packets received by filter
0 packets dropped by kernel

#connection on port 80 is in ESTABLISHED state. udp/DNS messages work ok.
#there is also ssh connection between Linux router and laptop behind the NAT, which works correct.
Linux_router$ sudo cat /proc/net/ip_conntrack | grep 192.168
tcp      6 431994 ESTABLISHED src=192.168.10.1 dst=192.168.10.130 sport=33477 dport=22 src=192.168.10.130 dst=192.168.10.1 sport=22 dport=33477 [ASSURED] mark=0 use=2
tcp      6 431994 ESTABLISHED src=192.168.10.130 dst=23.61.248.43 sport=40200 dport=80 src=23.61.248.43 dst=89.77.223.114 sport=80 dport=40200 [ASSURED] mark=0 use=2
udp      17 24 src=192.168.10.130 dst=62.179.1.63 sport=35901 dport=53 src=62.179.1.63 dst=89.77.223.114 sport=53 dport=35901 mark=0 use=2
udp      17 24 src=192.168.10.130 dst=62.179.1.63 sport=44618 dport=53 src=62.179.1.63 dst=89.77.223.114 sport=53 dport=44618 mark=0 use=2

#dns and ping messages work ok.
notebook_behind_the_NAT$ ping [www.bmw.com](www.bmw.com)
PING a1550.b.akamai.net (23.61.248.65) 56(84) bytes of data.
64 bytes from a23-61-248-65.deploy.akamaitechnologies.com (23.61.248.65): icmp_seq=1 ttl=58 time=11.6 ms
64 bytes from a23-61-248-65.deploy.akamaitechnologies.com (23.61.248.65): icmp_seq=2 ttl=58 time=11.9 ms
64 bytes from a23-61-248-65.deploy.akamaitechnologies.com (23.61.248.65): icmp_seq=3 ttl=58 time=13.1 ms
64 bytes from a23-61-248-65.deploy.akamaitechnologies.com (23.61.248.65): icmp_seq=4 ttl=58 time=18.1 ms

#now sniffing on public(internet) interface. This time I let finishing the session on its own.

Linux_router$ sudo tcpdump -ttnN port 80 -i eth0 #. note: connection is finished after 120s.
1336636100.968299 IP 89.77.223.114.57208 > 23.61.248.65.80: Flags [S], seq 671530171, win 5840, options [mss 1460,sackOK,TS val 804704 ecr 0,nop,wscale 6], length 0
1336636100.977786 IP 23.61.248.65.80 > 89.77.223.114.57208: Flags [S.], seq 1270365566, ack 671530172, win 14480, options [mss 1460,sackOK,TS val 653428079 ecr 804704,nop,wscale 2], length 0
1336636100.977960 IP 89.77.223.114.57208 > 23.61.248.65.80: Flags [.], ack 1, win 92, options [nop,nop,TS val 804707 ecr 653428079], length 0
1336636100.978239 IP 89.77.223.114.57208 > 23.61.248.65.80: Flags [P.], seq 1:194, ack 1, win 92, options [nop,nop,TS val 804707 ecr 653428079], length 193
1336636100.989938 IP 23.61.248.65.80 > 89.77.223.114.57208: Flags [.], ack 194, win 3888, options [nop,nop,TS val 653428091 ecr 804707], length 0
1336636221.102344 IP 89.77.223.114.57208 > 23.61.248.65.80: Flags [F.], seq 194, ack 1, win 92, options [nop,nop,TS val 834737 ecr 653428091], length 0

What is worth mentioning, my hardware network setup works very well when Linux router works on ubuntu 11.04.

Let's continue.

#some iptbles facts
Linux_router$ sudo iptables -L -nv
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Linux_router$ sudo iptables -tnat -L -nv
Chain PREROUTING (policy ACCEPT 26 packets, 6168 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 18 packets, 5640 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 6 packets, 334 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   14   862 MASQUERADE  all  --  *      *       0.0.0.0/0            0.0.0.0/0   

Linux_router$ iptables #version.
iptables v1.4.12: no command specified
Try `iptables -h' or 'iptables --help' for more information.

#I also disabled ipv6 features (maybe not enough?).
Linux_router$ sudo sysctl -p
net.ipv4.ip_forward = 1
net.ipv6.conf.all.autoconf = 0
net.ipv6.conf.all.accept_ra = 0
net.ipv6.conf.all.disable_ipv6 = 1

#ipv6 address not present.
Linux_router$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:04:8a:13  
          inet addr:89.77.223.114  Bcast:255.255.255.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:8611 errors:12 dropped:0 overruns:0 frame:12
          TX packets:1003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:982765 (982.7 KB)  TX bytes:97913 (97.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:02:b3:8c:dc:e7  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21024 (21.0 KB)  TX bytes:15609 (15.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

Linux_router$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         89.77.220.1     0.0.0.0         UG    100    0        0 eth0
89.77.220.0     0.0.0.0         255.255.252.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
255.255.255.255 0.0.0.0         255.255.255.255 UH    0      0        0 eth1

I am stuck and I need Your help.

best regards.
Paul

---

