---
title: "ATI Radeon X300 not using full memory?"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by kook44 on 2006-09-23
Hi-
I have an ATI Radeon X300.  It is 128MB card, but when I open the ATI control panel, it says: "Memory Size: 32MByte".  I obvioulsy want to get the most I can out of this card.  Anyone know how to adjust this?

thx

---

### Post by lha on 2006-09-24
Execute
```
sudo dpkg-reconfigure xserver-xorg
```
It will let you reconfigure X.org. If memory serves, it will ask how much memory your graphics card has.

---

### Post by kook44 on 2006-09-26
Hmmm, I tried that and I could not start Gnome.  The screen would just go black and I couldn't do anything.  I booted into recovery mode and diff'ed the two xorg.conf files (the new one and the backup that dpkg-reconfigure created).  It simply added the line for VideoRam.  Seems that no matter what value I place in that setting, I cannot start gnome

---

