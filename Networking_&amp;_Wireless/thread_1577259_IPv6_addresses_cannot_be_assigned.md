---
title: "IPv6 addresses cannot be assigned"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by ygoe on 2010-09-18
Hi,

I'm trying to assign like 80 IPv6 addresses on eth0 for virtual webhosting, but after 55 addresses I get the following error:

# ip addr add 2a01:9f8:a171:1651::4b:a8af dev eth0
RTNETLINK answers: File exists

What's the problem? I don't understand that error message at all. Is the number of IPv6 addresses per device somehow limited?

Ubuntu 10.4.1 server, 64 bit.

---

### Post by ygoe on 2010-09-18
Damnit, 'ip addr show' is broken. If I look at /proc/net/if_inet6, I see all my assigned IPv6 addresses. So they were really assigned but ip addr show just didn't admit it.

---

