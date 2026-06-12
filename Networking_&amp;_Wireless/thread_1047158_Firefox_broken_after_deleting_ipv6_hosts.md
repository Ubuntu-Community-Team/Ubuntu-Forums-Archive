---
title: "Firefox broken after deleting ipv6 hosts"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by ngms27 on 2009-01-22
Using the manual network configuration I deleted the host entries for all the ipv6 entities.

Now Firefox just fails to connect to any host.

I can nslookup, tracert and ping using ipv4 addresses.

VMWare server also fails to work as the web page displays a 503 error.

I've readded the ipv6 host entries (I think they are right though I'm not sure) but this still hasn't fixed the issue.

How can I progress this? Reinstall networking etc?

---

### Post by halovivek on 2009-01-22
could you post some more details below. Type in terminal and post.
code
1. sudo lshw -C network
2. ethtool eth0
3. ping -c 4 [www.google.com](www.google.com)
ping -c 4 74.125.43.104
4. cat /etc/resolv.conf
5. cat /etc/network/interfaces
6. route -n

---

