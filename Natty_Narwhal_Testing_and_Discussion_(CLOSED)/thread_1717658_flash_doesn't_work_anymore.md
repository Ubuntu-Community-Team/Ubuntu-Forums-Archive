---
title: "flash doesn't work anymore"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ngsupb on 2011-03-30
It seems after upgrading packages on 29.03 flash in firefox doesn't work anymore 

Tried to reinstall flashplugin-installer but get the error:

nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so

Any ideas what is wrong?

---

### Post by go7Ul1ai on 2011-03-30
> **ngsupb said:**
> It seems after upgrading packages on 29.03 flash in firefox doesn't work anymore 

Tried to reinstall flashplugin-installer but get the error:

nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so

Any ideas what is wrong?

Heh, I thought it was just me..

---

### Post by rburkartjo on 2011-03-30
try installing this ff addon. it worked for me
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by MadCow108 on 2011-03-30
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/745459](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/745459)

luckily the abomination that is ia32libs will soon be gone :D
[https://lists.ubuntu.com/archives/ubuntu-devel/2011-March/032750.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-March/032750.html)

---

### Post by 5149.5 on 2011-03-30
+1 on the flashaid addon. It should fix your flash issues.

---

### Post by MadCow108 on 2011-03-30
should be fixed on next update:
[https://launchpad.net/ubuntu/+source/ia32-libs/20090808ubuntu11](https://launchpad.net/ubuntu/+source/ia32-libs/20090808ubuntu11)

buts its now a 60mb package :(
version 9 was only 30 mb

---

### Post by ngsupb on 2011-03-30
it is fixed in the new version ia32. Almost happy now :D (waiting for the compiz crash fix too)

---

### Post by Kelvari on 2011-03-31
I've been trying to run Flash in Firefox on Natty for some time (both 32- and 64-bit) and it still ends up lagging out quite heavily while doing flash gaming. Video sites (ex: YouTube) work just fine, but for gaming it's borderline useless. Whenever I try playing [Zuma Blitz]("http://apps.facebook.com/zumablitz") on Facebook, I get at least a 3-second lag between the time that I fire one shot and the time I can even see what my next color is to shoot. By then, any speed bonus that I had earned up (which is almost essential to getting a good score) is completely gone.

I've tried using FlashAid for both 32- and 64-bit, and that did not help at all.

If it helps any, hardware is as follows:
AMD Athlon 64X2 3800+ @ 2.4 GHz
2 GB DDR-400 (512 MB x4)
nVidia GeForce 7600 GT KO

---

### Post by Kelvari on 2011-03-31
Tried some further testing, and it seems to be primarily an issue with Firefox. With Rekonq, flash works mostly fine.

---

### Post by FreeTheBee on 2011-04-01
I just fixed my flash problems with flash aid. After installing flash without hardware support things work again.

I had problems before, which were solved by disabling hardware support. But, for some reason I could no longer get to flash settings to turn it off in the installed version.

---

