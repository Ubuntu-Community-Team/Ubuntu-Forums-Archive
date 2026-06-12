---
title: "S-video help"
date: 2010-10-07
forum: Multimedia Software
---

### Post by tbridges42 on 2010-10-07
First the setup: I have a clean install of xUbuntu 10.04 with an ATI Radeon 9000 Pro connected through VGA to a CRT monitor that will remain until I get setup, and through s-video out to a Sylvania flat panel hdtv. (I won't scrabble around back for a model number unless I have to.)

Then the problem: The tv displays a message stating "Invalid input format" and nothing else. In xUbuntu, under the 'desktop' option, it displays two display tabs, one labeled 'VGA' and the other 'S-video'. However, under 'displays' it only shows the monitor. I tried installing the ATI drivers, but alien refuses to do so, telling me "unknown tag". If I change the resolution away from 800x600 the screen goes black. After playing around in the terminal and with xrandr for a few days I gave up and reinstalled. Suggestions?

Disclaimer the first: I am a Linux n00b. This is the second time I've ever installed Linux, after the first time I failed to get my network card working and gave up without access to internet help. I am, however, an experience power user of Windows and once upon a time was a programmer in C.

Disclaimer the second: These are not my choices of hardware, in particular the graphics card. This is a proof of concept machine that, if successful, will convince my wife to let me spend money on an HTPC.

Update: The ATI site is mis-linked. Whether you click x86 or x86-64 it takes you to the 64 bit drivers. I found the right ones, converted them to .deb, and installed them. To no noticeable difference whatsoever. Am I missing something after installing the package? Shouldn't *something* change? I checked the utility that lists proprietary drivers, and it showed none.

---

