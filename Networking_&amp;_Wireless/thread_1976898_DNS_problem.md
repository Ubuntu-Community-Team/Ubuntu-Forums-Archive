---
title: "DNS problem"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by Sarmini on 2012-05-09
Hello,

I'm using Ubuntu 10.10, and recently IP address lookup stopped working. I can ping IP addresses but when I ping Google for example it says:

ping: unknown host google.com

although I can ping Google using the router's ping tool, so it seems like an error in communicating between Ubuntu and the router (D-link 2640U). I tried changing the DNS server both in the router configuration and in /etc/resolv.conf but it doesn't work either (although I can ping the DNS server).

I have Windows on the same machine and IP lookup works fine there. And what's more weird is that it sometimes works for a period of time without me changing anything.

Any help fixing this is appreciated,
Thanks!

---

### Post by bureau on 2012-05-09
need to change value for "nameserver" inside /etc/resolv.conf

---

### Post by Sarmini on 2012-05-09
I tried that (as mentioned in the post). Anyway, I deleted NetworkManager and it's solved.

---

