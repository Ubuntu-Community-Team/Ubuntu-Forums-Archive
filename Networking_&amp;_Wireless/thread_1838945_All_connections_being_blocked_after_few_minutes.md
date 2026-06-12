---
title: "All connections being blocked after few minutes"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by u_lone on 2011-09-04
Strange problem here...

After starting Ubuntu, I can normally access it from any other computer on the LAN (either using VNC or FTP). But after few minutes, Ubuntu just rejects all connections. If any connection is open, it just closes it.

I still have Internet on Ubuntu and I can ping other machines from Ubuntu. But any attempt to connect to Ubuntu from any machine, it fails.

If I restart, it works again. But after few minutes, Ubuntu starts to block connections.

I've already tried *iptables -F* and the problem still there. I've removed iptables, ufw and firestarter, with no luck. I've also tried some things mentioned on [this thread]("http://ubuntuforums.org/showthread.php?t=939824"), but nothing changed.

Any ideas?

---

### Post by u_lone on 2011-09-05
The problem seems to be solved.

All I had to do was to disable wireless on Ubuntu and connect using a wired connection.

After that, Ubuntu started to reply pings and accept connections on VNC and FTP, without blocking the connections after few minutes.

---

