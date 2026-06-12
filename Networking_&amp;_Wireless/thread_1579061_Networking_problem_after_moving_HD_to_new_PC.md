---
title: "Networking problem after moving HD to new PC"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by papamike3108 on 2010-09-21
Hi, I'm having a problem regarding my nic. I have ubuntu server installed on a pc. The motherboard died, so I switched the HD to another computer. Everything is fine except the network. I cannot access this computer from other computer (while it was possible before). I looked at the interfaces and everything seems fine. The nic itselft seems to work too. Any ideas?

---

### Post by Iowan on 2010-09-21
You might need to edit [I]/etc/udev/rules.d/70-persistent-net.rules
[/I] Frequently, the old "eth0" definition gets left, and a new definition gets built.

---

