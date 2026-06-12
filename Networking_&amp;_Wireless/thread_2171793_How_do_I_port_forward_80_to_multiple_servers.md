---
title: "How do I port forward 80 to multiple servers?"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by caleb12134 on 2013-09-01
Hey, I have multiple servers. I need to forward port 80 to multiple servers. I have the newest verizon fios router. Thanks!

---

### Post by sanderj on 2013-09-01
You say "forward port", so you're behind NAT, right?

If so, the answer is: you can't.

However, you can forward port 8001 to server1:80, port 8002 to server:2:80, etc.

How to do port forwarding on your NAT device, is NAT device dependent. See your manual, or [http://portforward.com/english/routers/port_forwarding/](http://portforward.com/english/routers/port_forwarding/)

---

### Post by SeijiSensei on 2013-09-01
If you forward the port to an Apache server, you can use its [proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") features to route traffic based on the ServerName.

---

