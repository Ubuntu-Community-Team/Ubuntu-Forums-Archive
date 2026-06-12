---
title: "Terminal Server Client to Private IP"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by radagast89 on 2011-01-26
I'm currently successfully using the Terminal Server Client to connect to an SBS 2003 server at a remote location.  I've been trying to figure out if it's possible to connect to any of the XP machines on the LAN behind it.  I currently have to use RWW in IE on a VirtualBox XP machine to do that, and I'd love to be able to get rid of VirtualBox completely.

The server has 2 NICs, one connected to the internet, and the other connected to the LAN.  There is only one public IP.  The computer I'd most like to connect to has a static, private IP.  Anybody done anything like this or have any thoughts on how to get it to work?

---

### Post by radagast89 on 2011-01-26
Nevermind.  I figured it out.  If you're interested, what I had to do was open up port 3390 (or whatever) on the firewall that sits outside the server, then set up a rule on the server to map port 3390 to port 3389 on the private IP in question.

---

### Post by dmizer on 2011-01-26
> **radagast89 said:**
> Nevermind.  I figured it out.  If you're interested, what I had to do was open up port 3390 (or whatever) on the firewall that sits outside the server, then set up a rule on the server to map port 3390 to port 3389 on the private IP in question.

This is exceptionally insecure. The only thing keeping your SBS 2003 server from being hacked is a password (assuming you even have one in place). Moving the port really won't change the fact that you've just created a really sweet target for attackers.

Do not open anything to remote login unless it's connected by a secure (ie encrypted) tunnel of some kind.

---

