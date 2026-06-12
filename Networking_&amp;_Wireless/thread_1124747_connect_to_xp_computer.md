---
title: "connect to xp computer"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by izar on 2009-04-13
i set up a 'small network' on an xp running pc, and i am able to connect another xp laptop to it with a simple ethernet wire, and then browse the shared folders.
when i connect my laptop (running ubuntu 8.10) the same way, nothing happens (no light in the network card and no response from networkmanager applet)
looking in network>windows shares or using places> connect to server cant find the xp pc.
thanks for any help

---

### Post by dmizer on 2009-04-14
Do you mean that you have a direct cable connection from ethernet card to ethernet card (no router or hub inbetween)?

If so, are you using a [crossover cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)? If not, that could be at least part of your problem.

---

### Post by izar on 2009-04-15
thanks for your reply
the cable is not a crossover cable, and yet it works with windows XP so i thought it should work with ubuntu too. please correct me if there is something wrong with my logic.

---

### Post by dmizer on 2009-04-15
> **izar said:**
> thanks for your reply
the cable is not a crossover cable, and yet it works with windows XP so i thought it should work with ubuntu too. please correct me if there is something wrong with my logic.

Some network cards are able to automatically handle crossover. Most are not. There may be a setting that could force crossover, but I am unaware of it.

---

