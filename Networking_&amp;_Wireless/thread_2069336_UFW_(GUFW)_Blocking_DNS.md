---
title: "UFW (GUFW) Blocking DNS"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2012-10-10
Just setup GUFW Rules: outgoing ALLOW , incoming ALLOW 22, 25/tcp, 80, 110, LIMIT ssh/tcp. This is a server. I'll probably change port for ssh and close 22 later. When firewall is on, I can ping (from LAN client) to the gateway, an adsl modem router 192.168.1.1 but "cannot find host google.com" when I ping that. With firewall off I can ping it. What am I missing?

---

### Post by pqwoerituytrueiwoq on 2012-10-10
port 53 is DNS UDP IIRC
for some reason enabling port 80 udp made it work for me

note i was using the linux box as a router and it was unable to assign the addresses

---

### Post by hawaiiman on 2012-10-20
It was pointed out to me that ufw is problematic at times in mysterious ways, and that I didn't really need a firewall as the server is behind an enterprise router with QOS. Apt-get remove ufw ..problems solved!

---

