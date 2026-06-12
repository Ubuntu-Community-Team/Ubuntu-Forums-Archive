---
title: "Empathy People Nearby Ports"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by lessmemorelove on 2010-03-25
Hi.

Trying to use empathy with the people nearby to talk to each other in the house. When the firewalls are off, this works. When the firewalls are on, this does not. I want my firewalls on. I found a message board with fedora people that said people nearby uses 5353 and 5289 but adding those does not seem to help. I am using gufw and know how to add things to make it work as I host online games from my pc on weekends. Any ideas on the ports I need?

---

### Post by lessmemorelove on 2010-03-25
n/m somebody messed up. it is udp 5353 and tcp 5298.

---

### Post by ceefour on 2010-05-12
> **lessmemorelove said:**
> n/m somebody messed up. it is udp 5353 and tcp 5298.
Yes indeed.

See [http://saravananthirumuruganathan.wordpress.com/2010/04/04/empathy-chat-messenger-tutorial/](http://saravananthirumuruganathan.wordpress.com/2010/04/04/empathy-chat-messenger-tutorial/)

I have another problem though. Chat works. But "Send file" using People Nearby doesn't work with firewall on, even if udp5353+tcp5298 has been whitelisted.

---

