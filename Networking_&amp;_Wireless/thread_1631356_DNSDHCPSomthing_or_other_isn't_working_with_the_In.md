---
title: "DNS/DHCP/Somthing or other isn't working with the Internet (Comcast sucks?)"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by jkrez on 2010-11-26
I've been having an issue where I know a website is up, but can't connect to it. I go to the U of M so I use the site ctools.umich.edu often, but can't connect to it via my comcast connection often times and have to use my phone to teather and connect.

From my comcast connection I can do:

$ host ctools.umich.edu
ctools.umich.edu has address 141.211.48.10
ctools.umich.edu mail is handled by 50 ctools-mx.itd.umich.edu.
ctools.umich.edu mail is handled by 10 mx2-ctools.ds.itd.umich.edu.

or

$ nslookup ctools.umich.edu
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
Name:	ctools.umich.edu
Address: 141.211.48.10

or

$ dig ctools.umich.edu

; <<>> DiG 9.7.1-P2 <<>> ctools.umich.edu
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19707
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ctools.umich.edu.		IN	A

;; ANSWER SECTION:
ctools.umich.edu.	234	IN	A	141.211.48.10

;; Query time: 24 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Nov 26 13:10:19 2010
;; MSG SIZE  rcvd: 50


but when I try to browse to it or ping it I get no response. This happens on and off.  Some days it will work, some it wont. What's happening, and what can I do to fix this? (This is the same on all computers on this connection)

Thanks in advance for any help.

---

### Post by jkrez on 2010-11-26
Ohh btw:


$ traceroute ctools.umich.edu
traceroute to ctools.umich.edu (141.211.48.10), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

---

### Post by cajunaggie on 2010-12-05
I'm in a similar situation. I'm trying to connect to a particular forum, but I keep getting a connection time-out. I've communicated with other forum members by IM & e-mail and they can get through in about 8 seconds. I've tried clearing cookies & history and flushing the cache. I can't connect in Linux or in Windows with Firefox or IE. Any ideas at all?

---

