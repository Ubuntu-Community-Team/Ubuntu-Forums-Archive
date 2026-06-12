---
title: "Three Monitors with two video cards - NOT WORKING!"
date: 2010-12-10
forum: Multimedia Software
---

### Post by notoriousBIG on 2010-12-10
All

I am a total noob to ubuntu and I have a very frustrating problem. I have two video cards installed, an ATI RADEON 5700 and Matrox Millenium G450 Dual head. The ATI card has two video ports which are working perfectly. As a matter of fact, they've been working since install with the open source fglrx driver. I added the matrox after initial install and can see it with lspci:

01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
07:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)

I also have installed the open source matrox driver for xorg (xserver-xorg-video-mga). The current configuration has two monitors connected, and working, to the ATI card. The third monitor is connected to one of the ports on the matrox card and i cannot get a video signal. This has been killing me for the last couple of days. I did notice when i load the mga module in xorg.conf i see in the Xorg.0.log that it loads then unloads the module.  Anyone with suggests, tips, hints, help, etc ...I would hugely appreciate it. I love ubuntu so far but windows seems to have far superior multi monitor support.

 This has to work, I know im probably being stupid and it's something easy. unfortunately, I just don't have the experience with ubuntu.

Thanks

---

