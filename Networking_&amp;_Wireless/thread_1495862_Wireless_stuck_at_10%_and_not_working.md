---
title: "Wireless stuck at 10% and not working"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Jedster on 2010-05-28
I'm trying to get UNR working on a Joggler having followed instructions on the joggler forum and UNR seems fine - however the wireless strength is stuck at 10% and I can't connect to the net. I've moved the joggler to within 10' line of site of the router and it still sticks at 10% - upstairs through walls and floors - 10%!
If I use the native joggler software it shows a very good signal near the router and good upstairs so I don't think it's the hardware at fault. 

It did work fine at one point, and I even backed up a .img of it all working, but even going back to that image doesn't fix the problem so I sort of think the problem isn't UNR, but rather something UNR has done to a hardware setting.

Any thoughts please? This is driving me nuts.

Thanks,
Jeddy

---

### Post by chessnerd on 2010-05-28
Do you know what wireless card the computer has? It is possible that the driver you are using doesn't work very well. The repositories have some proprietary drivers for specific cards. In Synaptic, search for your wireless card brand and see what comes up.

If that isn't the case, you could take a look at backported drivers. I installed them under Ubuntu Karmic and they greatly enhanced my wi-fi experience on my laptop. To get backported drivers, open up the Software Sources manager and check backports. Then, install these:

linux-backports-modules-lucid-generic
linux-backports-modules-wireless-lucid-generic

If you have a version other than 10.04 substitute the version name where "lucid" is. You'll probably only need the wireless one, but having both shouldn't hurt anything.

---

### Post by Jedster on 2010-05-28
Thanks for the suggestion, I've not checked if it works connected via ethernet yet, fingers crossed then I'll try those backportedl drivers.

Cheers!
Jeddy

---

