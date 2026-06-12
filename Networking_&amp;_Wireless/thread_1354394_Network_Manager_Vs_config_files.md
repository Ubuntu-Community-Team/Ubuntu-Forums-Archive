---
title: "Network Manager Vs config files"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by shade5 on 2009-12-13
Hi,
I want to know if you can configure your network by the files or if you need the network manager. I prefer the files to make scripts. But I also read that you should go for the developers tools because sometimes there are things you cannot set by config files or other values are set you do not know about.

I ran into some problems when using the files so I want to know if it is even possible. 

Greetings.

Edit: Now I did it with Network Manager and it worked. But when I check my /etc/network/interfaces only my loopback is displayed. I want to use files too. What do I have to do?

---

### Post by uncaspi on 2009-12-13
If you use anything else in /etc/network/interfaces than the loopback the network manager doesn't handle it.

---

### Post by Iowan on 2009-12-14
As Ubuntu and Network Manager evolve, NM seems to exert more control over the interfaces.  It *shouldn't* touch interfaces configured via */etc/network/interfaces*, though some threads mention DHCP overwriting static address configurations. A few other options - disable, remove, or replace Network Manager.

---

