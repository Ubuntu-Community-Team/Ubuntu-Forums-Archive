---
title: "Matrox G450 Dual head"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by wearekosh on 2007-03-02
Does anyone know how to install a Matrox G450 video card so it works in dual head mode?

I had a look around and found the Matrox drivers.
And of course the install.sh does not work
so i looked at doing a manual install.......
The instruction says to install the driver ("mga_drv.o") and the HAL library ("mga_hal_drv.o") in "/usr/X11R6/lib/modules/drivers".
But i don't seem to have this directory 'modules' so where would i put them?? (the install instructions are based on Red Hat Linux 9.0.)
It also says i need A working installation of XFree86 4.3.0, and X.org versions 6.7.0, 6.8.0, 6.8.1, 6.8.2, 6.9.0, 7.0.0 is required before the binaries can be installed.
How can i tell what version of Xfree86 ans X.org i have installed??

I have just installed the latest ubuntu 6.10 edgy eft

Also Matrox seems to have a different copy of "mga_drv.o" and "mga_hal_drv.o" for each version of xfree86 and x.org ??

It would be nice to know which to use and where to put it??

Not to mention that along side the copies of "mga_drv.o" and "mga_hal_drv.o" there are "mga_drv.so" and "mga_hal_drv.so"

and the last question ---:) 
I think i have the correct modification to add to the Xconfig file for the G450 card - but can someone tell me where to find the Xconfig file :) 

thanks

---

### Post by wearekosh on 2007-03-03
Just to let you know this problem of mine has been solved by DEATHSHADOW in the "Hardware & Laptop" forum 

If you have the same issue with a G450, look there for the solution.

---

### Post by pneaveill on 2007-03-22
Any chance on putting a direct link to that posting for us?  This is the problem of double posting -- it sets up "honey-pots" against people needing help.

Thanks in advance

----------------------------

Never mind, I did myself:

[http://ubuntuforums.org/showthread.php?t=374611](http://ubuntuforums.org/showthread.php?t=374611)

---

