---
title: "KTorrent Port Forwarding Problem."
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by zerofool2005 on 2009-02-01
I cant get KTorrent to work properly with the port forwarding. Im conected to the router over wifi (Local IP 192.168.1.4)

Netger WGR614 v6.

Port forwarding is set up in router. But it just wont  connect and using a online scanner shows it as blocked. Anybody got any ideas?

---

### Post by zerofool2005 on 2009-02-01
Found in another thread.
Something that seems to fix it

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

---

