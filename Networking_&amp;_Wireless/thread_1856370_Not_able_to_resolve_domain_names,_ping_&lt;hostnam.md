---
title: "Not able to resolve domain names, ping &lt;hostname1&gt; o/p: unknown host"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by tirthapratim1987 on 2011-10-08
i am using a usb modem for internet connection. The nameservers are also  fine in the /etc/resolv.conf. When i am logged in to superuser root,  domain resolving is working fine. But when logged in to other  administrator user, it's not able to resolve the domain name.

when i am logged in as user: tirtha (administrator user), here are some relevant o/p's:

tirtha@tirtha-lxp1:~$ dig router.test.local

; <<>> DiG 9.7.0-P1 <<>> router.test.local
;; global options: +cmd
;; connection timed out; no servers could be reached

tirtha@tirtha-lxp1:~$ sudo cat /etc/resolv.conf
nameserver 121.242.190.180
nameserver 4.2.2.3
nameserver 121.242.190.180
nameserver 4.2.2.3

tirtha@tirtha-lxp1:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:22:68:1f:60:e5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35675 (35.6 KB)  TX bytes:35675 (35.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:121.245.20.110  P-t-P:172.29.145.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9598994 (9.5 MB)  TX bytes:1309321 (1.3 MB)

wlan1     Link encap:Ethernet  HWaddr 00:22:fa:d4:e6:dc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


So clearly dig is saying the servers cann't be reached.

Whereas when logged in as root (superuser), i get these o/p's and the domain name resolving is happening perfectly fine.

root@tirtha-lxp1:~# dig router.local.test

; <<>> DiG 9.7.0-P1 <<>> router.local.test
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 17540
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;router.local.test.		IN	A

;; AUTHORITY SECTION:
.			10800	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2011100800 1800 900 604800 86400

;; Query time: 579 msec
;; SERVER: 121.242.190.180#53(121.242.190.180)
;; WHEN: Sat Oct  8 12:41:10 2011
;; MSG SIZE  rcvd: 110

root@tirtha-lxp1:~# cat /etc/resolv.conf
nameserver 121.242.190.180
nameserver 4.2.2.3
nameserver 121.242.190.180
nameserver 4.2.2.3


root@tirtha-lxp1:~# ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:22:68:1f:60:e5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35675 (35.6 KB)  TX bytes:35675 (35.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:121.245.20.110  P-t-P:172.29.145.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9641984 (9.6 MB)  TX bytes:1331000 (1.3 MB)

wlan1     Link encap:Ethernet  HWaddr 00:22:fa:d4:e6:dc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@tirtha-lxp1:~# ping google.com
PING google.com (74.125.71.106) 56(84) bytes of data.
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=1 ttl=53 time=239 ms
64 bytes from hx-in-f106.1e100.net (74.125.71.106): icmp_seq=2 ttl=53 time=246 ms


Please suggest!!!

---

