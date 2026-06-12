---
title: "Unable to access any DVD (blank, data ..), ubuntu 9.04"
date: 2010-03-23
forum: Multimedia Software
---

### Post by chang5562 on 2010-03-23
I have a Dell E5500 with Internal CD writer/DVD-rom, (product: CDRW/DVD GCCT20N, vendor: HL-DL-ST) with Ubuntu 9.04.  I only could read CD on this device (blank or data), but could not read any DVD (data or blank).  Pop in any DVD, there was no icon shown on the desktop, no record in "mount", under the "dmesg | tail" - Buffer I/O error on device sr0.
I have installed libdvdread4 and totem package and latest ubuntu-restricted-extras, still nothing was shown.  my fstab of this item as 
/dev/scd0      /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0 0
I tried to play with the fstab by modify above to different format, sr0, cdrom... none of them worked.
I spent almost 2 weeks on this issue, no result.  Does anyone have more suggestion how can it access DVD? 
I have tried a brand new Ubuntu 9.04 installed, the same thing.
Also tried on my other Dell E5500 machine with same ubuntu and same internal CDRW/DVD reader, same problem.
I just want to access a data DVD, not watching any video DVD.

---

