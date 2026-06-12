---
title: "Wireless problem in ubuntu 10.04"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by ypok on 2010-08-23
Hi all,

I have not been able to use wireless since I upgraded UBUNUTU to 10.04. I checked other related posts and tried everything but when I try to connect to wireless, it says "connection established" but I can't use the internet....
can anyone help me out?

Thanks in advance.
YP

---

### Post by Iowan on 2010-08-23
Does **ifconfig -a** show the interface with an IP address? It's possible routing (**route -n)** or DNS (**less /etc/resolv.conf**) or IPv6 might be responsible...

---

