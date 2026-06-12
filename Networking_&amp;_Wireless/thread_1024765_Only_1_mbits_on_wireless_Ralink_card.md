---
title: "Only 1 mbit/s on wireless Ralink card"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by TNE26 on 2008-12-29
Hi guys. I recently installed Ubuntu 7.10 on a server/desktop machine, and as it's a long way from my router, i plugged in a wireless PCI card. I think its a Ralink RT2500.

The problem is, that i usually only get 1 Mbit/s when downloading from it. When updating it goes higher, but effectively only 1 Mbit/s in Firefox, and a special network speed measurer run in Wine.

I read [this page]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660"), and i downloaded a driver but i cant install it, but I dont even know if thats the way to go.

I'm pretty much a newbie to Ubuntu, but I'm a fast learner. Please help me fix this, as i need to use this pc as part-time game server, and that needs a bit more than a 1 Mbit/s connection! ;)

---

### Post by michaelloft on 2009-07-13
I have the same problem on my debian system. A temporary fix is to open a terminal and type the command:

```
iwconfig wlan0 rate 54M
```

where wlan0 is my network card. You probably need sudo before the command on a ubuntu system.

---

