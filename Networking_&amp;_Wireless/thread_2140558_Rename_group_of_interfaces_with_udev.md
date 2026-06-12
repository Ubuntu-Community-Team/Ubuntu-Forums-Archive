---
title: "Rename group of interfaces with udev"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by sakishrist on 2013-04-30
Hello!

I was wandering how I could achieve the following with udev or with the help of some other tool:


[LIST]
[*]Match an interface (used for wan) and rename it to WAN (DONE)
[*]Match All the rest of the interfaces and rename them as LAN1, LAN2 ... LANn.
[/LIST]

The thing is that I want to be able to add an Ethernet card in the future and not have to worry about it's name.

Thanks in advance

---

### Post by praseodym on 2013-04-30
The names of the interfaces (check "ifconfig -a") are set in the file /etc/udev/rules.d/70-persistent-net.rules.

---

### Post by sakishrist on 2013-04-30
I am aware of the location I have to set the rules, the problem is I want to mach multiple interfaces excluding one and rename all of them (bullet two of my original post).

---

