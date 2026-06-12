---
title: "SiS AC'97 integrated soundcard suddenly not detected"
date: 2008-08-14
forum: Multimedia Software
---

### Post by tux_attack on 2008-08-14
I lost sound about 5 days ago. After I put my computer to sleep, when I brought it back up the mixer icon had changed to the mute symbol and clicking on it yielded this message:

"No volume control GStreamer plugins and/or devices found."

lspci output with sound card in bold
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
** 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)**
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:08.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```When I run "aplay -l" it says it can't find any sound cards. I have tried the stickied sound guide and reinstalled alsa too. 

It has run perfectly under my fresh gutsy install for a  while now and my current kernel is the same one that is used under my other install on the same computer (upgraded from feisty->gutsy->hardy).

any ideas?

---

### Post by tux_attack on 2008-08-19
bump.

---

### Post by Super TWiT on 2008-08-19
Have you tried the sound card in another operating system or livecd to make sure that the sound card is okay?  Maybe it still shows up, but part of it isn't working right. I have an AC'97 card, but it is from Intel and it is working.  I think the same drivers are used.

---

### Post by tux_attack on 2008-08-24
Yup, you're right. I just wanted to believe it was the software not the hardware but I tested in knoppix and my old install and they couldn't detect it. The soundcard is fried. I'll add this to my list of reasons to build a new computer soon :-) 

And Leo Laporte definetly rocks!

       Thanks!

---

