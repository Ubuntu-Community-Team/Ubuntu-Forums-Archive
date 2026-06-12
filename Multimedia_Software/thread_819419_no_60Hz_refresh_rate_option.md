---
title: "no 60Hz refresh rate option"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Fatfool on 2008-06-05
I'm using a geforce 7600GS with an ATi RS482 motherboard and I have used the restricted driver but there is no 60hz refresh rate to choose from. it was there when this same comp was running windows XP btw so I'm gonna guess that this LCD monitor can obviously take it. seems that this refresh rate is more like 30hz or so though in practical usage
heres a screenie:

[IMG]http://img338.imageshack.us/img338/1556/poorrefreshrateew2.jpg[/IMG]

very odd. and seems the drivers from Nvidia's site are apparently impossible to install on Ubuntu (according to some threads) I can't test those out.

btw since those nvidia site drivers can't be installed (easily; or rather I still can't find a guide i can understand on how to do it haha), theres no control panels for the more advanced options?

---

### Post by diggity on 2008-06-05
Try using nvidia-settings (might have to run as sudo)

---

### Post by Fatfool on 2008-06-05
> **diggity said:**
> Try using nvidia-settings (might have to run as sudo)
'sudo nvidia-settings'?

---

### Post by Pjotr123 on 2008-06-05
Two things:

1. the 50 and 51 Hz are not really that: the Nvidia driver uses "wrong" hz numbers on purpose, to differentiate between plural screens (or to keep the possibility of unique identification of plural screens open). So: no worries, mate.  :-)

Check the BIOS of your screen with the physical buttons on your screen: that will show the real Hz number (probably 60 Hz).

2. nvidia-settings: see an explanation (and usage) here:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

Greeting, Pjotr.

---

### Post by Fatfool on 2008-06-06
> **Pjotr123 said:**
> Two things:

1. the 50 and 51 Hz are not really that: the Nvidia driver uses "wrong" hz numbers on purpose, to differentiate between plural screens (or to keep the possibility of unique identification of plural screens open). So: no worries, mate.  :-)

Check the BIOS of your screen with the physical buttons on your screen: that will show the real Hz number (probably 60 Hz).

2. nvidia-settings: see an explanation (and usage) here:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

Greeting, Pjotr.
ah I see ok thanks. yeah it was set at 75hz but 60hz seems to give no difference. guess its the lousy monitor at fault.

---

