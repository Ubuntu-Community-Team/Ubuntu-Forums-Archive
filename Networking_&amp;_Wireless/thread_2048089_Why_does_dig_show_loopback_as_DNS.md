---
title: "Why does dig show loopback as DNS"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by jacobroecker on 2012-08-26
Can anyone tell me why my dig command shows my loopback address as my DNS?  I've recently put a local DNS on my other ubuntu machine and have pointed this computer to use it, but it doesn't seem to want to play ball.  I expected the server to read 192.168.1.2 not 127.0.0.1:

```
jacobroecker@MooseFlix:~$ dig mothballs.com

; <<>> DiG 9.8.1-P1 <<>> mothballs.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20111
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mothballs.com.			IN	A

;; ANSWER SECTION:
mothballs.com.		203	IN	A	208.87.33.151

;; Query time: 596 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Aug 26 16:28:08 2012
;; MSG SIZE  rcvd: 47

```

---

### Post by sanderj on 2012-08-26
That's a new feature in Ubuntu 12.04.

EDIT:

See [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/) for explanation and help.

---

