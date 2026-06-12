---
title: "Does Ubuntu Server block ICMP by default?"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by TomOttaway on 2011-01-08
Installed Ubuntu Server 10.10, included Apache, PHP, and OpenSSH.  Apache is up and serving pages, I can connect using PuTTY no problem.  Server responds to a ping.  However, attempting to use ping or traceroute from the server results in a Destination Unreachable.  Happens even for other 192.168.1.10x boxes on the local network.  Any ideas why?

Thanks,

Tom

---

### Post by PatchesTheCaveman on 2011-01-09
Run these commands and copy/paste the output so we can see what might be going wrong:
```
cat /etc/interfaces
cat /etc/resolv.conf
ifconfig -a
ip route
```

---

