---
title: "Wireless Internet Help"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by Xclusiveitalian on 2010-07-24
I am 100% new to Ubuntu and i heard a lot of good things about it so i decided to install it on my old laptop. I installed Ubuntu From Windows Vista Home premium 32bit to 10.04(netbook version) the newest version, on my HP Pavilion Dv6604nr Entertainment Notebook PC. 

After the install I noticed that my wireless button switch is always red no matter which way I turn it. Normally when it is switched to on it will turn blue, however, it is always red. This lead me to believe that maybe my network card isn't installed?

Also more importantly, on the top where I can click to connect to the internet, both Wired, and Wireless are grayed out and it says Disconnected under both. I have tried several times to try and connect to the internet on it but failed using "Connect to hidden Wireless network," and "Create new wireless network." I failed both times, and according to my other computer(in which the router is connected to) my ubuntu laptop isn't even detected as trying to connect to that network. 

My router is 100% working and am connected to it right now using my other laptop to post this. I did enter the correct password and even selected the correct Wireless security. 

Using "lspci" in the terminal I found my network controller to be:

"03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)"

Any help is appreciated, I would really hope to get the internet working on this, I have a adequate knowledge of Windows PCs but the code part of ubuntu confuses me.

---

### Post by Xclusiveitalian on 2010-07-25
Please can anyone help

---

### Post by gordintoronto on 2010-07-25
I suggest Googling: BCM4311 ubuntu

---

### Post by antiballs on 2010-07-25
Have you gone to System>Admin>Hardware Drivers? If you havent go there and activate the drivers, its a good place to start

---

### Post by Xclusiveitalian on 2010-07-25
I was up all night but I finally got it to work!!! 

I did a Fresh Install and didn't let the window ever go into lock mode(If that matters, I think it was messing mine up) by moving the mouse from time to time. Than I directly inserted my ethernet cable into my laptop. I completely updated it using the update manager, than rebooted. Than went to System/administration/hardware drivers and activated both Wireless Drivers. Than rebooted and it worked!

There were dozens of different fixes online for my specific card and it made it confusing, glad I got it to work!

Solved!

---

