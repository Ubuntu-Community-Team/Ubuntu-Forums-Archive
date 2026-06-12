---
title: "No DNS from terminal (windows network)"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by Seine on 2009-08-26
Hi. My browser can resolve domain names, but I cannot do so from the terminal.

I have configured /etc/resolv.conf with the correct nameserver IPs (and verified these with a windows machine).

Here's what I get when using dig:

```
jem@D120108:~/Downloads$ dig google.com

; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57237
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; AUTHORITY SECTION:
com.			188	IN	SOA	ns.cdn.telstra.com.au. hostmaster.telstra.com.au. 2009030341 900 300 6220800 900

;; Query time: 18 msec
;; SERVER: 161.117.159.200#53(161.117.159.200)
;; WHEN: Thu Aug 27 10:33:10 2009
;; MSG SIZE  rcvd: 96
```

Note, there is no ANSWER section. There is also a flag that says answer=0.

Where to from here?

---

