---
title: "X11 with NVIDIA broken after update"
date: 2008-07-20
forum: Multimedia Software
---

### Post by calvert888 on 2008-07-20
So, this afternoon I upgraded to the latest version of the linux kernel headers because my Symantic had been reminding me that new updates were available for the past few days. I believe I was upgrading from 2.6.17.36 to 2.6.17.37 (though it could have been .35 to .36, I can't remember). There were a couple of other updates (I believe 1 was a Firefox update).

Anyway, I install the updates and reboot and get one of those nice big blue/grey error screens telling me that x server failed to start because it is likely not setup correctly. When I look at the log it says toward the bottom:

FATAL: Error running install command for NVIDIA
(EE) NVIDIA (0): Failed to load the NVIDIA kernel module
(EE) Screen(s) found, but none have a usable configuration
Fatal server error: no screens found

I've booted into recovery mode and tried:
-# dpkg-reconfigure xserver-xorg
 Here I've reconfigured to use nv instead of nvidia and back again
-Restoring my old xorg.conf from a backup I made just 2 days ago
-Performing various apt-get's found on here and other forums, though most were unsuccessful

I have not yet tried uninstalling/reinstalling xserver, mostly because I don't think that would fix it, but if you think I'm wrong, please feel free to correct me.

BTW, I'm still on 7.04 (I was getting ready to upgrade to 7.10 & then 8.04) and I've only been on Ubuntu a little under a year. Also, I believe I was using the restricted drivers package and I'm running a nvidia GeForce FX5700 (no jokes necessary, I know it's old).

Any ideas? 

Thanks,
Cal

---

### Post by NT4usB on 2008-07-20
Might try:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` or if you're handy in a terminal, edit your xorg.conf and change the driver to vesa. Then you can get your screen back and run the restricted drivers manager again.

---

### Post by calvert888 on 2008-07-24
That worked. Thanks!

---

### Post by NT4usB on 2008-07-24
cool...
Be sure to mark the thread solved using the thread tools above.
btw, which worked? -phigh or editing xorg?

---

