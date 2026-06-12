---
title: "internet not working"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by shane8002 on 2009-03-22
Network manger showing a connection when connected through wireless, modem, and ethernet; but when I try to use mozilla, pidgin, synaptic, nothing works just says address not found.

---

### Post by Iowan on 2009-03-23
Post contents of **ifconfig -a**. If it's a 169.254.X.X address, **avahi** is trying to help (usually unsuccessfully).

---

### Post by shane8002 on 2009-03-23
got it fixed last night, looked at the system log and saw an entry about guarddog and ip tables. I installed guarddog the other day but uninstalled because i liked firestarter better. Dont know why guarddog would be running in the background like that after a uninstall.

---

### Post by Iowan on 2009-03-23
Glad you found it - firewall was gonna be my next suggestion :---)

---

