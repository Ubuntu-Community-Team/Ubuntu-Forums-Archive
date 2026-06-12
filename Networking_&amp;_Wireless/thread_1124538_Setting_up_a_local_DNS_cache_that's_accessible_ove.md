---
title: "Setting up a local DNS cache that's accessible over the LAN"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by argie on 2009-04-13
I have pdnsd installed and running fine. However, the only way I can access it is from the machine on which pdnsd is installed. Simply put, I have a computer (192.168.1.38) but can only get answers on localhost from that machine. As in the following:

```

 dig google.com @192.168.1.38

; <<>> DiG 9.4.2-P2 <<>> google.com @192.168.1.38
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

```

dig google.com @127.0.0.1

; <<>> DiG 9.4.2-P2 <<>> google.com @127.0.0.1
;; global options:  printcmd
;; Got answer:
<snip>
;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr 13 22:59:55 2009
;; MSG SIZE  rcvd: 212

```

What settings do I change so that I can access pdnsd from another computer on the LAN?

I have tried setting the server_ip (and interface) to the following settings and restarting pdnsd with `/etc/init.d/pdnsd restart`:

* "192.168.1.38"
* wlan0
* any

EDIT: Never mind, I just used BIND anyway. It functions as well (since I keep this computer perpetually up) and I don't have these problems with it.

---

