---
title: "Mobility Radeon HD4200 3D issue"
date: 2012-01-14
forum: Multimedia Software
---

### Post by sschevy010 on 2012-01-14
I have been searching all over forums, I came across this [http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748) and still no go with 3D acceleration, I even did the Hardware Driver.. where it assigns a propiet driver.. no good. changed settings.. no good. All i can get is 2D, and this is a 3D Graphic accelerator as well. Works great in Windows of course but nothing in any Distros including this one.. the Ubuntu I now have installed is 10.04 Lucid x64.

Anyone help with this please? This is on a Laptop - NV53 Series Gateway with Mobility Radeon HD 4200

Thanks!

Shawn

---

### Post by sschevy010 on 2012-01-14
60+ Views.. man this must be unresolve problem :( which i dont understand why ATI has not made an effective driver for a 2  yr old device for Xorg 10-11..

---

### Post by sschevy010 on 2012-01-15
Any new ideas?

---

### Post by coffeecat on 2012-01-15
My Acer laptop with the Mobility Radeon HD4200 gave me 3d acceleration out of the box (at least good enough for compiz) with the default open source driver in Lucid 10.04. Did you you not get 3d before you installed the proprietary driver with the Hardware Drivers utility?

---

### Post by sschevy010 on 2012-01-15
Nope, It said it has 3D acceleration, played a few games, it wouldnt run each games in 3D and they were choppy. So i tried doing the steps in the link.. still nothing. And in Windows 7 it comes with, all 3D games works perfect.. I was even able to play StarCraft 2 on it as well as WoW, but with Ubuntu and drivers saying its enabled... or even if it says disabled, still choppy and unable to run on 3D.

---

### Post by sschevy010 on 2012-01-20
So i reinstalled ubuntu to newest version.. 11.10 AMD64.

I tried installing the post-release updates of ATI Drivers through ubuntu driver.. and gives me error that this driver failed installation check log... and i got this..

2012-01-20 03:30:36,253 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 03:30:36,253 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-20 03:30:44,833 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 03:30:44,833 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 03:30:50,742 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 03:30:50,742 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

And the other one listed just has no 3d acceleration at all.
Any ideas?

---

### Post by silverhaze06 on 2012-01-21
Try the suggestions in this thread. It made my video card work a lot better. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

### Post by sschevy010 on 2012-02-01
Now that i have freshly installed the 11.10 once again.. I have been having so much troubles trying to get it installed correctly.. reasons of doin again cause last time it didnt go well... now i came across this log in usr/share/ati  
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
./packages/Ubuntu/ati-packager.sh: 399: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
./packages/Ubuntu/ati-packager.sh: 399: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 399: debclean: not found
./packages/Ubuntu/ati-packager.sh: 399: dpkg-buildpackage: not found
[Error] Generate Package - error generating package : Ubuntu/oneiric

I have tried the steps in this... [http://ubuntuforums.org/showthread.php?t=1873072](http://ubuntuforums.org/showthread.php?t=1873072)  for which gives that error .... what is fix to this?

---

### Post by sschevy010 on 2012-02-01
Any ideas??

---

