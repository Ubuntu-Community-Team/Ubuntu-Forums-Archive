---
title: "Mythbuntu Question (image quality)"
date: 2008-12-19
forum: Mythbuntu
---

### Post by davetibbs on 2008-12-19
Hi guys

Hopefully someone can help me with this.  I have built a HTPC with a Technotrend C2300 DVB-C card and integrated nVidia 8200 graphics which works fine, but I have an issue with using Mythbuntu.

In testing Myth distros, I have tried Mythdora 5 (i386) and Mythbuntu 8.04 and 8.10 (both x64) - both setup exactly the same way (apart from cpu architecture) running both backend and frontend on same machine.

I would like to stick with Mythbuntu as I use Ubuntu on my laptop and much prefer a Debian-based system to Fedora (plus a lot of the guides on getting other MythTV aspects working e.g. lirc are mythbuntu-based).

However, I've found that the picture quality for is **noticably** better in Mythdora compared to Mythbuntu.  It's a much sharper image when viewing TV full screen in Mythdora, whereas it looks quite grainy in Mythbuntu.

I'm afraid I'm not enough of a guru to know how the two distros differ in regards to graphics drivers, both were vanilla installs, with the exception of installing of the nVidia driver (32 bit for Mythdora, and 64bit for Mythbuntu).

Does anyone have any suggestions as to why this might be, and how to rectify it?  Could it just be a difference between 32 and 64 bit (unlikely?) and therefore is it worth trying the 32bit install of Mythbuntu (despite having a 64 bit machine?)

Thanks in advance for any help you can offer.

Dave

---

### Post by jMon54 on 2008-12-19
It could be using different drivers and it could be the default playback settings may be different.  You might compare the Xorg.conf files for more clues.  I used to use MythDora and was happy with it but when I got my AMD64 system I switched over to MythBuntu and have been quite pleased with the results.  Good luck!

---

