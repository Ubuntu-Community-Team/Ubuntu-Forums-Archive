---
title: "Everybody says NVIDIA?!"
date: 2009-04-29
forum: Multimedia Software
---

### Post by theozzlives on 2009-04-29
I should've known better, there's too many Threads about NVIDIA problems. Well now I have one. I installed my new card and it had 2 drivers, version 173 and version 96. 173 was recommended so I activated it, it downloaded the drivers and nothing. I tried 96, same thing. I tried to activate effects and it told me to enable by drivers, so I clicked enable. It told me effects can't be activated. Someone please help, here's my lspci:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```

Oh! I'm running Jaunty.

---

### Post by Kareeser on 2009-04-29
Do you want to try installing the driver directly from nvidia? :)

---

### Post by mihai.ile on 2009-04-29
GeForce FX 5200 is quite an old card so it's not a priority for nvidia, look at the mess ati has with it's drivers not that dropped support for many ati's.

I suspect that this could be due to nvidia drivers being incompatible with xserver-xorg 1.6, just like ati's drivers for older cards.

I have a newer nvidia and it works great.

---

### Post by theozzlives on 2009-04-29
> **Kareeser said:**
> Do you want to try installing the driver directly from nvidia? :)

Think it might be on the CD, if not sure.

---

### Post by Kareeser on 2009-04-29
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44)

Replace the link in that guide with this one: [http://www.nvidia.com/object/linux_display_ia32_173.14.18.html](http://www.nvidia.com/object/linux_display_ia32_173.14.18.html)

---

### Post by HappyFeet on 2009-04-29
Actually that card (GeForce 5200) is very old at this point. It is like 5 generations behind the latest. People with older ATI cards are also experiencing major problems. I can assure you that most Nvidia cards series 7000 and up are basically trouble free. Plus they are very cheap. You can get a 7300 for next to nothing that will work good.

---

### Post by lessgov2007 on 2009-04-29
I'm no expert by any means, but how old is your processor? Does it use SSE? If not maybe my thread will help you... I dunno, but check it out anyways. [http://ubuntuforums.org/showthread.php?t=1142924]("http://ubuntuforums.org/showthread.php?t=1142924")

---

### Post by theozzlives on 2009-04-29
> **lessgov2007 said:**
> I'm no expert by any means, but how old is your processor? Does it use SSE? If not maybe my thread will help you... I dunno, but check it out anyways. [http://ubuntuforums.org/showthread.php?t=1142924]("http://ubuntuforums.org/showthread.php?t=1142924")

My processor is a single core 2.63 GHz (Remanufactured Dell). NVIDIA had the driver online so I'm good now, and no I'm not a gamer.

---

### Post by Nostrud on 2009-04-29
I'm not going to be able to help you, but I could at least mention that my Nvidia Fx 5200 is running fine with the recommended 173 driver provided by default (Jaunty 9.04).

However, my problem is not getting the card/driver working, rather it's almost all 3D applications and flash consuming like 100% CPU whenever I run them. But for every day usage (office applications, Compiz etc) FX 5200 works like a charm.

So as not to hijack your thread I should probably create a new one for my problems, though.

P4 3 GHz
1,5 GB RAM
128 MB GeForce FX 5200

---

