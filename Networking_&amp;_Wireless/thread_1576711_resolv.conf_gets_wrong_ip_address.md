---
title: "resolv.conf gets wrong ip address"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by fivebells on 2010-09-17
Whenever my 10.04 laptop wakes up and establishes a network connection, at the top of /etc/resolv.conf it puts the local IP address of my wireless router at home, 192.168.2.1.  This makes DNS lookups very slow if I'm not on my home network.  I can fix it each time by removing the inaccurate "nameserver 192.168.2.1" line, but that's becoming a bore.  Where should I look for the misconfiguration which is causing this?

---

### Post by fivebells on 2010-09-17
Just thought to search for the IP address under /etc.  Here are the results:```
met% sudo fgrep -r '192.168.2.1' /etc/
/etc/resolv.conf~:nameserver 192.168.2.1
/etc/resolvconf/run/resolv.conf:nameserver 192.168.2.1
/etc/resolvconf/run/resolv.conf~:nameserver 192.168.2.1
/etc/resolvconf/run/interface/eth0:nameserver 192.168.2.1
/etc/resolvconf/resolv.conf.d/original:nameserver 192.168.2.1
/etc/resolv.conf:nameserver 192.168.2.1
```Could resolvconf be the culprit?

---

### Post by fivebells on 2010-09-17
Never mind... It appears that all I needed was an apt-get upgrade...

---

