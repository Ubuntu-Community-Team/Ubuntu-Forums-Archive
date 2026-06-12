---
title: "ATI X600 256Mb PCIe"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by MeijUbuntu on 2005-10-17
Hello,

Has anyone setup an ATI X600 256Mb PCIe card.

It detects an ATI device, but the driver "ATI" or "fglrx" doesn't work.
SOme errors about GLCore.

If i select the driver "VESA" it works (not a pretty face ofcourse).

Anyone any ideas and suggestions ?

---

### Post by MeijUbuntu on 2005-10-18
News update.

I have created a new xorg.conf using the online fglrxconfig.
After that the fglrx driver seems to work.

The problem has something to do with the GLcore lib (?). In the new generated xorg.conf the GLcore lib is not included.

When i type fglrxinfo there is a error about DR and GL, but show some info.

More info later !

---

### Post by onesandzeroz on 2007-10-03
Hi
If you could could please share info on how you got your ATI x600 working that would be great.
I also have this video card and iam having issues getting to work. i need 3d graphics :)

much appreciated

---

