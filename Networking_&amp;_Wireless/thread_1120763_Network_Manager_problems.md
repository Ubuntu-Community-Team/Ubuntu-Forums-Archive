---
title: "Network Manager problems"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by mechrekt on 2009-04-09
Hi everybody,
I'm new to the forum and new to linux :oops:
I finally installed Ubuntu 8.10; I can connect to wired network correctly, but I have this problem:
on the icon relating to networks, "Auto eth0" is automatically set: if I manually set an IP address by creating a new connection (called "Wired connection 1") everything works fine, but when I restart my PC the system automatically selects the "Auto eth0 " (instead of mine that I previously created).
I tried to delete the item "Auto eth0" or edit again the connection that I created before by selecting "connect automatically" and "system settings", but nothing changes.

Help me please! ](*,)

---

### Post by superprash2003 on 2009-04-09
try entering your static ip info in /etc/network/interfaces

for reference : [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

