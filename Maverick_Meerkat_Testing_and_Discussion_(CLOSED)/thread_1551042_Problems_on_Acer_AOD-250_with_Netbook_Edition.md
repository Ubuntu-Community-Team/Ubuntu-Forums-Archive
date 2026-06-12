---
title: "Problems on Acer AOD-250 with Netbook Edition"
date: 2010-08-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ATA0311 on 2010-08-11
So I am completely new to Ubuntu, 10.04 was my first time ever installing and using. A problem that i had with 10.04 Netbook Edition was with hibernating. Whenever I would close the lid nothing would happen and whenever I would plug or unplug the Acer it would hibernate each time. I found a fix for it online, but it was a pain. Also, 10.04 would make my Acer run incredibaly hot. I downloaded 10.10 Alpha 3 tonight and tried it out and noticed that all of these problems still exist. Is there any way for me to report this to someone or does anyone have an easy fix for these problems?

---

### Post by cariboo on 2010-08-11
Reporting bugs, is what we do here. Have a look at this [document]("https://help.ubuntu.com/community/ReportingBugs"), it explains the bug reporting process.

It would also help a lot if you listed the hardware your system uses:

[list]
[*]CPU
[*]Ram
[*]graphics chipset
[*]network adapters
[/list]

If you aren't sure about some of the components, just open a terminal and type:

```
sudo lshw
```

the above command will give a complete listing of all your hardware.

---

### Post by ATA0311 on 2010-08-11
CPU - Intel(R) Atom(TM) CPU N270   @ 1.60GHz
RAM - 1GB DIMM DDR2 Synchronous 533 MHz
Graphics - Mobile 945GME Express Integrated Graphics Controller
Network - AR5001 Wireless Network Adapter, Atheros AR8132 / L1c Gigabit Ethernet Adapter

---

### Post by cariboo on 2010-08-11
I've got exactly the same hardware in my Compaq mini 110 except for wireles, it runs at a pretty constant 51°C.

I've been running unity since it was released, and haven't had any serious problems.

---

### Post by ATA0311 on 2010-08-11
So do you have any idea why simply unplugging my Acer would cause it to hibernate and when i plug it back it to hibernates again?

---

### Post by ranch hand on 2010-08-11
Is this about 10.10-testing?  If not, remove post and repost on the ABT or General Help forum.

If it is, a lot more info on your box is needed.

---

### Post by ATA0311 on 2010-08-12
In my original post I explained all of the problems I was having in 10.04 netbook edition I am having with the 10.10 Netbook Edition Alpha 3. I was simply trying to see if this is a common problem with my model Acer or if I am the only one and someone could help me fix this.

---

### Post by cariboo on 2010-08-12
Right-click the battery icon and select preferences and check the settings, I have it set to sleep when the lid is closed, and hibernate if I don't wake it up in an hour.

---

### Post by ranch hand on 2010-08-12
Sorry, we have had a number of folks on here in the last week or so about unrelated versions.

Laptops are mostly a mystery to me.  My wife does have one.  Sys76 preinstalled with 9.10.

Hope you get it straightened out.

---

### Post by ATA0311 on 2010-08-12
> **cariboo907 said:**
> Right-click the battery icon and select preferences and check the settings, I have it set to sleep when the lid is closed, and hibernate if I don't wake it up in an hour.
I booted 10.10 from a usb and tried what you said and it only made things worse. Before when i unplugged or plugged it back in it would only hibernate. Now it causes my Acer to shutdown completely.

---

