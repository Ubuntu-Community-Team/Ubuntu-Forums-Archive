---
title: "Having Problems with the latest Nvidia Beta Driver? Read This"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by Beamerboy on 2007-06-04
Hi,

I just found a fix for this.  there is a problem with the NVidia.Com installer in that it doesn't update the module dependencies.  To fix this problem boot your machine and let xorg fail then hit ALT+CTRL+F1

Login using your username and password the type the follow:

sudo depmod -a

then type sudo reboot

This should fix your problems but if it doesn't you need to do the following:

sudo nano /etc/default/linux-restricted-modules-common

add the following line

DISABLED_MODULES="nv"

press CTRL+X and save the file.

Reboot.

Everything should now work.

Paladine
[Edit] Thanks to ROAF for the fix

---

### Post by Beamerboy on 2007-06-04
The following post should solve your problems if you are getting an API mismatch or failure to load the new nvidia module after rebooting:

[http://ubuntuforums.org/showthread.php?p=2777440#post2777440](http://ubuntuforums.org/showthread.php?p=2777440#post2777440)

Paladine

---

### Post by dannyboy79 on 2007-06-06
very well put!!!!!

---

