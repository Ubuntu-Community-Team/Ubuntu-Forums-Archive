---
title: "Radeon HD8870M / Intel Haswell produces green display"
date: 2014-11-11
forum: Multimedia Software
---

### Post by paul-fayoux on 2014-11-11
I have the same problem , still with Dell Inspiron 17R (with cards radeon HD8870M and Intel). 

I tried each time installing OS in dual boot with windows 8 with efi boot (I don't have any problems to boot).

Apparently this problem not only occur with ubuntu (I only tried version 14.04 and 14.10) , but also with Fedora 20, Mint 17 and with Kali 1.0.9a . I tried each drivers for the amd cards (fglrx , fglrx-update and xorg) , I downloaded the last version of amdcccle and tried it too without any result even if the amdcccle was apparently working. 
I can only had two things more about this problem , I can have the same screen problems on windows if I set the screen refresh rate from 60hz to 40hz (It's not only looking quite the same it's exaclty the same bug). I tried to fixe it with xrandr , but the refreshing rate is already set to 60hz , I even tried to add mode for xrandr with higher refreshing rate and it didn't change nothing (it change nothing too when I change the rate to 40hz), like xrandr cannot change the refreshing rate. 

I saw another thing , it's that the shortcut for brightness setting are recognized by the OS (the little sun with brightness bar appear on screen) but brightness cannot be modified.

One last things when I tried with nomodeset the screen rate appear to be 76hz and color are normal (I only tried that on mint and ubuntu), if I choose intel rather than radeon HD8870M only the screen size change but the color are good and screen refreshing rate up to 76hz.

Ok sorry I saw later that everything was already known , so apparently it's a kernel compatibility problem ...

---

### Post by QIII on 2014-11-11
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2207882](http://ubuntuforums.org/showthread.php?t=2207882)

The original thread described problems with Ubuntu 13.10, which is past its EOL (End Of Life) and which you apparently are not using.

Better a new thread than a post buried in an old thread about an unsupported release.

Cheers!

---

