---
title: "Cant Connect To The Net"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by Chaosmachine420 on 2010-09-07
I just installed Ubuntu and I cannot connect to the internet. Im new at this I wanted to try it out before I restore my computer back to Windows. So I need to be walked through it all still trying to figure out where all the shortcuts and everything are.

---

### Post by pricetech on 2010-09-07
Wired ?  Wireless ?  What kind of computer ?  What kind of NIC ?  What type of Internet Connection ?

More information please.

---

### Post by Chaosmachine420 on 2010-09-07
Im doing it wired for the tower. Its a built in wired connection. Its a self build too. The motherboard is an Asus P7P55D-E Pro and the connection is Ethernet.

---

### Post by wojox on 2010-09-07
What if you open a terminal and type

```
ping -c 3 www.google.com
```

---

### Post by Chaosmachine420 on 2010-09-07
It says ping: unknown hose [www.google.com](www.google.com).

---

### Post by wojox on 2010-09-07
What did you use to install it? You typically need a network connection to install.

What does this tell us?

```
ifconfig
```

---

### Post by Chaosmachine420 on 2010-09-07
link encap:local loopback
inet addr:127.0.0.1 mast 255.0.0.0
inet6 add : ::1/128 scope:hose
up loopback running mtu:16436 metric:1
rx packets:76 errors:0 dropped:0 overuns:0 frame:0
tx packets:76 errors:0 dropped:0 overuns:0 carrier:0
collisions:0 txqueuelen:0
rx bytes:5840 (5.8 kb) tx bytes:5840 (5.8 kb)

---

### Post by Chaosmachine420 on 2010-09-08
So no one can figure out what is wrong with my net not turning on.

---

### Post by slashwannabe94 on 2010-09-08
so your using a router then ? have you correctly set up your internet >?

---

### Post by Chaosmachine420 on 2010-09-08
Ok its not the program thats wrong but its the the network card built in that is messed up because i reinstalled windows to see if it would work and its having the same trouble. Its saying my cable is bad which I plugged another cable in that I know is good and is doing the same thing. So to fix this issue first off would I get a new motherboard or install a network card and not worry about a new motherboard.

---

### Post by Iowan on 2010-09-08
Network card is probably less expensive... unless you're looking for a good excuse to upgrade MB ;)
You may need to disable the onboard, though. First choice would be via BIOS.

---

### Post by Chaosmachine420 on 2010-09-09
Well I have a network card and I just put in sadly its doing the same thing. My motherboard I rather keep it this is the best one so far I have used and its easy and simple mostly. So your saying to even fix this at all to disable it in the bios.

---

### Post by grahammechanical on 2010-09-09
First off (as you say), Stop and think!

Does the computer boot? Can you access the BIOS settings? Do you really need a new motherboard? Think before rushing off to do something that may or may not solve the problem.

2) get hold of a Ubuntu live CD. Test out Ubuntu. See if you can get internet access before installing the Operating system.

3) If you choose to install Ubuntu tell it to create three partitions. One for the Windows installation that you already have installed. One for the Ubuntu Operating System (15 - 20 GigaBytes) mount point / . One for all your data files as big as you like, mount point /home.

Having home on a separate partition lets you re-install Ubuntu without losing your data or your settings. Having a dual boot system lets you use the computer if one OS is mucked up.

It is unusual for Ubuntu to fail to give network access by ethernet cable. In Windows you may have the wrong settings for the router. Is the router switched on. How does an OS know the difference between a faulty cable, a disconnected cable and a router that is switched off. There are indicators on the router. What information do they give you. Have you reset the router? This put its settings back to those it had when it left the factory. If you changed those settings then, the OS may not be able to connect to the router if the router is reset to its factory settings.

Regards

---

### Post by Chaosmachine420 on 2010-09-09
Well first off I couldnt connect to the net using the trial version and i thought maybe i need to install the cd it said i could along side windows when i was in windows. After i did that came up all the time. Its something that ubuntu installed because i even tried directly plugging into my modem and it still would say my cord is bad after and this is all on windows side.

---

### Post by pricetech on 2010-09-13
> **Chaosmachine420 said:**
> Well first off I couldnt connect to the net using the trial version and i thought maybe i need to install the cd it said i could along side windows when i was in windows. After i did that came up all the time. Its something that ubuntu installed because i even tried directly plugging into my modem and it still would say my cord is bad after and this is all on windows side.

Windows will show a cable unplugged if there's a problem, but doesn't pretend to diagnose a "bad cable".

If you have a physical layer problem, it's usually the NIC itself, or a bad port in the router / switch that you're plugging in to. assuming you are using a known good cable.

Do any lights on either the router / switch or the NIC show a physical connection ??  Lets start there.

---

### Post by Chaosmachine420 on 2010-09-13
Ok now oddly enough my internet is bad on this computer but now windows 7 wont start up up after the first time ur on the desktop. It shows the default background.

---

### Post by pricetech on 2010-09-20
If I'm reading right, it sounds like you've damaged your windows profile in some fashion, forcing it to be recreated from the default.

---

