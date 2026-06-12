---
title: "Ping not responding"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by absoord on 2012-05-12
Hi all! I'm having an issue with the ping command on a LAN with the following description:

Server (A, 192.168.0.100):
Gateway: 192.168.0.1 (router)

Client (B, 192.168.0.5):
Gateway: 192.168.0.100

That's the configuration I chose to route clients (B) through a proxy server (A). Any ping from A to any host outside the LAN is responded. The problem is the client (B): If I try to ping any host outside the LAN I get no response.

A iptables configuration: iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
No B iptables configuration.

I can ping 192.168.0.1 from B.

Why can't I ping any host outside the LAN from B?

Thanx so much!

EDITED: I forgot, the ping command RESOLVES the host, but doesn't get response.

ubuntu@ubuntu:~$ ping google.es
PING google.es (74.125.132.94) 56(84) bytes of data.
(no response)

---

### Post by The Cog on 2012-05-12
Your proxy is only proxying http on TCP port 80. But B is using A as its internet gateway, so any other protocol/port heading to the internet must simply be forwarded by A without interception. This requires that A must be configured to perform IP forwarding. 
[http://linuxpoison.blogspot.co.uk/2008/01/how-to-enable-ip-forwarding.html](http://linuxpoison.blogspot.co.uk/2008/01/how-to-enable-ip-forwarding.html)

---

### Post by absoord on 2012-05-12
Clear and simple :-) Thanx so much!

---

