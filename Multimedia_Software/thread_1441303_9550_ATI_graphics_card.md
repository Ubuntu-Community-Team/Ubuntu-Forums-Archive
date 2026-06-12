---
title: "9550 ATI graphics card"
date: 2010-03-28
forum: Multimedia Software
---

### Post by akonchat on 2010-03-28
Using Ubuntu 9.10
I installed Ubuntu onto a second hard drive and everything seems to work fine except for the fact that I cannot install the driver (it says not supported or something) when I downloaded it from the website. I downloaded the driver made for Linux. The driver manager claims "no proprietary drivers." At the moment it shows to be using integrated graphics, but I need the full hardware graphics to play games. The open source alternate driver didn't work either. Please help! ](*,)
 Envy NG sees it but it says not compatible and not recommended

---

### Post by ShadowTek on 2010-03-28
That's an old one.
[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Radeon_R300_.289xxx.2C_X10xx.29_series](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Radeon_R300_.289xxx.2C_X10xx.29_series)

ATI's driver's for older cards are outdated and don't work the latest Xorg. I think you'd have to revert back to Hardy to have something that they would work with, but I'm not certain exactly which last distro worked with them.

---

### Post by Mark Phelps on 2010-03-29
ShadowTek is right.  AMD/ATI dropped Linux support for your card nearly a year ago.  

Ubuntu versions since 9.x are NOT going to be able to use the older ATI driver, and the newer ATI driver versions will no longer work with your card.

Unless you regress back to Hardy, there is no way you're going to get the 3D acceleration you need to play games.

And, don't try to force a driver installation.  All that will do is trash your display and you end up having to boot into the console to remove the drivers and replace them with the ones you already have.

---

