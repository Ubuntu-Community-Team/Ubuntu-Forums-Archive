---
title: "One hostname for lan and internet IP"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by m0116815 on 2009-10-15
Hi,

This seems like a simple matter but I can't find a solution.
I have a webserver running. It has an external and a local IP. When I want to ssh into it, I have to use the local IP if I'm on the LAN and the external one if I'm not. Is there an easy way to let linux decide whether I'm on the LAN or not and choose the appropriate IP automatically? I have given both IP addresses nicknames in the ~/.ssh/config file, but I can't give them the same one...

Any ideas?

---

### Post by Lars Noodén on 2009-10-20
You should be able to use the external IP address all the time.  Can you?

---

### Post by i.r.id10t on 2009-10-20
Do this on the DNS level - internal (on your LAN) dns points to the internal IP, external DNS (on the "out there") points to external IP.  All for same host/domain name.

---

