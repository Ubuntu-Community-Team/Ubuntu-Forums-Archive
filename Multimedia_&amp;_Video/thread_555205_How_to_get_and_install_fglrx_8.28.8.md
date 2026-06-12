---
title: "How to get and install fglrx 8.28.8"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by DarkDead on 2007-09-19
Hi. I've got a Sapphire ATI Radeon 9200SE and I've been trying to install the drivers for it.
After installing the most recent version of xorg-driver-fglrx: 7.1.0-8.34.8 I realised that they don't support my card. So I tried to install the 8.28.8 driver (the one that appears when I choose the 9200 series on the ATi site) manually but due to some errors I couldn't. Then I saw that the linux-restricted-modules package on Edgy includes the fglrx module from the 8.28.8 driver version.
I searched a bit but I didn't find any way to download this version. Does anyone can get this version? And does it work with Fiesty?

Thanks in advance.

---

### Post by w4ett on 2007-09-20
In Ubuntu, only the 9500 series and above cards are supported by the fglrx driver. See:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This is due to ATI's neglect for their "legacy' cards.

The correct driver for your card is the xorg-driver-ati.

---

### Post by Bluejacket on 2007-09-20
I have 3d acceleration working with Radeon 9200 using xorg-driver-fglrx version 7.0.0-8.25.18 on Kubuntu 6.06.

---

### Post by w4ett on 2007-09-20
> **Bluejacket said:**
> I have 3d acceleration working with Radeon 9200 using xorg-driver-fglrx version 7.0.0-8.25.18 on Kubuntu 6.06.

From Edgy on, fglrx will not work for that card......due to xorg incompatibilities.....ATI has not ported/modified their legacy driver to be usable.  (I use a 9200SE too)

---

### Post by DarkDead on 2007-09-20
Thank you for the information w4ett. Even compiling the drivers supplied by ATI won't work?
Is it possible to get hardware-accelerated 3D with the xorg-driver-ati drivers?

---

### Post by w4ett on 2007-09-20
well...the xorg-driver ati gives me a framerate of 800-900 fps, while not sufficient for gaming, I can run google earth quite well, and compiz fusion too.

---

