---
title: "DNS not working properly (Maybe be BIND9 related)"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by domzz on 2010-04-25
So I am migrating my server from Kloxo (lxadmin) to Ubuntu (webmin/virtualmin), and I already had my Nameservers on my register (Godaddy) to go to ns1.thedomz.com and ns2.thedomz.com along with my IP. (I set the ttl to 60 cuz I thought that might be a problem)


Now, I do a dig thedomz.com, it gives me this output.
```
; <<>> DiG 9.6.1-P2 <<>> thedomz.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40276
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 2

;; QUESTION SECTION:
;thedomz.com.                   IN      A

;; ANSWER SECTION:
thedomz.com.            60      IN      A       87.98.249.202

;; AUTHORITY SECTION:
thedomz.com.            60      IN      NS      ns1.thedomz.com.
thedomz.com.            60      IN      NS      thedomz.com.
thedomz.com.            60      IN      NS      ns2.thedomz.com.

;; ADDITIONAL SECTION:
ns1.thedomz.com.        60      IN      A       87.98.249.202
ns2.thedomz.com.        60      IN      A       87.98.249.202

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Apr 25 16:32:46 2010
;; MSG SIZE  rcvd: 127
                             
```

when I do dig +trace thedomz.com
```
;; global options: +cmd
.                       512996  IN      NS      a.root-servers.net.
.                       512996  IN      NS      i.root-servers.net.
.                       512996  IN      NS      h.root-servers.net.
.                       512996  IN      NS      g.root-servers.net.
.                       512996  IN      NS      k.root-servers.net.
.                       512996  IN      NS      j.root-servers.net.
.                       512996  IN      NS      f.root-servers.net.
.                       512996  IN      NS      d.root-servers.net.
.                       512996  IN      NS      e.root-servers.net.
.                       512996  IN      NS      m.root-servers.net.
.                       512996  IN      NS      b.root-servers.net.
.                       512996  IN      NS      c.root-servers.net.
.                       512996  IN      NS      l.root-servers.net.
;; Received 456 bytes from 127.0.0.1#53(127.0.0.1) in 0 ms

com.                    172800  IN      NS      L.GTLD-SERVERS.NET.
com.                    172800  IN      NS      G.GTLD-SERVERS.NET.
com.                    172800  IN      NS      J.GTLD-SERVERS.NET.
com.                    172800  IN      NS      H.GTLD-SERVERS.NET.
com.                    172800  IN      NS      M.GTLD-SERVERS.NET.
com.                    172800  IN      NS      F.GTLD-SERVERS.NET.
com.                    172800  IN      NS      I.GTLD-SERVERS.NET.
com.                    172800  IN      NS      C.GTLD-SERVERS.NET.
com.                    172800  IN      NS      B.GTLD-SERVERS.NET.
com.                    172800  IN      NS      D.GTLD-SERVERS.NET.
com.                    172800  IN      NS      K.GTLD-SERVERS.NET.
com.                    172800  IN      NS      E.GTLD-SERVERS.NET.
com.                    172800  IN      NS      A.GTLD-SERVERS.NET.
;; Received 501 bytes from 192.58.128.30#53(j.root-servers.net) in 17 ms

thedomz.com.            172800  IN      NS      ns1.thedomz.com.
thedomz.com.            172800  IN      NS      ns2.thedomz.com.
;; Received 97 bytes from 192.31.80.30#53(D.GTLD-SERVERS.NET) in 96 ms

**;; connection timed out; no servers could be reached **   
```




Anyone know what the problem is?

I can go to my website only when I change my hosts file (on my windows machine).

---

### Post by domzz on 2010-04-25
Here is my bind9 zone file:

```
$ttl 60
thedomz.com.	IN	SOA	thedomz.com. domz.tvstarcraft.com. (
			1272160173
			10800
			3600
			604800
			38400 )
thedomz.com.	IN	NS	thedomz.com.
thedomz.com.	IN	A	87.98.249.202
www.thedomz.com.	IN	A	87.98.249.202
ftp.thedomz.com.	IN	A	87.98.249.202
mail.thedomz.com.	IN	A	87.98.249.202
ns1.thedomz.com.	IN	A	87.98.249.202
ns2.thedomz.com.	IN	A	87.98.249.202
thedomz.com.	IN	NS	ns1.thedomz.com.
thedomz.com.	IN	NS	ns2.thedomz.com.
thedomz.com.	IN	MX	10 mail.thedomz.com.

```

---

### Post by domzz on 2010-04-25
Also 

cat /etc/resolv.conf
```

nameserver 127.0.0.1
search thedomz.com
nameserver 94.23.156.122
nameserver 94.23.159.236
nameserver 94.23.203.208
nameserver 87.98.249.202  
```

---

