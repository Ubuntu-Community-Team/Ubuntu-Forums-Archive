---
title: "Trouble getting my nVidia 745M to work on Asus N550... bbswitch issue?"
date: 2014-01-09
forum: Multimedia Software
---

### Post by broekeman on 2014-01-09
Hello all,


About a week ago I bought a fresh new Asus N550 laptop. Little did I know those things come with hybrid graphics nowadays – this one comes equipped with an Intel (integrated) and an nVidia (dedicated) videocard of the type 745M. I assumed there would be only one videocard, namely the nVidia one, but I can now see having two videocards in one laptop has serious advantages when it comes to power consumption and heat generation. 

I had to learn that to utilize the nVidia card, I was supposed to install a program called Bumblebee. I did so according to the instructions here: [https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation)
I am running Ubuntu 13.10 so I followed those instructions. Everything went well after rebooting, except for the following. When executing optirun [application], I get the following error:

```
[  511.456378] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:4:0:0.  Please

 [  511.456413] [ERROR]Aborting because fallback start is disabled.]
```

This is one of the most common errors in bumblebee if the search hits are to be trusted. Now, I have followed the instructions on the bumblebee website but the bus ID is correct. I have searched for other solutions and thus far it has cost me about a day in total without any fruitful results. 

The only thing I have found out, it that is it probably caused by bbswitch, that has not been properly incorporated into the kernel. Executing dmesg | grep bbswitch gives this error:

```
 [   19.394581] bbswitch: module verification failed: signature and/or required key missing - tainting kernel
[   19.394711] bbswitch: version 0.8
[   19.394715] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   19.394718] bbswitch: Found discrete VGA device 0000:04:00.0: \_SB_.PCI0.RP05.PXSX
[   19.394726] bbswitch: failed to evaluate \_SB_.PCI0.RP05.PXSX._DSM {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0} 0x100 0x0 {0x00,0x00,0x00,0x00}: AE_NOT_FOUND
[   19.394730] bbswitch: failed to evaluate \_SB_.PCI0.RP05.PXSX._DSM {0xA0,0xA0,0x95,0x9D,0x60,0x00,0x48,0x4D,0xB3,0x4D,0x7E,0x5F,0xEA,0x12,0x9F,0xD4} 0x102 0x0 {0x00,0x00,0x00,0x00}: AE_NOT_FOUND
[   19.394737] bbswitch: failed to evaluate \_SB_.PCI0.GFX0._DSM {0xA0,0xA0,0x95,0x9D,0x60,0x00,0x48,0x4D,0xB3,0x4D,0x7E,0x5F,0xEA,0x12,0x9F,0xD4} 0x102 0x0 {0x00,0x00,0x00,0x00}: AE_NOT_FOUND
 [   19.394738] bbswitch: No suitable _DSM call found.
```

But, I cannot insert the bbswitch module! This is giving me nightmares! Please, someone, help me out here... it's quite frustrating having this awesome piece of hardware and not being able to use it (and I'm NOT reverting to Windows!!). 

Thanks,
/ Harm.

---

### Post by broekeman on 2014-02-03
Wow.... 3 weeks on and no answer at all. I'm starting to doubt the effectiveness of this so-called Ubuntu community.

And no, FYI, bumblebee still doesn't work. Even after trying loads of other options that only managed to break the system. *sigh*. 
I guess Ubuntu is still not ready for the laptop niche. It wasn't when I first tried it back in 2004, and still isn't. :/

---

