---
title: "dns/routing/smthg_else issue"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by krossovok on 2010-09-09
Hi, All

I am trying to set up a powerdns resolver. Network settings for my server are:
eth0 - 1.1.1.1/27 - for management
eth1 - 1.1.1.33/27 - for incoming queries
eth2 - 1.1.1.65/27 - for outgoing queries
lo:1 - 2.2.2.2/32 - only this interface is listened by pdns-resolover

default gateway - 1.1.1.94

also quagga running, which advertising lo:1 via eth1

$ cat /proc/sys/net/ipv4/ip_forward
1

I can access 2.2.2.2:53 from network 1.1.1.0/24. But I can't access this address and port from any other networks. Even from networks connected to the same router, which is gateway for resolver.

I run tcpdump on eth1 and it shows that packets from remote machine are reaches eth1, but there is no outgoing queries via eth2, nor answers on remote machine.

on resolver:
$ sudo tcpdump -vvi eth1 'dst port 53'
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
21:39:10.706208 IP (tos 0x0, ttl 63, id 62015, offset 0, flags [none], proto UDP (17), length 54)
    remote.machine.37492 > resolver.test.domain: [udp sum ok] 34038+ A? example.com. (26)

on remote machine:
$ dig @2.2.2.2 example.com

; <<>> DiG 9.7.0-P1 <<>> @2.2.2.2 example.com
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

  
I can't understand what's wrong, can somebody help me?

---

