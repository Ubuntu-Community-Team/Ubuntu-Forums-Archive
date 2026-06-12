---
title: "ATI Radeon X 1950 pro fx display driver on 12.04 Precise"
date: 2013-04-03
forum: Multimedia Software
---

### Post by Elsias79 on 2013-04-03
I am currently using unbuntu 12.04 and am at a complete lost as to understand how to install these proprietary driver of my video card. ive followed instruction for AMD driver but the one provided by the site does not support precise... help please....

---

### Post by mJayk on 2013-04-04
In my exp. DON'T use the one from the site,  go to software center -> edit -> software sources -> additional drivers

---

### Post by QIII on 2013-04-04
Hello and welcome to the forums!

The X1950 is in a legacy driver branch for Linux.  Unfortunately, that driver will not work with any X Server version since late 2008/early 2009.  Don't even try to install it.

If you attempt to install the driver from additional drivers, you will be greeted with a message that you do not have a recognized card.

The Windows driver is also considered "Legacy", but because Windows does not use anything like X Server, the legacy driver will work.

The default open source Radeon driver installed with Ubuntu should fulfill the needs of the vast majority of users.

Regards,


QIII

---

