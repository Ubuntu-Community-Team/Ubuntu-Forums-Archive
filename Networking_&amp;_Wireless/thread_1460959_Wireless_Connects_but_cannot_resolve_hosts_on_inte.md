---
title: "Wireless Connects but cannot resolve hosts on internet"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by yeehi on 2010-04-23
The computer connects wirelessly to a router.
The router is connected to the internet and that is working well. (If i use a cable connection to the router, I can reach the internet).

Why won´t the wireless connection reach the Internet? It is a strong connection. It worked before wirelessly. I am on 10.04 beta, with the recent updates installed.

---

### Post by Iowan on 2010-04-23
If the computer has a valid IP address (**ifconfig -a)**, and can ping the router, check **route -n** to verify that the computer is using the router as it's gateway. If you can ping the internet by IP address (74.125.95.106), check DNS settings in */etc/resolv.conf*.

---

