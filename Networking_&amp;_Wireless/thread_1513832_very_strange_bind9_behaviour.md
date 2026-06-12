---
title: "very strange bind9 behaviour"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by MacOkieh on 2010-06-20
I successfully installed and configured bind9 for my intranet (simply using "local" as my tld). Now when I "dig" to check if everything is ok only the first call to bind9 is working as expected. Here's what I get:

```
heiko@suh-ubuntu:/etc/bind$ dig local

; <<>> DiG 9.7.0-P1 <<>> local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15272
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;local.				IN	A

;; ANSWER SECTION:
local.			604800	IN	A	192.168.178.53

;; AUTHORITY SECTION:
local.			604800	IN	NS	ns1.local.

;; ADDITIONAL SECTION:
ns1.local.		604800	IN	A	192.168.178.53

;; Query time: 1 msec
;; SERVER: 192.168.178.53#53(192.168.178.53)
;; WHEN: Sun Jun 20 09:44:03 2010
;; MSG SIZE  rcvd: 73

```

But the second and all further calls are just getting this:

```
heiko@suh-ubuntu:/etc/bind$ dig local

; <<>> DiG 9.7.0-P1 <<>> local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 32758
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;local.				IN	A

;; AUTHORITY SECTION:
.			946	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2010061901 1800 900 604800 86400

;; Query time: 1 msec
;; SERVER: 192.168.178.1#53(192.168.178.1)
;; WHEN: Sun Jun 20 09:44:12 2010
;; MSG SIZE  rcvd: 98

```

In other words: no answer at all. Can someone explain to me what is happening here? Bind9 IS definetely working since the first call from a client in my intranet works fine. If necessary I will post my conf files...

TIA
Heiko

---

### Post by gombadi on 2010-06-20
> 
;; SERVER: 192.168.178.53#53(192.168.178.53)


and

> 
;; SERVER: 192.168.178.1#53(192.168.178.1)


You are asking two different servers. Are they configured with the same information?

---

### Post by MacOkieh on 2010-06-20
first ip (...178.53) is my name server where bind is running, second one (...178.1) my router; there is a forwarder {...} option in named.conf which points to this ip. So  first call to bind is absolute correct!

---

