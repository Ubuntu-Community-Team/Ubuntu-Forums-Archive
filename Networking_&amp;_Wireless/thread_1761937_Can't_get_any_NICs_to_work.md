---
title: "Can't get any NICs to work"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by Snipersnest on 2011-05-18
Ok so I'm gonna try and explain this easily..
 
I installed 11.04 32bit on an older HP P4 machine. Boots up and goes to classic desktop.. But networking looks like a wifi devices rather than a wired connection.
 
I installed another NIC rather than the onboard but had the same result.. I also tried yet another PCI NIC and a USB NIC with the same result. I also tried to set my connection to manual and give myself a static IP, but had no such luck.
 
I know my internet connection works because I'm on another machine typing this to you all.. All the NICs also work in W7 on the dualboot setup I did.
 
What log file or what do I need to show you to resolve this? Thanks!

---

### Post by chili555 on 2011-05-19
> But networking looks like a wifi devices rather than a wired connection.This isn't very clear to me; can you explain it, please?

I assume you are trying to get your on-board NIC to connect to the internet. Please open a terminal and post:> lspci -nn
ifconfigThanks.

---

