---
title: "Ubuntu + DDNS"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by gmann1 on 2009-06-16
Hi,

I have router Asus 500gP, which can connect to two DDNS servers, but I need more.
I installed on my notebook with Ubuntu 8.10 - NOIP2 app., but it refresh only 2 from 5 host on [www.no-ip.org](www.no-ip.org) and also no periodically.
I don´t know why ?? :(

Somebody help me with thic client or any solution ? 

Thx

---

### Post by dmizer on 2009-06-16
Use [ddclient](http://ddclient.wiki.sourceforge.net/):
```
sudo aptitude install ddclient
```

---

### Post by gmann1 on 2009-06-16
i checked it, but ddclient isn´t only for DynDNS ?
It will be also right for NO-IP ddns ??

---

### Post by dmizer on 2009-06-16
> **gmann1 said:**
> i checked it, but ddclient isn´t only for DynDNS ?
It will be also right for NO-IP ddns ??

I use ddclient for all my dynamic hosts including noip.

---

### Post by gmann1 on 2009-06-16
OK, i go test it :).

Thx

---

