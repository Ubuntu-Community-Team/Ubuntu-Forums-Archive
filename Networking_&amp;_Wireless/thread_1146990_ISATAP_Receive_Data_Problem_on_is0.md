---
title: "ISATAP Receive Data Problem on is0"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by laizacruz on 2009-05-03
Hello
 
I'm trying to configure ISATAP client on ubutu 9.04 server, but not successful.
 
I monitor traffic with tcpdmp on the PC, and find certain packet ubutu receives, but the application does not receive data. I find the RX error counter increase.
 
What I did is:
 
root@wpc2:~# more isatap
#!/bin/bash
ip tunnel add is0 mode isatap local 192.168.2.61 ttl 64 dev eth1
ip link set is0 up
ip -f inet6 addr add 2002:0a01:170c:1:0:5efe:c0a8:023d dev is0
ip -f inet6 route add default via fe80::5efe:0a01:0c0c dev is0 metric 1
 
 
(I read an article that says v4any is outdated for ISATAP implementation, nor supported in ip command, so I believe this configuration should work.
I used 2002:: prefix because I'm trying 6to4/ISATAP gateway on cisco gear, but prefix selection itself should not be a problem.)
 
 
ping6 does not show any response, while tcpdump says it recevie packets.
 
 
root@wpc2:~# ping6 2002:a01:170d:1:280:6dff:fe51:49ac -c 3 -i 5
PING 2002:a01:170d:1:280:6dff:fe51:49ac(2002:a01:170d:1:280:6dff:fe51:49ac) 56 d
ata bytes
--- 2002:a01:170d:1:280:6dff:fe51:49ac ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 10004ms
 
 
root@wpc2:~# tcpdump -i eth1 -n -vvv
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
03:12:26.442486 arp who-has 192.168.2.11 tell 192.168.2.61
03:12:26.601889 arp reply 192.168.2.11 is-at ca:00:08:fc:00:00
03:12:26.601959 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto IPv6 (41)
, length 124) 192.168.2.61 > 10.1.12.12: IP6 (hlim 64, next-header ICMPv6 (58) p
ayload length: 64) 2002:a01:170c:1:0:5efe:c0a8:23d > 2002:a01:170d:1:280:6dff:fe
51:49ac: ICMP6, echo request, length 64, seq 1
03:12:28.385347 IP (tos 0x0, ttl 254, id 637, offset 0, flags [none], proto IPv6
(41), length 124) 10.1.12.12 > 192.168.2.61: IP6 (hlim 62, next-header ICMPv6 (
58) payload length: 64) 2002:a01:170d:1:280:6dff:fe51:49ac > 2002:a01:170c:1:0:5
efe:c0a8:23d: ICMP6, echo reply, length 64, seq 1
 
 
and RX error counter increase in proportion to recevied packets.
 
root@wpc2:~# ifconfig is0
is0 Link encap:IPv6-in-IPv4
inet6 addr: 2002:a01:170c:1:0:5efe:c0a8:23d/128 Scope:Global
inet6 addr: fe80::5efe:c0a8:23d/64 Scope:Link
UP RUNNING NOARP MTU:1480 Metric:1
RX packets:0 errors:3 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:312 (312.0 B)
 
Can someone suggest me:
 
(1) How can I know what type of errors RX error counted ?
 
(2) Is there anything I'm missing ? 
 
(3) Is there any good reference of working configuration ?
 
Thanks,

---

