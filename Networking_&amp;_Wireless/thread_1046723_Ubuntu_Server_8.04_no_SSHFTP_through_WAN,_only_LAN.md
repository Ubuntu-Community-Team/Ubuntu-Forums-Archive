---
title: "Ubuntu Server 8.04 no SSH/FTP through WAN, only LAN."
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by nonexistentera on 2009-01-21
Hello.
I have a Ubuntu 8.04 Server installed on one of my systems.
I am able to successfully connect and login to the system through my local network, but fails when I try to connect using my domain, and WAN IP.

Any suggestions on how this could be fixed, is there something wrong with how my network is configured, or is it the SSH/FTP servers, or both.

Thanks in advance.

---

### Post by Kebabman on 2009-01-21
You need to forward the SSH and FTP (22 and 21) ports on the Internet connected router on your network to the internal PC running the servers.

[www.portforward.com](www.portforward.com) should tell you how to do this for your router.

---

### Post by nonexistentera on 2009-01-21
That makes sense.
I guess it just didn't seem like something that you had to forward.

Well this thread is done, It's solved

---

