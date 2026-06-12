---
title: "Wireless: can detect but not connect"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by jjjrrr3 on 2010-06-05
I'm new to Ubuntu and have installed Xubuntu on an old laptop with a "RaLink RT2561/RT61 802.11g PCI" (according to lspci) wireless networking card.

The Network Manager applet detects wireless networks, but I cannot actually connect to any of them.  Ideas?  Suggestions?  I am a networking novice and don't know where to go from here. 

Thanks!

---

### Post by Talon2 on 2010-06-05
> **jjjrrr3 said:**
> I'm new to Ubuntu and have installed Xubuntu on an old laptop with a "RaLink RT2561/RT61 802.11g PCI" (according to lspci) wireless networking card.

The Network Manager applet detects wireless networks, but I cannot actually connect to any of them.  Ideas?  Suggestions?  I am a networking novice and don't know where to go from here. 

Thanks!

As far as I can tell, Ralink wifi support is really messed up in 10.04.

Here is a [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801") to a bug that may give you some ideas.

What we really need is for the kernel developers to take a look at what is going on.

---

