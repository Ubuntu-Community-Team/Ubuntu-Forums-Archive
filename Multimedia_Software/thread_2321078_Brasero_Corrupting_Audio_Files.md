---
title: "Brasero Corrupting Audio Files"
date: 2016-04-20
forum: Multimedia Software
---

### Post by spode2 on 2016-04-20
If I copy an HDCD using Brasero, the HDCD information remains intact.

If I rip an HDCD, the ripped files retain the HDCD information.

If I create a CD in Brasero using the ripped files, the HDCD information is removed.

This indicates that Brasero does not put a bit-perfect copy of the files onto the CD, even though normalisation is off.

Can anyone suggest what is causing this corruption, please?

---

### Post by yoshii on 2016-04-21
I'm not sure about Brasero, but if you have Wine installed, you might have some luck using ImgBurn or InfraRecorder.  One or both of them has a portable (installerless) version.  They are both freeware.  Try the 32-bit versions.  If you don't want to use Wine, you might have luck with Linux freeware "K3B" for audio ripping.  But unfortunately, I think something is wrong with the recent version of K3B because it fails on Data disc burns for me where Brasero works just fine.  And yet in the past, Brasero seemed buggy instead, but lately it's been working OK for me for Data discs.  

I don't usually rip audio discs and I don't use HDCD's so sorry I can't be more helpful.  

ImgBurn might be hard to configure, but I think it has a lot of support.  It might be worth a try.  Just be sure to point the CD/DVD-RW drive letter to the correct "cdrom" path of your linux filesystem using Wine Configuration (winecfg).  Sorry I can't be more specific.

---

