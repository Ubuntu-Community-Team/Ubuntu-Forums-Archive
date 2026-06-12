---
title: "NetBios over TCP: Supported Out Of The Box?"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by PeteCress on 2008-12-24
(I tried this in the eee forum, but no nibbles)'

Got PC-To-PC communication problems on my home LAN.

Four boxes total: 2 Windows XP and 2 Ubuntu.

Everybody can ping everybody else using IP addrs.

The two Windows XP boxes can ping each other AND the two Linux boxes by name.

But the two Linux boxes cannot ping anybody by name - only IP addr.

Greater minds than mine think it's a NetBT issue - as in the two Linux boxes not knowing from NetBT.

So, bottom line, should an un-tweaked Linux install (MythBuntu 8.04 on one, eee Ubuntu on the other) be able to speak NetBT?

If not, can I do something to remedy the situation?

---

### Post by albandy on 2008-12-24
Modifying the samba configuration you can do it, read this manual:
[http://oreilly.com/catalog/samba/chapter/book/ch07_03.html](http://oreilly.com/catalog/samba/chapter/book/ch07_03.html)

But if you don't want modify your samba configuration (could be a bit difficult if you don't know how samba works) you can modify the /etc/hosts file and add the windows ip address followed by the machine name.

for example, adding this entry to /etc/hosts:
192.168.1.2 machinename

will resolve machinename as 192.168.1.2

---

### Post by iponeverything on 2008-12-24
See this thread, it may be what you are looking for.

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

