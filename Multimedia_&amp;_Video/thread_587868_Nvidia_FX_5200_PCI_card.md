---
title: "Nvidia FX 5200 PCI card"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by 1/0 on 2007-10-23
I have a problem with one of my computers. Its an P4 Celeron 2,4 GHz with a QDI BA1/GV mother board. I'm trying to get the Nvidia PCI card to work but it seems to interfere with the onboard Intel one (note PCI not PCI-e). 

```
lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
01:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

I just can't boot properly with the nVidia card. I've tried different settings in BIOS, s.a. onboard graphics card disabled (PCI instead). Depending on the settings I get one of the following two error codes:

```
work_notifysig+0x13/0x25

error_code+0x6a/0x70
```

I've tried Kubuntu 7.04 and now 7.10. Now, in Gutsy, I've tried just turning on the restricted devices as recommended and double checked the xorg settings. Advice, solutions, pointers etc. are very welcome!

---

### Post by 1/0 on 2007-10-25
Bump

---

### Post by sanddgroper on 2007-10-26
Is it a PCI card or an AGP card.I thought the FX5200 was an
AGP card.
Also the fact that lspci sees two graphics cards is probably
not helping.I know it is a long time since they were used but you
dont need to change any onboard jumpers to disable the onboard
graphics card.
Not much help I know.

Cheers
Sandy

---

### Post by 1/0 on 2007-10-26
Yes, its a PCI card. Somehow QDI decided, lets build a mother board with PCI slots only and my girlfriend got a computer with it... The card used to work fine in Win32 so its not broke. I just can't seem to get it working,

---

### Post by sanddgroper on 2007-10-26
Ok once again all I can suggest is to check if there are onboard
jumpers to disable the onboard graphics.
You might want to check the motherboard out by googling its
specifications on the net.
Finally you might like to try moving it to another slot on the
motherboard as the slot it is in might be sharing an irq with
the onboard card.
After that I am all out of ideas.

Cheers
Sandy

---

