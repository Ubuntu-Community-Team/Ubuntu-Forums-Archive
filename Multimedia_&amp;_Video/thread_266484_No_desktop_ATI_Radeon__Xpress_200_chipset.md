---
title: "No desktop ATI Radeon * Xpress 200 chipset"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by ShirishAg75 on 2006-09-27
Hi all,
       A friend of mine bought an Intel desktop board, the D101GGC  which has an ATI Radeon *Xpress 200 chipset. Hence he gets dumped on the console with X.org 6.8 giving unknown ATI chipset error. Now how should I help him. Also is this a good graphics chipset as well as is this new or an old chipset? Thnx in advance for all your responses.

---

### Post by Ragnarol on 2006-09-27
Install the ati drivers ([https://help.ubuntu.com/community/BinaryDriverHowto)](https://help.ubuntu.com/community/BinaryDriverHowto)).

If you get black screen when xwindows start after installing the drivers go to BIOS and enable card sideport+uma memory.

Also this card could have problems when DRI is enabled. There is a couple of posts in this forum talking about. The last and still life one is [http://ubuntuforums.org/showthread.php?t=250260](http://ubuntuforums.org/showthread.php?t=250260)

About the card, well, It is a new chip but I have heard that is crap, I haven't been able to make it work with DRI in my machine so I can say more.

Good luck,

---

