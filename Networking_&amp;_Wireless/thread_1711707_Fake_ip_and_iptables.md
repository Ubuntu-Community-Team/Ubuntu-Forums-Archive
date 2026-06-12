---
title: "Fake ip and iptables"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by morefeo on 2011-03-21
Hi all, I'm trying to run a wine program that connects on the internet.

Everything is fine until it tries to connect, it connect to myself (127.0.0.1), but as other similar applications I'm trying to use iptables to fix it, but as it's 127.0.0.1 and not a random fake ip, it's not working at all.

The port is right (9080), so I need something to redirect the data from 127.0.0.1:9080 to re.a.l.ip:9080 (I'm hiding the real ip obviously).

Reading the manual of iptables and searching around has not been for much success.

Sorry for my english, help is appreciated.

---

