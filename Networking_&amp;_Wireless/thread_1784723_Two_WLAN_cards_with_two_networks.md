---
title: "Two WLAN cards with two networks"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by xz124 on 2011-06-17
Hey everyone,

I've searched and searched for an answer to this question to no avail. I have two WLAN cards installed in my desktop. I have a PCI Broadcom BCM4306 b/g card by Linksys (the original Linksys) and a USB Ralink WLAN n card by TRENDnet. Both of these cards work flawlessly, no problems in that sense. I also have two WLAN routers and networks at home. One of these networks is a Wireless N and another is a Wireless G. However, every time that I start up my computer, NetworkManager automatically assumes that both cards should be on the same network and connects both of them to the Wireless N router. This causes problems as I then cannot browse the internet as the cards conflict. I already set up the Ralink card to take priority (its wlan0). How do I force NetworkManager to assign a different network to each card? Is there a configfile that I can specify MAC addresses or using a driver or a plugin for NetworkManager? Thanks in advance for any help.

---

