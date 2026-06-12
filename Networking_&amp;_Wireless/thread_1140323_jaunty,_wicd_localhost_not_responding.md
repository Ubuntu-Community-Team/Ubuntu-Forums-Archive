---
title: "jaunty, wicd localhost not responding"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by kristian_nissen on 2009-04-27
During the weekend I upgraded to jaunty, afterwards I got sick and tired of knetworkmanager never working properly so I just switched to wicd instead which is working fine.

But now I'm unable to connect to my localhost! I have apache running and tested mongrel_rails as well but none of them would answer, I tested this using firefox and konqueror but none of them answered.

when I dig [http://localhost](http://localhost), I get this:

dig [http://localhost](http://localhost)

; <<>> DiG 9.5.1-P2 <<>> [http://localhost](http://localhost)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 33978
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;[http://localhost](http://localhost).              IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     A.ROOT-SERVERS.NET. NSTLD.VERISIGN-GRS.COM. 2009042701 1800 900 604800 86400
...

any help appreciated.

---

### Post by drpyro on 2009-10-10
I have the same problem, anyone have an idea ?
i switched recently to WICD and network-manager was removed automatically after that i was anable to connect to my apache2 localhost ...
when i switched back to network-manager everything get to work normally
the issue is about  wicd !!!!

my /etc/network/interfaces:
auto lo
iface lo inet loopback
****

---

### Post by ShizzlePDX503 on 2009-10-17
I have the same problem however I am on ununtu jaunty and I had apache installed and then switched over to wicd here is my dig:

```
$ dig http://localhost

; <<>> DiG 9.5.1-P2 <<>> http://localhost
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 27559
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;http://localhost.        IN    A

;; Query time: 4391 msec
;; SERVER: 192.168.15.1#53(192.168.15.1)
;; WHEN: Sat Oct 17 05:36:12 2009
;; MSG SIZE  rcvd: 34
```

my /etc/network/interfaces:
auto lo
iface lo inet loopback

would doing ```
sudo aptitude reinstall apache2
``` fix this?

---

### Post by ahmedhelmy007 on 2009-12-16
I have the same problem.
where are linux gurus???

---

### Post by Iowan on 2009-12-16
What is in */etc/network/interfaces* and */etc/hosts*?

---

