---
title: "backtrack wireless cracking?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2010-09-06
I've recently moved into my dad's and he has two routers, i've connected to one as he gave me the key, I wanted to try and crack the other considering that this is going to be one of the most sensible ways to learn a bit about backtrack and I was just wondering if anybody could tell me what I'm supposed to be looking at as a starting point, there are many guides but none seem to really work.

I'm using an N1 Belkin router and on Ubuntu I needed ndiswrapper to get the wireless card working and I'm running Backtrack through a virtual machine in Ubuntu, though backtrack returns no wireless card installed, do I need to get the drivers and re-install and use ndiswrapper in backtrack and then will most of the other seemingly simple guides start to work as at the moment I'm just getting no device found and I/O errors?


I am sure that there is no problem with me accessing the second router and Im not breaching any legal issues this way.

---

### Post by louis--taylor on 2010-09-06
Although this is fairly easy, I don't think this forum is the place to discuss it.

EDIT: Sorry! knee-jerk reaction there! Try aircrack-ng:
 [http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

Why not run backtrack off the live cd? I'm sure it would make it more straightforward.

---

### Post by ironic.demise on 2010-09-06
> **louis--taylor said:**
> Although this is fairly easy, I don't think this forum is the place to discuss it.

EDIT: Sorry! knee-jerk reaction there! Try aircrack-ng:
 [http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

Aha thanks, I was doing a bit of looking around and I'm thinking about just live-cd booting it as VM seems to be a pretty poor way of doing it.
Thanks for the link.

---

### Post by louis--taylor on 2010-09-06
> **ironic.demise said:**
> Aha thanks, I was doing a bit of looking around and I'm thinking about just live-cd booting it as VM seems to be a pretty poor way of doing it.
Thanks for the link.

No problem!

---

### Post by BkkBonanza on 2010-09-07
You won't have any success with a VM because it uses virtual network drivers and for most of this stuff you real network adapters for monitor mode and injection.

I'm not sure about the status of ndiswrapper based adpaters but I'm somewhat sure they don't support the things you need. You will likely need to buy a cheap usb dongle for doing this. My ZyDas zd1211w based adapter seems to work fairly well, and was really cheap. 

Anyway, you're best off reading on the aircrack and backtrack forums as they talk a lot about adapters that work and don't work.

---

### Post by ironic.demise on 2010-09-07
> **BkkBonaza said:**
> You won't have any success with a VM because it uses virtual network drivers and for most of this stuff you real network adapters for monitor mode and injection.

I'm not sure about the status of ndiswrapper based adpaters but I'm somewhat sure they don't support the things you need. You will likely need to buy a cheap usb dongle for doing this. My ZyDas zd1211w based adapter seems to work fairly well, and was really cheap. 

Anyway, you're best off reading on the aircrack and backtrack forums as they talk a lot about adapters that work and don't work.

hm, true. Imight go out and buy a USB then, I could use it on a laptop then too.

---

### Post by BkkBonanza on 2010-09-07
Do a bit of reading about which models work. It gets really complicated because the manufacturers change the chipsets inside sometimes without any model# change. 

I had good luck too with a $10 eBay cheapo chinese dongle based on the RT8181 chip. The nice thing was it had an SMA connector with 7dB antenna (well, that's what they claim). That's nice for using external antennas and playing with sat dish, woks, and cans etc.

---

### Post by Ernie S. on 2010-09-19
Ndiswrapper WILL NOT work with aircrack-ng. Even the aircrack website states ndiswrapper will never be supported. Part of this is due (I believe) to the fact that ndiswrapper uses the proprietary windoze drivers to run the card. Windoze drivers do not support injection, thus are unusable for cracking wep.

---

