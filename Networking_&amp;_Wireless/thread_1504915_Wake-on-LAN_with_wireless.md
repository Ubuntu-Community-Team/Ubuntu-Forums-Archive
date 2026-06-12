---
title: "Wake-on-LAN with wireless"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by Arthur_D on 2010-06-08
Hello, I tried to follow [this guide]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_Wake-On-Lan_%28Ubuntu%29") on how to set up wake-on-lan with a laptop, but instead of 
>         Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes
I got this:
>         Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: no

I must confess I didn't see any setting in the BIOS that directly referred to WoL, but I enabled something and hoped it should be right. Is this the problem? Is there any way to check if the hardware supports WoL other than looking through the BIOS?

Thanks for your time. :)

---

### Post by gobbledigook on 2010-07-14
hi there!

your thread title says "Wake-on-LAN with **wireless**" But the nature of Wake-on-Local-Area-Network is that you can only use it with a cable... that's why the guide you refer to references eth0 the whole time.

---

