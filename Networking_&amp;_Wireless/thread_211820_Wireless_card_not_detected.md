---
title: "Wireless card not detected?"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by mfarquhar on 2006-07-08
i've never done any networking in linux before, i just physically installed an:

AirLink AWLH3026 Wireless PCI card

i don't know ANYTHING about networking in linux
i dual-boot with windows ME and it works there, but i just don't know how to get it working in linux

PS. i'm still running Breezy should i upgrade first(i have the Dapper CD)...will the upgrader detect it? install it?

please help[-o<

*EDIT* how can i install ndiswrapper without directly downloading it to ubuntu (i.e. sneakernet...i have to download it from windows then move it to linux...)

---

### Post by Zerocool10482 on 2006-07-09
I have the same card. Fry's right. I hate Airlink but I just need a card. Oh well.

---

### Post by Zerocool10482 on 2006-07-18
Try a D-Link 1320. It works out of box. Good luck.

---

### Post by Stinger on 2006-07-18
Your card has a good chance with Dapper , it is supported in Linux.
Ralink RT2561 driver:
> There is a Linux driver for the Ralink RT2561 chipset. This means that at the moment cards like the Airlink Tech AWLH3026 PCI card, do work in Linux. However: Only with Ralink's driver since January 2006.

So with Breezy your only chance is to use ndiswrapper and your Windows driver.

Personally I prefer Dapper.

Have you tried booting from your Dapper CD to see if you card shows in System > Administration > Networking ?

---

### Post by mfarquhar on 2006-07-21
i honestly never thought of using the live thing to check it, i'll go do that *scampers off*

---

### Post by mfarquhar on 2006-07-21
i just did the Live thing and it detected my card, i was able to activate it, but i still couldn't use the internet (probably because i didn't really know what i was doing)

i have comcast internet and i use a router to get it to my linux box (don't know if thats important or not)

---

### Post by Stinger on 2006-07-26
> **mfarquhar said:**
> i just did the Live thing and it detected my card, i was able to activate it, but i still couldn't use the internet (probably because i didn't really know what i was doing)

i have comcast internet and i use a router to get it to my linux box (don't know if thats important or not)

I would think your trouble is you need to load your wireless network module to make it work , this is normaly done when you boot , but since you just activated it you'll have to reboot.
And ofcourse you can't do this when using the live CD , you lose all settings.

If you know which module your card is using , you can use the "modprobe" command to load it , but......

I think the best solution is to install Dapper , setup the network and reboot to make it work.

I'll be there to guide you the best I can.  :-D

---

