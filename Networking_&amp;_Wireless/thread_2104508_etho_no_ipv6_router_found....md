---
title: "etho: no ipv6 router found..."
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by raviji on 2013-01-13
during booting of ubuntu 11.04 giving error..
   *etho: no ipv6 router found*

---

### Post by lemming465 on 2013-01-16
This is only a warning that no IPv6 ICMP router advertisement messages were received in response to your host sending a router solicitation to the IPv6 registered (with IANA) all-routers multicast address ff02::2.  If you are on an IPv4 only network, this is the expected behavior and not an error.

It's only an error if you are supposed to have native IPv6, because the only way IPv6 has of finding its upstream internet facing gateway is from the link-local (fe80::/64 prefix) sending address of the router advertisement.

---

