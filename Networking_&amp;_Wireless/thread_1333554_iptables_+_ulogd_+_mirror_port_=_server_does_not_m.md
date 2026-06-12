---
title: "iptables + ulogd + mirror port = server does not match packets"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by Salivan on 2009-11-21
I configured mirroring at border router from uplink interface to interface which is connected to server.
I would like to match at server all packets which go through uplink interface.

I tried
"-A PREROUTING -p tcp -m tcp --tcp-flags SYN SYN -j ULOG --ulog-nlgroup 3 "
at raw, mangle and nat.

Server match only packets with dest. MAC address of this server.

What I made wrong?

---

### Post by yapakmoi on 2013-01-02
That's exactly what I am trying to do. I've been unable to find a solution. If someone can have a solution 3 years later.

---

