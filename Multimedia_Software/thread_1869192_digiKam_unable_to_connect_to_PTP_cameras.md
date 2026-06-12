---
title: "digiKam unable to connect to PTP cameras"
date: 2011-10-25
forum: Multimedia Software
---

### Post by CryptoPaul on 2011-10-25
It seems at the moment that digiKam is unable to connect to PTP cameras.

The error message seen when started from a terminal is "digikam(nnnn)/digikam (core): Failed to detect camera with GPhoto2 from Solid information"

The current version in the repository, DigiKam Version 2.1.1-0ubuntu1 (Build date: Sep 23 2011), has been compiled with gphoto2 support disabled because it causes a DSO build failure.

If I'm reading this bug report ([https://bugs.kde.org/show_bug.cgi?id=268267](https://bugs.kde.org/show_bug.cgi?id=268267)) correctly, the developers of digiKam are waiting an upstream fix.

I'm running 64bit Kubuntu/KDE, however, I believe this affects all variants, but open to correction there.

---

### Post by biji on 2011-11-19
too bad... my camera only support PTP mode

---

### Post by CryptoPaul on 2011-11-23
Philip Johnsson (very active on the digiKam mailing list, I would regard his ppa as 'trusted') has digiKam version 2.3.0 this has a fix for the problem.

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

---

### Post by biji on 2011-11-23
thanks

---

