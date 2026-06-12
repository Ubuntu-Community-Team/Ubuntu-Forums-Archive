---
title: "Spotty Wireless since Ubuntu"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by Synoc on 2009-12-13
ok first off, I'm coming from Windows XP, got sick of some... nevermind no one cares why I upgraded to a better OS, just that I did. Fresh installed Ubuntu, used the hardware driver utility and an Ethernet cable to download and install the Broadcom B43 wireless driver, to get my wireless up and running, it works great when I'm on the same floor as my router, if I head up stairs, it's spotty at best, when it DOES connect, it wants to reenter my WEP key... it still has it saved in Network connections. When I was using windows it worked fine. 

need some help.

Here's the info from a lspci
>  00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller 

in addition, I apparently have a Dell Dual-band Wireless 1450 card installed by Dell with my computer. which is probably the one that was getting better reception.

---

### Post by sophicsage on 2009-12-13
The same thing is happening to me.  I've mentioned this before but received no responses yet, but it's a new post.

Before I removed Windows, wireless reception was 100%.  Now I hover around an average of 35%.  This isn't really acceptable and I know it is not my hardware or a router problem.  My wife's laptop works just fine in the same location.

I've had the same issue with the system wanting my WEP key again.  Sometimes it drops the connection irreparably and I must restart.  The connection, right next to the wireless router in the living room, at best is 78%.  On this side of the house I have 37% right now and my wife's is again....100%.  This is a post Ubuntu install issue.

What computer do you have?  Mine is a Sony NS series laptop.

---

### Post by Synoc on 2009-12-13
well according to DEL I have the Dell wireless dual-band 1450, but I couldn't get on the internet wireless ly until I downloaded the BROADCOM B43 driver, so my question is this "did broadcom MAKE the dell card? and LINUX doesn't pick up on subtle nuances of it? like the new name of it and the added range? or does windows simply have a lower threshold it will remain connected to.?"

---

### Post by wilee-nilee on 2009-12-13
Routers generally have a access IP, that on some routers allows you in to adjust several things like a firewall and monitor wired and wireless connections, and wifi signal strength. I got my IP access from the IP provider so if the routers are provided by your IP call them. If it is a independently purchased router it mosy likely has this access as well so contacting the maker and the IP providor and or Google the router for more information.

Your computer should have the password saved and be auto connecting so right click on the wireless icon and click on edit connections then wireless then edit the connections and make sure auto connect is ticked on.

---

### Post by Synoc on 2009-12-13
> **wilee-nilee said:**
> Routers generally have a access IP, that on some routers allows you in to adjust several things like a firewall and monitor wired and wireless connections, and wifi signal strength. I got my IP access from the IP provider so if the routers are provided by your IP call them. If it is a independently purchased router it mosy likely has this access as well so contacting the maker and the IP providor and or Google the router for more information.

Your computer should have the password saved and be auto connecting so right click on the wireless icon and click on edit connections then wireless then edit the connections and make sure auto connect is ticked on.

My wireless settings on my router don't have an adjustable signal strength, but this very laptop under Windows had better reception with it than it does under Ubuntu. Now Ubuntu calls this card a Broadcom B4309. Dell calls this card Dell wireless 1450. is it that Dell has something in their driver that allows for better signal receiving? or is there something I am missing?

With regards to my WEP key, I do have it saved and when it disconnects me and I have to reconnect, again upstairs further from my router (where Windows would still pick it up) it sometimes asks me for my key again, I am PROUD to say I don't have a 128 bit encryption key memorized : ) on the other hand if I disable and re-enable it, it will work, if it connects at all.

---

### Post by wilee-nilee on 2009-12-13
I am not knowledgeable in this area, so hopefully others will help.

---

### Post by Synoc on 2009-12-14
still lookin for some help (thanks though for the pointer, I did learn something new atleast so it was still helpful in a manner : )

---

