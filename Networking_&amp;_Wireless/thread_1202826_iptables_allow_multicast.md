---
title: "iptables allow multicast"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by doobie on 2009-07-02
I have ubuntu server 9.04 running netatalk for AFP and using avahi.  I have iptables configured so that I can connect to the AFP server, but it is not "advertising" itself using avahi due to iptables config.  I had this working, but flushed the iptables and rebuilt them.  So, does anyone know what the iptable commands are to get the avahi port 5353 broadcasting itself on the local network (i.e., 192.168.1.0/24)?  I currently have:
```
iptables -A INPUT -p udp --dst 192.168.1.0/24 --dport 5353 -s 192.168.1.0/24 -j ACCEPT
iptables -A OUTPUT -p udp --dst 192.168.1.0/24 --sport 5353 -j ACCEPT
```
but this is not working.  Thanks in advance...

---

