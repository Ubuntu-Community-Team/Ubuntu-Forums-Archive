---
title: "Mixed ethernet speeds"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Paqman on 2009-09-01
Quick and easy question: if I have a gigabit ethernet switch with a couple of PCs and a NAS (all gigabit) connected to each other, but the router located elsewhere is only fast ethernet, what speed will traffic between the PCs and NAS be? Presumably anything plugged into the router will only be 100Mbit/s, but will the devices sharing the switch benefit from greater speed?

---

### Post by denver on 2009-09-01
Of course!

All devices connected to the switch will be as fast as the switch and the installed Ethernet cards allow. That means that if the switch and the devices connected to it are all gigabit, they will have a gigabit connection between them.

If the router is only fast ethernet, then all communications OUTSIDE your local LAN, will only be as fast as the router.

Switches are layer 2 devices. Anything connected to layer 2 devices are on the same LAN segment (providing no VLANs are configured). As long as they are part of the same network, they should be able to comunicate with eachother without the use of a router. Imagine all the computers connected to a switch as people in the same room, and the door as the router connecting that room to another room.

Do a search for the OSI model to find out some information about basic networking concepts. Networking can be fun, if you have the necessary patience to learn the basics.

---

### Post by Paqman on 2009-09-01
Cheers, I figured that was the case, but was having trouble finding anywhere that spelled it out specifically.

> **denver said:**
> 
Do a search for the OSI model to find out some information about basic networking concepts. Networking can be fun, if you have the necessary patience to learn the basics.

Yeah, learning about networks properly is definitely on my short list of technical topics.

---

