---
title: "Cant ping through gre tunnel"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by ermali82 on 2011-04-09
Hi i'm having  a strange issue with a ubuntu box.
 
2 ubuntu server boxes connect through a VPN connection (OpenSwan).
The connection is working fine and can ping from each box.
 
Over the VPN created a gre tunnel. The tunnel works normally and can ping each side of the gre tunnel.
 
Now the Proble.
From server 1 through the gre interface can ping Box 2 gre interface and vpn interface.
 
server11:~# ping -I gre1 10.10.10.1
PING 10.10.10.1 (10.10.10.1) from 10.0.0.2 gre1: 56(84) bytes of data.
64 bytes from 10.10.10.1: icmp_seq=1 ttl=64 time=1.05 ms
64 bytes from 10.10.10.1: icmp_seq=2 ttl=64 time=1.13 ms
64 bytes from 10.10.10.1: icmp_seq=3 ttl=64 time=1.62 ms
64 bytes from 10.10.10.1: icmp_seq=4 ttl=64 time=1.96 ms
 
10.10.10.1 is the vpn interface on box 2
 
From server 2 through the gre interface can ping Box 1 gre interface but not the vpn interface.
 
 
If i make a tcdump of the traffic on server 1 i see the traffic from server 2 coming through the gre tunnel and going back normally.
On server 2 i see the traffic going to server 1 and and commin back on the vpn interface then on the gre interface.
 
box2:~# tcpdump -i any  host 10.10.9.240
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
19:19:59.185799 IP 10.0.0.1 > 10.10.9.240: ICMP echo request, id 18519, seq 64, length 64
19:19:59.187022 IP 10.10.9.240 > 10.10.10.1: GREv0, length 88: IP  10.10.9.240 > 10.0.0.1: ICMP echo reply, id 18519, seq 64, length 64
19:19:59.187022 IP 10.10.9.240 > 10.0.0.1: ICMP echo reply, id 18519, seq 64, length 64
19:19:59.485789 IP 10.0.0.1 > 10.10.9.240: ICMP echo request, id 29199, seq 22218, length 64
19:19:59.486689 IP 10.10.9.240 > 10.10.10.1: GREv0, length 88: IP  10.10.9.240 > 10.0.0.1: ICMP echo reply, id 29199, seq 22218, length  64
19:19:59.486689 IP 10.10.9.240 > 10.0.0.1: ICMP echo reply, id 29199, seq 22218, length 64
19:20:00.185801 IP 10.0.0.1 > 10.10.9.240: ICMP echo request, id 18519, seq 65, length 64
19:20:00.186677 IP 10.10.9.240 > 10.10.10.1: GREv0, length 88: IP  10.10.9.240 > 10.0.0.1: ICMP echo reply, id 18519, seq 65, length 64
19:20:00.186677 IP 10.10.9.240 > 10.0.0.1: ICMP echo reply, id 18519, seq 65, length 64
19:20:00.485787 IP 10.0.0.1 > 10.10.9.240: ICMP echo request, id 29199, seq 22219, length 64
19:20:00.488032 IP 10.10.9.240 > 10.10.10.1: GREv0, length 88: IP  10.10.9.240 > 10.0.0.1: ICMP echo reply, id 29199, seq 22219, length  64
19:20:00.488032 IP 10.10.9.240 > 10.0.0.1: ICMP echo reply, id 29199, seq 22219, length 64
^C
12 packets captured
12 packets received by filter
0 packets dropped by kernel
 
 
10.10.9.240 is the vpn interface on server 1
10.10.10.1 is the vpn interface on server 2
10.0.0.1 is the gre interface on server 2
 
so the traffic is coming  back to the gre interface but not to the ping program, it gets blocked somehere.
 
iptables rules on server 2 are configured to permit anything 
 
On server 1 everything is workin as it should but not on server 2.

---

