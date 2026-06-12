---
title: "Skystar2 in Jaunty"
date: 2009-05-02
forum: Multimedia Software
---

### Post by DGTL_Magician on 2009-05-02
Hi,

I have a mediacentre running since 2,5 years now. Since 1,5 years this is equipped with a Skystar2 PCI DVB-S card.

This card has worked fine on several upgrades. Today I upgraded to Jaunty and my card isn't recognized anymore. It even does not show in lspci anymore.

I did a scan for channels during the upgrade so I'm fairly sure the upgrade broke things and it's not an problem with my card itself.

In the past I needed to do:

modprobe budget
modprobe stv0299

to get my card recognized, now this does not give any messages in dmesg.

---

### Post by micko45 on 2009-05-04
Hi,

I have having the same problem. 
I have the 2.8 rev card but after the upgrade it doesn't work any more :(

I used to use the instructions from [http://www.linuxtv.org/wiki/index.php/TechniSat_SkyStar_2_TV_PCI_/_Sky2PC_PCI](http://www.linuxtv.org/wiki/index.php/TechniSat_SkyStar_2_TV_PCI_/_Sky2PC_PCI) to get my card working.
This still compiles but doesn't create a device in /dev/dvb/ anymore.

I tried the drivers from the techisat web site 
[http://www.technisat.com/index6be4.html?nav=Downloads,en,33&pID=174](http://www.technisat.com/index6be4.html?nav=Downloads,en,33&pID=174)
With no luck either as i can't get it to compile.

According to Linuxtv.org the card had build in support from kernel 2.6.28-git5.
I have kernel 2.6.28-11-generic installed, does this mean the support should be in my kernel?

thanks
Michael

---

### Post by micko45 on 2009-05-06
Just an update,

I downloaded and compiled the kernel 2.6.29.2 and the card started working :-) That Kernel has support for it.

Rgds
Michael

---

### Post by peterinca on 2009-12-06
I need Satellite Internett have a SkyStar2 PCI card put it in the slot. And now, what do I do to get it work for Internett downlink?
It looks like you figured that one out. . .
would be great if you could give me some advise. But you need to use easy to understand language to communicate to me please. Thanks

---

