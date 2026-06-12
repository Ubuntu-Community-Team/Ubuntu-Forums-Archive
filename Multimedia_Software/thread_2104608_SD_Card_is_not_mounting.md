---
title: "SD Card is not mounting"
date: 2013-01-13
forum: Multimedia Software
---

### Post by lferg on 2013-01-13
I'm posting this here as I assume multimedia relates to SD cards and the mp3's I am trying to retrieve. When I insert my card, which is coming out of my Galaxy Note II (works perfect in Windows) I get the following error: **Error mounting /dev/sdb1 at /media/niviah/2E9A-3192: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/niviah/2E9A-3192"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat' **  Any thoughts?

---

### Post by dabl on 2013-01-13
Yes. Short answer -- I think you're screwed: [http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

This may or may not help you cope: [http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm](http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm)

---

### Post by lferg on 2013-01-13
> **dabl said:**
> Yes. Short answer -- I think you're screwed: [http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

This may or may not help you cope: [http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm](http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm)


Note: The PPA is supported from Lucid (10.04) to Precise (12.04). It is not supported in Quantal (12.10) yet.

:(

---

### Post by dabl on 2013-01-14
The package in the 12.04 repo may or may not work correctly when installed on your 12.10 system.  At your own risk, you could set up the 12.04 PPA in /etc/apt/sources.list.d/ and install the package.  There is a very small chance that this experiment could totally trash your system.  There is a larger chance that it won't find needed dependencies and will fail to install.  And of course there is a chance that it will appear to install, but fail to function.

On the other hand, it could work.

---

### Post by lferg on 2013-01-14
It looked like it installed.  But it either doesn't work or did not install. Thanks for the direction.  Linux is proving to have a serious learning curve.

---

### Post by 0v3r on 2013-02-10
Hi guys i`m quite new here.i manage to read an exfat usb hd in ubuntu 12.10 simply following the steps described here 

[http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm](http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm)

you don`t even have to mount the disk from a terminal :)

hope this help

---

