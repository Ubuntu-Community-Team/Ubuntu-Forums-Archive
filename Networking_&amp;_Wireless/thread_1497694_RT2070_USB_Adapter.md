---
title: "RT2070 USB Adapter"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by alberto_chaos on 2010-05-30
Hello, first a must say that my english is very very poor but i think you will understand my problem.
I have bought an antenna/usb adaptor, the antenna is named "aquário usb-2510" and it's adaptor is the **RT2070**.
Well, once i got home my computer was logged into [COLOR=Indigo]windows seven[/COLOR], i just plug in the antena and magically [COLOR=Indigo]everythings seems ok[/COLOR], i've installed the management tool in the cdrom just to take a look... 
Everythings fine but, it's windows! and my primary OS is Linux, until now the great** Lucid Lynx**, booted , logged-in, usb connected, nothing, really nothing, just the old ralink rt61 pci I have.. 
It's about like 1 month my pain, googling, searching, compiling drivers, changing blacklists, again again again.. but NOTHING changes, iwconfig returns the same interfaces as ever: lo, eth0 and wlan0 with the pci adapter, that is currently without antenna and getting nothing in the air, the "aquarius" is a big and external one, on windows i got about like fifty AP's very well, just to emphatsize that **ubuntu is not recognizing the adaptor**.
I'm stressed and really tired, if ubuntu/backtrack don't really support this adaptor i'll need to buy another one, wich will be very unprobable now... 
I hope my english is understandble and my problem solvable. Thanks since now, and please** share any solution** another than buying another adaptor. =]

---

### Post by darkod on 2010-05-31
OK, lets see first if we have everything correct.
The Ralink website doesn't mention RT2070 chipset, like it doesn't exist.
To check the exact chipset used, in ubuntu run:

lsusb

Look for the line where the Ralink is reported and see which RTxxxx chipset is reported.

---

### Post by alberto_chaos on 2010-06-01
> **darkod said:**
> OK, lets see first if we have everything correct.
The Ralink website doesn't mention RT2070 chipset, like it doesn't exist.
To check the exact chipset used, in ubuntu run:

lsusb

Look for the line where the Ralink is reported and see which RTxxxx chipset is reported.

darko, even the cd-rom that came with the adaptor, the real driver name is rt2870, i don't know why, and the rt2870 is on the ralink website, i have followed some threads in foruns that tells me to try putting things in blacklist and using the rt3070 and blablabla, nothing works, what a i need anything solid about this adaptor on ubuntu, or on any other distro linux.

---

### Post by darkod on 2010-06-01
You wrote RT2070, not RT2870 and that's why I asked.

The first thing to try for that chipset I think, is blacklisting rt2500usb. Did you try that?

Don't blacklist rt2870sta right now, if it's in the blacklist delete it from there. Blacklist just rt2500usb and see how it goes.

In my case ubuntu was loading rt2500usb by mistake and it was interfering with the adapter properly functioning.

---

