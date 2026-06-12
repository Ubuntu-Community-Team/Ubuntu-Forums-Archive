---
title: "Intel HD graphics video adapter not recognized by Ubuntu 12.04"
date: 2013-05-22
forum: Multimedia Software
---

### Post by MEPHIST0FELIZ on 2013-05-22
Hello everyone

I just installed Ubuntu 12.04 in my HP dv5 laptop with the following hardware:

[I]Product Name dv5-2146la
Product Number XR121LA
Microprocessor 2.40GHz Intel Core i5-450M Processor with Turbo
Boost Technology
Memory 4 GB DDR3 DIMM
Maximum
Memory
8 GB 2 slots
Video Graphics Intel HD Graphics with up to 1696MB total graphics
memory
Hard Drive 500 GB (7200 RPM)
Multimedia Drive LightScribe SuperMulti 8X DVD±R/RW with Double
Layer Support
Display 14.5" diagonal High-Definition HP BrightView LED
Display (1366 x 768)
Network Card Integrated 10/100/1000 Gigabit Ethernet LAN
Wireless
Connectivity
Wireless LAN 802.11b/g/n WLAN
Bluetooth with WiDi
Sound Altec Lansing with Dolby Advanced Audio
Keyboard Full size keyboard
Pointing Device HP Clickpad with On/Off button[/I]

The problem is that my video adapter is not recognized by ubuntu, currently I'm using the VESA Intel ironlake driver which was installed by default.

I've read that installing the mesa-utils package would solve the problem bu it didn't work for me.

I would really appreciate any help with this problem.

Thank you very much in advance.

Kasim.

---

### Post by Bucky Ball on 2013-05-22
*Thread moved to **Multimedia & Video**.*

You might have more luck here.

---

### Post by MEPHIST0FELIZ on 2013-05-22
Thank you very much, I had not realized there was a Multimedia & Video section.

---

### Post by Mark Phelps on 2013-05-22
If your video chipset was not recognized by Linux, you would have a totally black screen with no display.  The fact that you can (I presume, or you would have said otherwise) see a desktop is proof that Ubuntu has loaded the proper drivers for your chipset. Intel drivers are installed as part of the initial setup.

---

### Post by sammiev on 2013-05-22
Go into your software package manager and add mesa-utils. That should just about do it.

---

### Post by MEPHIST0FELIZ on 2013-05-23
Thank you very much guys for helping me.

I already tried installing the mesa-utils package but it didn't work.

Actually I can see the desktop, but the compiz-like visual effects are not enabled and I can't change the size of the launcher icons, that's why I think Ubuntu did load the right driver.

Anyone knows how can I enable the compiz-like effects and change the size of the launcher icons?

---

### Post by Bucky Ball on 2013-05-23
> **MEPHIST0FELIZ said:**
> 

Anyone knows how can I enable the compiz-like effects and change the size of the launcher icons?

You'll have a better chance of help by marking this thread as solved (follow link in my signature) and starting a new thread with an appropriate title as the title of this one now has little to do with what you're asking. You can leave a link to the new one here if you want. Good luck. ;)

---

### Post by MEPHIST0FELIZ on 2013-05-24
Thank you very much for the advice.

I Just created a new thread [here]("http://ubuntuforums.org/showthread.php?t=2148347&p=12662347#post12662347").

---

