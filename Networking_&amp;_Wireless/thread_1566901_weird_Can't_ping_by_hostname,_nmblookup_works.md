---
title: "weird Can't ping by hostname, nmblookup works"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by Lookcrabs on 2010-09-03
I can't ping by netbios name or fully qualified domain name, BUT nmblookup works just fine. I know it's a dns problem(s) I just don't know what or how to fix it. I'm very new to all of this(networking, domain administration, posting on forums etc) so I hope this is the right way to ask for help here.

I've searched around the forums and the internet for a bit but I haven't found a solution to my problem yet.

here is some background on how the network is setup
[LIST]
[*]2 different domains sharing the same dhcp scope.
[*]DC for DomainA is running windows 2003 std
[*]DC for DomainB is running windows 2008 sbs
[*]DC-A has ip of 192.168.1.249
[*]DC-B has ip of 192.168.1.3
[*]router is sonicwall (192.168.1.1)
[*]DC-A is hosting both DHCP and DNS
[*]there are 25 computers in DomainB and 1 computer (not in domain) with ubuntu 10.04 and Free Open Ghost running on it (dhcp off)
[*]all 25 computers can ping the fog server by name (and eachother)
[*]all 25 computers pxeboot to fog just fine
[/LIST]

output of ifconfig -a
```

administrator@fogserver:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:7e:aa:de  
          inet addr:192.168.1.240  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe7e:aade/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11972169 (11.9 MB)  TX bytes:40404219 (40.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2013778 (2.0 MB)  TX bytes:2013778 (2.0 MB)


```

output of "ip route show"
```

administrator@fogserver:~$ ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.240  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 

```

output of ping to lab-04
```

administrator@fogserver:~$ ping lab-04
ping: unknown host lab-04
administrator@fogserver:~$ ping lab-04.local
ping: unknown host lab-04.local
administrator@fogserver:~$ ping lab-04.DomainB.local
ping: unknown host lab-04.DomainB.local

```

output of nmblookup (live host)
```

administrator@fogserver:~$ nmblookup lab-04
querying lab-04 on 192.168.1.255
**192.168.1.166 lab-04<00>**
administrator@fogserver:~$ nmblookup lab-04.local
querying lab-04.local on 192.168.1.255
name_query failed to find name lab-04.local
administrator@fogserver:~$ nmblookup lab-04.DomainB.local
querying lab-04.DomainB.local on 192.168.1.255
name_query failed to find name lab-04.DomainB.local

```

output of nmblookup (dead host)
```

administrator@fogserver:~$ nmblookup lab-01
querying lab-01 on 192.168.1.255
name_query failed to find name lab-01
administrator@fogserver:~$ 

```

output of dig to lab-04
```

administrator@fogserver:~$ dig lab-04

; <<>> DiG 9.7.0-P1 <<>> lab-04
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 18280
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;lab-04.				IN	A

;; Query time: 4 msec
;; SERVER: 192.168.1.249#53(192.168.1.249)
;; WHEN: Fri Sep  3 00:07:00 2010
;; MSG SIZE  rcvd: 24

administrator@fogserver:~$ dig lab-04.local

; <<>> DiG 9.7.0-P1 <<>> lab-04.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 2106
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;lab-04.local.			IN	A

;; AUTHORITY SECTION:
.			10065	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2010090101 1800 900 604800 729

;; Query time: 3 msec
;; SERVER: 192.168.1.249#53(192.168.1.249)
;; WHEN: Fri Sep  3 00:07:05 2010
;; MSG SIZE  rcvd: 105

administrator@fogserver:~$ dig lab-04.DomainB.local

; <<>> DiG 9.7.0-P1 <<>> lab-04.DomainB.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 5809
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;lab-04.DomainB.local.		IN	A

;; AUTHORITY SECTION:
.			10059	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2010090101 1800 900 604800 712

;; Query time: 4 msec
;; SERVER: 192.168.1.249#53(192.168.1.249)
;; WHEN: Fri Sep  3 00:07:11 2010
;; MSG SIZE  rcvd: 115

administrator@fogserver:~$ dig lab-04.DomainB

; <<>> DiG 9.7.0-P1 <<>> lab-04.DomainB
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 24216
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;lab-04.DomainB.		IN	A

;; AUTHORITY SECTION:
.			10800	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2010090201 1800 900 604800 86400

;; Query time: 61 msec
;; SERVER: 192.168.1.249#53(192.168.1.249)
;; WHEN: Fri Sep  3 00:07:15 2010
;; MSG SIZE  rcvd: 109

administrator@fogserver:~$ 

```

output of resolv.conf
```

administrator@fogserver:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
search DomainB.local
nameserver 192.168.1.249
nameserver 192.168.1.3
nameserver 192.168.1.1
administrator@fogserver:~$ 

```

output of nsswitch.conf
```

administrator@fogserver:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal dns [NOTFOUND=return] mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

output of hosts.conf
```

administrator@fogserver:~$ cat /etc/host.conf
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

```

sorry for the long post but i'm losing my mind. Any help is much appreciated.

---

### Post by scorp123 on 2010-09-03
Newer Windows releases block ping per default. Please check the Windows firewall settings.

---

