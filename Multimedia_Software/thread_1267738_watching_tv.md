---
title: "watching tv"
date: 2009-09-16
forum: Multimedia Software
---

### Post by adrianmak on 2009-09-16
I have a COMPRO VideoMate TV Gold Plus II M505 analog tv card.


can it be used on linux ?

I installed on a pci slot and install tvtime software
but tvtime cannot find a /dev/video0 device

I checked tvtime's web site , this software is support SAA7134 chipset which is used by M505.

---

### Post by lovinglinux on 2009-09-16
I guess you can use that card, since it has saa7134 chipset, which is supported.

The problem is that the TV card is not properly detected or the necessary driver/module is not loaded automatically. I don't understand that very well, but I know you have to edit some configuration files to make the card properly available after boot.

Check how I did that at [http://ubuntuforums.org/showpost.php?p=5971890&postcount=2](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2)

Keep in mind that the numbers in red on that post will not be the same for your graphics card. The link to find the specific numbers for your card is broken, so you might need to Google for it.

---

