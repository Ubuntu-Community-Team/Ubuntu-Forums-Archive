---
title: "[SiS] Sound Card Drivers?"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by MenZa on 2007-08-20
Hey everyone, I'm having some problems with my sound card, which appears to be installed, but I am unable to get any sound output from either the speakers of my laptop or any external input. The card in question is a "Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)", according to my lspci:

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
**00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)**
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
00:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
00:09.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
00:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


```

This is the default sound card of my Packard Bell EasyNote J2701 from last year (I assume so; it has the new Intel logo on it). It seems like a pretty generic device, so I don't see why there should be any problem finding it anywhere.

What's weird, is that both the GNOME and Xfce volume control applets identify a "SiS SI7012", but the sound is not there. What gives?

---

### Post by wolfen69 on 2007-08-20
see this thread [http://ubuntuforums.org/showthread.php?t=39109&highlight=ac97+sound+card](http://ubuntuforums.org/showthread.php?t=39109&highlight=ac97+sound+card) where the problem was resolved.

---

### Post by MenZa on 2007-08-20
> **wolfen69 said:**
> see this thread [http://ubuntuforums.org/showthread.php?t=39109&highlight=ac97+sound+card](http://ubuntuforums.org/showthread.php?t=39109&highlight=ac97+sound+card) where the problem was resolved.

I appreciate your effort, but the options in that thread do not coincide with the ones available to me, nor is it the same chipset (VIA vs. SiS)

---

### Post by w4ett on 2007-08-20
Ive got:

> 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

which worked out of the box in Feisty.  You might want to ask in the Gutsy development Forum.

---

