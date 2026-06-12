---
title: "Help switching to vesa mode!"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by juniorsonny on 2007-11-24
I 'm using have a Geforce fx 5200 pci card.  I'm trying to get into vesa mode and do a complete purge of any other driver and then reinstall my nvidia drivers.  How do you get into vesa mode and also what is the best way to purge all the other divers?  I know my card is one of the ones that is giving people trouble.  Right now I am running my mesa drivers just to be able to keep from crashing when it goes to sleep. Also, at times using the nvidia drivers I notice the swap file is at 90
% usage and my cpu usage is just as high.  Any help would be appreciated.

---

### Post by Yellow Pasque on 2007-11-24
I think the best way to purge drivers would be to boot into a terminal (recovery mode). Hit 'Esc' after the computer posts and goes to the GRUB screen. Choose recovery mode.

Uninstall the packages with 'dpkg -P' or use 'aptitude' to look for packages with "nv" in the  name.
I'm guessing you have the proprietary nvidia drivers installed?

EDIT: To install aptitude
```
sudo apt-get install aptitude
```

---

