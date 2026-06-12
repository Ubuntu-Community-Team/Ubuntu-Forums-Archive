---
title: "slow Radeon 3200 on AMD64x2, ubuntu 9.04"
date: 2009-05-23
forum: Multimedia Software
---

### Post by alex009 on 2009-05-23
Hi,

I have recently installed 9.04 (64bit) on AMD64x2 with ATI Radeon HD 3200 card and noticed that graphics is very slow. Even simple tasks as dragging a window from side to side look very choppy. The glxgears report about 900-1000fps, which i think is too low for this card. 
I tried installing the drivers from AMD (by downloading directly from AMD), but that didn't change much. 

Could anyone please shed a light or point to a guide on how-to improve radeon's performance?

Thanks,
Alex

---

### Post by bworg on 2009-05-24
unfortunately, the ati drivers for linux suck. i'm having the same problems after upgrading to jaunty: slow 2d performance, and flickering screen. so i'm thinking of going back to 8.10, which is a pity....

---

### Post by acosta68 on 2009-05-24
Hello: I have the same problem, some idea ?

Thanks !
):P

---

### Post by alex009 on 2009-05-27
Just wanted to add that removing the proprietary driver (catalyst) by running an fglrx-uninstall.sh script that came with the driver broke X. The X window stopped working completely, freezing the computer at login prompt.  

Restoring the original xorg.conf or running "dpkg-reconfigure xserver-xorg" to reconfigure the X window didn't work and the only way to get X running was to reinstall the catalyst driver again. 

What would be the correct way of uninstalling the damn ati driver?

Thanks,
AL

---

### Post by hmc123 on 2009-05-29
I had similar problem and my screen went black when using the ati driver. 
I'm not sure what the fglrx-uninstall.sh script does, but I managed to uninstall the fglrx package altogether. There are 3 packages for the fglrx, you can use 

dpkg -l | grep 'fglrx'

to find them. Then, try to remove each package using dpkg -r <each package> . Do the dpkg-reconfigure -phigh xserver-xorg again to reset the xorg.conf at /etc/X11. Reboot the system and hopefully everything works. Mine is working fine now without the ati driver.

Good luck!

---

### Post by Alka-Seltzer PLUS on 2009-06-02
what's about me ???
this is my output for " dpkg -l | grep 'fglrx' ":

ii  fglrx-modaliases                           2:8.600-0ubuntu2                     Identifiers supported by the ATI graphics dr

---

### Post by Melcar on 2009-06-02
> **alex009 said:**
> Just wanted to add that removing the proprietary driver (catalyst) by running an fglrx-uninstall.sh script that came with the driver broke X. The X window stopped working completely, freezing the computer at login prompt.  

Restoring the original xorg.conf or running "dpkg-reconfigure xserver-xorg" to reconfigure the X window didn't work and the only way to get X running was to reinstall the catalyst driver again. 

What would be the correct way of uninstalling the damn ati driver?

Thanks,
AL

If you installed the drivers with the ATI installer, that is the correct way.  You just have to remember to configure xorg.conf correctly to load the open source driver, because for some reason it does not load by default with Jaunty.  If you don't specify what driver to load in xorg.conf, X will simply crash next time you attempt to log in.

---

