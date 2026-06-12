---
title: "nVidia 8800 GS Support Broken"
date: 2008-06-20
forum: Multimedia Software
---

### Post by jonnyrockets on 2008-06-20
Hey Everyone, 

I was excited to try 8.04 with an nVidia card, but it seems the proprietary binary driver from nVidia doesn't work with the 8800 GS. 

To be more specific, i have an XFX 8800 GS, 384MB ram. Ubuntu Hardy can boot with it, and give me the full resolution of 1280x1024 that my monitor supports, but when I go to the Hardware Drivers module, and enable the nVidia driver, X doesn't start properly. 

I can't even make it to the login screen with the nVidia driver enabled. I can start hardy in the troubleshooting mode/ safe mode, and select the option to fix X, which I'm guessing re-writes the xorg.conf. This of course causes the normal (non proprietary) video driver to be used. 

Does anyone know the version of the proprietary driver that ubuntu hardy is utilizing? 

After a quick visit to the nVidia website, they list 8800GS support for the linux driver released on June 11th. Are we that up to date?

Does anyone have suggestions as to how to get this working? :confused:


thanks in advance! rock on. :guitar:

---

### Post by IbnKuldun on 2008-06-20
If you want to install the latest drivers, have a look at this thread. 

[http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

### Post by jonnyrockets on 2008-06-23
Tried installing the newest binary drivers.... still no luck :(

After running dmesg, it shows a segmentation fault at the end for xorg. Something still isn't right here. 

I'll post the exact error code later..

---

### Post by man_bash on 2008-06-23
Helloa
I have an identical problem as you (slightly different video card - EVGA 8800 GT). I have narrowed down the problem as to the binary driver attempting to use an older kernel interface, so the driver is version 169.12 but it tries to use the 76.xx.xx kernel interface. 
Pakage nvidia-new-kernel-source has the same version, so compiling and installing the package should fix the problem. I am new to linux and I am at a loss as to how to actually accomplish the building and installing the source. I tried # sudo apt-get -b source nvidia-new-kernel-source, but that has failed - got the 
line from debian's wiki.

---

### Post by jonnyrockets on 2008-06-23
try the new binary driver from nvidia's site. if you follow the link that other guy posted, it brings you to a driver that is newer than the one you have mentioned. 

the driver in the ubuntu repository is not very up to date for the nvidia binaries. 

hope yours works out! i would hope yours is up-to-date, the 8800GS is a relatively newer card, yours has been around for a bit and should definitely be working..

---

### Post by jonnyrockets on 2008-06-23
im going to try to update via envy tonight. 

hopefully that works, if not i'll post the seg fault errors i kept seeing.

---

