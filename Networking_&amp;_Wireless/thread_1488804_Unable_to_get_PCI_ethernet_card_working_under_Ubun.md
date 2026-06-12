---
title: "Unable to get PCI ethernet card working under Ubuntu 9.10"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by philross2010 on 2010-05-20
Hi there,
I have just installed a generic PCI ethernet card into a fairly low powered system (Celeron 766MHZ, 512mb Ram, 40 Gb HDD, Generic sound and video). The card came with no drivers. I have since installed Ubuntu 9.10, and up to a point everything is fine and looks great. However when I connect an ethernet cable up to the PCI card (in the hope of connecting with the Internet), nothing happens. I am thinking that I need Ubuntu drivers for the PCI card ? or does Ubuntu 9.10 come with drivers and I need to go into the 'engine room' to sort it all out ?
Would really appreicate help on this as I so want to not use Windows ever again.
Phil Ross

---

### Post by chili555 on 2010-05-20
> does Ubuntu 9.10 come with drivers and I need to go into the 'engine room' to sort it all out ?It comes with most drivers, let's go to the engine room. Please open a terminal and do:```
lspci -nn
```Post the part that is clearly your ethernet card, similar to this:```
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
```We will google the device id, something like 123a:456b and see what we can find. Let's also look at:```
dmesg | grep eth
```

---

