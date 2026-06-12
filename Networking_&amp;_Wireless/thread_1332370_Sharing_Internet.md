---
title: "Sharing Internet"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by rifazmohamme on 2009-11-20
Hi

i have a laptop and a desktop both with ubuntu 9.10

n i have connected my laptop to the internet via Wi-Fi

i would like to share that internet to the desktop via ethernet.somebody pls help me on tat

---

### Post by dandnsmith on 2009-11-20
I'd allocate IP addresses in a restricted range to the ethernet (say 192.168.0.1 and 192.168.0.2), connect the 2 with a twisted UTP cable (not the standard straight patch cable), and set the routing table to forward stuff from the desktop to the laptop, and the stuff for the desktop to the laptop.
What I'm not clear about is how you need to set up the NAT stuff.

---

### Post by Iowan on 2009-11-20
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a connection sharing help page - but you may need to tweak settings a little to work via wireless.

---

