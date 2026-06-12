---
title: "Cannot Make Home LAN"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by xramoj on 2009-03-29
I've got PC(linux, Ubuntu 8.10) and Noutbook(win) at home.
PC got 2 LAN cards, first one is configured as manual, and it works properly. Noutbook configuration:
192.168.0.2
255.255.255.0
192.168.0.1
DNS 1/DNS 2, and connected to LAN2.
I tried to configure LAN2 as it was on windows:
192.168.0.1
255.255.255.0
xxx.xxx.xxx.xxx(my IP)
DNS1/DNS2, but it doesn't works. At windows there was option, that I allow other connections through LAN1.
What should I do?

---

### Post by Iowan on 2009-03-29
Network Manager seems to have problems with multiple interfaces.  [This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page may/not help.

---

### Post by BkkBonanza on 2009-03-30
It looks like you're telling your notebook the gateway is 192.168.0.1 but from what you say thats not your gateway, so it cannot get to the dns server (unless you are running one yourself on that ip). If you have two LAN cards then each one has it's own subnet/network. So if you want anything on one to talk to the other then you will need a route command to bridge the two. Suggest googling "bridge route linux".

---

### Post by xramoj on 2009-04-01
Thank,s it may help

---

