---
title: "Help diagnosing network problem in 8.10"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by Stormx on 2008-12-16
Hi. I see the old (and good) network manager has vanished, and frankly I have no idea how to diagnose my brother's network problem.

I guess it's lost the DNS server settings or something. Won't resolve domains, but it can ping IP address. launching nm-applet does nothing. NetworkManager does nothing. I'd really like to be able to do this via GUI.

I just can't see how to configure the network with the horrible new networking tools.

Help?

---

### Post by Stormx on 2008-12-16
Sorted it. Needed to add a line like:

nameserver 192.168.0.1

to my /etc/resolv.conf

---

