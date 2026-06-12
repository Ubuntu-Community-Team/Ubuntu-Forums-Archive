---
title: "Wireless is disabled by hardware switch Xubuntu 12.04"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by TheThingThatFlies on 2012-05-25
Hi,
I just installed Xubuntu 12.04 using Wubi to dual boot with Windows Vista. I tried to connect to my wireless router, which is a Netcomm NB6Plus4W. When i went into the networking menu, it says, "wireless is disabled by hardware switch". I have checked along the side of my laptop, which is a HP Compaq nc6220. I have tried multiple methods but none of them work.
 
Can someone please help me?

---

### Post by praseodym on 2012-05-26
Hi,

please show the terminal outputs of the commands:
> lsmod
rfkill list
iwconfig
Check the BIOS settings and/or reset the BIOS to default.

---

### Post by Toz on 2012-05-26
Also, [http://h18000.www1.hp.com/products/quickspecs/12130_na/12130_na.html]("http://h18000.www1.hp.com/products/quickspecs/12130_na/12130_na.html") - button #3, is it enabled (on)?

---

