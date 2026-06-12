---
title: "connection timeout problems on a Ubuntu desktop"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by boondocks on 2010-05-20
Something is wrong with the networking on this Ubuntu system.
It has been assigned the LAN ip address 10.1.10.10 

From another Ubuntu desktop, I can:
ssh myself@10.1.10.10   [COLOR="Blue"]( from 10.1.10.143 )[/COLOR] 
and I can login without any problems.

I can  ping  10.1.10.10 [COLOR="Blue"]( from 10.1.10.143 )[/COLOR]
> PING 10.1.10.10 (10.1.10.10) 56(84) bytes of data.
64 bytes from 10.1.10.10: icmp_seq=1 ttl=64 time=0.422 ms
64 bytes from 10.1.10.10: icmp_seq=2 ttl=64 time=0.387 ms
64 bytes from 10.1.10.10: icmp_seq=3 ttl=64 time=0.382 ms
64 bytes from 10.1.10.10: icmp_seq=4 ttl=64 time=0.367 ms
64 bytes from 10.1.10.10: icmp_seq=5 ttl=64 time=0.388 ms
64 bytes from 10.1.10.10: icmp_seq=6 ttl=64 time=0.359 ms
64 bytes from 10.1.10.10: icmp_seq=7 ttl=64 time=0.392 ms
64 bytes from 10.1.10.10: icmp_seq=8 ttl=64 time=0.381 ms
64 bytes from 10.1.10.10: icmp_seq=9 ttl=64 time=0.396 ms
64 bytes from 10.1.10.10: icmp_seq=10 ttl=64 time=0.386 ms
64 bytes from 10.1.10.10: icmp_seq=11 ttl=64 time=0.397 ms
64 bytes from 10.1.10.10: icmp_seq=12 ttl=64 time=0.386 ms
64 bytes from 10.1.10.10: icmp_seq=13 ttl=64 time=0.397 ms
64 bytes from 10.1.10.10: icmp_seq=14 ttl=64 time=0.387 ms
64 bytes from 10.1.10.10: icmp_seq=15 ttl=64 time=0.404 ms
64 bytes from 10.1.10.10: icmp_seq=16 ttl=64 time=0.372 ms
64 bytes from 10.1.10.10: icmp_seq=17 ttl=64 time=0.393 ms
64 bytes from 10.1.10.10: icmp_seq=18 ttl=64 time=0.382 ms
64 bytes from 10.1.10.10: icmp_seq=19 ttl=64 time=0.394 ms
64 bytes from 10.1.10.10: icmp_seq=20 ttl=64 time=0.383 ms
64 bytes from 10.1.10.10: icmp_seq=21 ttl=64 time=0.399 ms
64 bytes from 10.1.10.10: icmp_seq=22 ttl=64 time=0.383 ms
64 bytes from 10.1.10.10: icmp_seq=23 ttl=64 time=0.406 ms

--- 10.1.10.10 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 21992ms
rtt min/avg/max/mdev = 0.359/0.388/0.422/0.028 ms
But once I ssh into 10.1.10.10 then
> wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) 
--01:26:08--  [http://checkip.dyndns.org/](http://checkip.dyndns.org/)
           => `index.html'
Resolving checkip.dyndns.org... 208.78.70.70
Connecting to checkip.dyndns.org|208.78.70.70|:80... failed: Connection timed out.
Retrying.

--01:29:18--  [http://checkip.dyndns.org/](http://checkip.dyndns.org/)
  (try: 2) => `index.html'
Connecting to checkip.dyndns.org|208.78.70.70|:80... failed: Connection timed out.
Retrying.

and
> wget [http://www.google.com](http://www.google.com)
--01:40:34--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 74.125.19.104, 74.125.19.99, 74.125.19.103, ...
Connecting to [www.google.com|74.125.19.104|:80](www.google.com|74.125.19.104|:80)... failed: Connection timed out.
Connecting to [www.google.com|74.125.19.99|:80](www.google.com|74.125.19.99|:80)... failed: Connection timed out.
Connecting to [www.google.com|74.125.19.103|:80](www.google.com|74.125.19.103|:80)... failed: Connection timed out.
Connecting to [www.google.com|74.125.19.147|:80](www.google.com|74.125.19.147|:80)... failed: Connection timed out.
Retrying.

What is wrong? What can I do?

---

### Post by boondocks on 2010-05-20
So accessing a web server on the LAN works:
> wget [http://10.1.10.143/](http://10.1.10.143/)
--02:19:56--  [http://10.1.10.143/](http://10.1.10.143/)
           => `index.html'
Connecting to 10.1.10.143... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41 [text/html]

100%[============================================================================>] 41            --.--K/s             

02:19:56 (2.69 MB/s) - `index.html' saved [41/41]

---

