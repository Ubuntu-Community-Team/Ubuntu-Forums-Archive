---
title: "Two general routing questions"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by Sve n on 2012-05-23
Hi,
all guides I read, concerning routing, told me, to use "-m conntrack --ctstate", to differentiate between new and established connections, and to always accept latter ones, without checking the interfaces and source-ips. Does that fasten the connection, or why should one use it? Is it unsafe, in any way?
```
iptables -A FORWARD -o eth0 -i eth1 -s 192.168.3.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
#instead of only
iptables -A FORWARD -o eth0 -i eth1 -s 192.168.3.0/24 -j ACCEPT
```On a side note, what's the difference between ESTABLISHED and RELATED? The man-entry didn't help me much...

The second question concerns masquerading - why do I need it, or not? How does it work together with autofs, for example. Doesn't it give a mess, if several machines automount a nfs-directory from a different network, masqueraded from the same server, thus with the same ip, and one of them unmounts the directory?

Edit: A friend of mine could answer my questions, I think (the connection-tracking version lets packages from the outside through, if they're related to connections opened from the inside).

---

