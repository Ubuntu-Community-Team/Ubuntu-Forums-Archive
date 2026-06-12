---
title: "fglrx driver and mobility FGL v3200 ... what is going on ?"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by enryfox on 2007-12-12
I think i'm missing somthing but i don't know what: i habe an IBM t43p laptop with an ATI mobility firelLv3200 (M24GL chipset) and Ubuntu 7.10. Right now i'm using the opensource driver and everything is fine except for 3D; i'm trying to install fglrx driver both from ATI (catalyst 7.11) or ubuntu repository. In both case Xorg fails and the error is:

> (II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(EE) No devices detected.

Fatal server error:
no screens found

This clearly means that my chipset is not supported. I tried forcing the ChipID of a mobility X600 and again xorg fails but with no errors. 

The problem is, when i first installed ubuntu 7.10 and until a few weeks ago, the restricted driver worked perfectly ! what has happened ? I'm going mad ....

thanks
bye

---

