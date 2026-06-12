---
title: "Where are we re: Blu-Ray support?"
date: 2010-06-10
forum: Multimedia Software
---

### Post by sbalfour on 2010-06-10
I'm on Kubuntu 10.04, KDE 4.4.4 with K3b 1.92.0 RC3-2 plus a handful of patches from 
sourceforge development branches, plus a couple of my own fixes, i.e. beyond bleeding edge.  BDR disks are recognized and written to, but there's an I/O error upon close,
and most of the files written are corrupt.  BD-RE is not recognized, and dual-layer
BDR disks are recognized only as single-layer.  None of my commercial BD-ROMs
will play, even with contortions necessary to decrypt them.  I could read/write and 
play Blu-ray disks on windows since the early days of Vista.  I can even play them on 
XP, with upgraded drivers.

It appears to me that Blu-ray support was not in development until K3b 1.69, though
some data structure was there before that (1.68 is the latest version on 9.10).  The
situation is still grim:  you need Kubuntu 10.04 plus KDE 4.4.4 plus beyond-bleeding-edge
(you build and patch it) K3b to have any hope of getting anything to work re Blu-ray.  
You'll need a complete development environment installed to do it, enhanced with
25 KDE development environment libraries I never had to install before.  1.92 
appears to be a sort of pre-release 2.0, because it's more than a bug-fix upgrade
from 1.91.  1.92 is a long way from repository stability and compatibility, probably
Kubuntu 10.10 timeframe.   Maybe somebody on the development team can post
a sticky (somewhat sticky, until Blu-ray is fully supported) as to where we are.

So, can anybody get plug-n-play Blu-ray anything to work?  This might be the juncture where I join the development team, because we're a leg down here.

                                                                             Stuart

---

### Post by 67GTA on 2010-06-10
I was asking myself the same question a couple of weeks ago. The only "official" thing I could find was here: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD  ]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")It seems it is a pain to implement, and is still 50/50 afterwards. Blu-Ray seems to be one of those restricted formats that someone smarter than me will have to work around like dvd css protection. Sony intentionally encrypts the contents to prevent pirating.

---

### Post by PC_load_letter on 2010-06-15
Here is another guide: [http://wiki.flexion.org/BluRayRipping.html](http://wiki.flexion.org/BluRayRipping.html)

I'm also interested in knowing what is the status quo of the Linux support of the Blu ray discs. Are there any plans by Canonical to provide out-of-the-box support to blu ray?

---

