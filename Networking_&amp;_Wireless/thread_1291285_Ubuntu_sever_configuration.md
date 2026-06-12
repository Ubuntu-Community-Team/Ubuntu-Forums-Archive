---
title: "Ubuntu sever configuration"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by ikey_d on 2009-10-14
I've been looking through the forums trying to find some information but I can't find it yet; This is what I have:

DELL Poweredge Server
Configured as Application & File Server
with Red Hat
2 NICs

DELL Dimension Desktop
Configured as Gateway/Proxy
with Ubuntu Server
2 NICs

Nortel Router

My gateway connects to my router with gives internet access as well as internal access to all connected terminals.

My question is the following: how do I physically connect my Application Server to the setup so that it has INTERNAL access but not internet access. I want my internal terminals to be able to connect to it but I don't want any external access to it. I also would like to periodically be able to give it internet access to do software updates.

Any ideas are welcome, thanks.

---

### Post by Iowan on 2009-10-14
There's a similar thread around here somewhere... As far as I know, unless you have ports forwarded from the router to the server, it (the server) *should* be inaccessible from internet.

---

