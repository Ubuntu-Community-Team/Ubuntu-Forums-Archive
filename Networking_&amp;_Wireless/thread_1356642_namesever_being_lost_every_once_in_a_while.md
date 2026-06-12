---
title: "namesever being lost every once in a while"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by yiorgos on 2009-12-16
I am facing a weird problem in Ubuntu 9.04 with KDE installed.
Every now and then the nameserver settings are lost,
namely the contents of the /etc/network/resolv.conf file are deleted.

I haven't found any other report to such a problem.
Any ideas why this may happen?

Thanks in advance

---

### Post by yiorgos on 2009-12-22
Please note, that any information would be helpful,
since the problem is persistent.

---

### Post by Iowan on 2009-12-22
Ordinarily, Network Manager (at least on Ubuntu) updates that file from information received from DHCP server.The question becomes which of the three is dropping the ball: DHCP server. Network Manager, or **resolvconf**.

---

### Post by yiorgos on 2009-12-23
Is there any way to monitor this?
To figure out which of the three is causing the problem?

---

