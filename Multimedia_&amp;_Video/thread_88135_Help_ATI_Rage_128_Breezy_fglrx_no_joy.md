---
title: "Help ATI Rage 128 Breezy fglrx no joy"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by Neobuntu on 2005-11-09
Following all directions including the reinstall of restricted stuff for my K7 it will not startx when set to fglrx.

I'm not finding serchable help.

It worked in MEPIS to my surprise and I have played TORCS on it. Now this is Breezy and a different motherboard with no DRI (direct 3D). 

Has anyone had success with breezy and rage 128 dri?

UPDATE(late): I got this to work and you might search the newer thread as to the details. This did give me the limited Rage 128 3D benefits.

---

### Post by az on 2005-11-09
Some have had success with dri snapshots of the rage128 xorg driver.

Install build-essential gcc-3.4 and get these:
[http://dri.freedesktop.org/snapshots/common-20051107-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20051107-linux.i386.tar.bz2)
[http://dri.freedesktop.org/snapshots/rage128-20051107-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/rage128-20051107-linux.i386.tar.bz2)

unbzip them and run the install script.

---

### Post by pascalbuz on 2005-11-28
I tried a lot of things to have 3d on my 123 rage pro. But nothing seems to work.

I tried to install dri with  azz post but here is an error at the end:
[HTML]rage128-20051107-linux.i386$ sudo ./install.sh 

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver:

Driver Name    : rage128
Description    : ATI Rage 128 (Pro) Driver
Architecture   :
Build Date     : 20051107
Kernel Module  : r128

Optional Information

Driver Version      :
Special Description :

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will need to copy the DRI XFree86 driver modules to
your XFree86 directory.

The script will use the following XFree86 directory:

 /usr/X11R6

If this is correct press ENTER, press C to change or CTRL-C to exit.


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.12-10-686
Module Directory : /lib/modules/2.6.12-10-686

If this is correct press ENTER, press C to change or CTRL-C to exit.

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
[/HTML]

This is the dri log file:
Makefile:166: *** Cannot find a kernel config file. Arrêt.

I updated the kernel module but it doesn't work.

Someone has an idea?

Thanks

---

### Post by Ubuntu Warrior on 2005-12-04
I also tried the stuff azz recommended with no joy. Seems to be complaining about x.org. Looks like the drivers will only work with XFree86???

Still no joy getting my ATI AIW Pro card to handle TV!!!

---

### Post by ranf on 2005-12-04
[QUOTE=pascalbuz]I tried a lot of things to have 3d on my 123 rage pro. But nothing seems to work.

I tried to install dri with  azz post but here is an error at the end:
This is the dri log file:
Makefile:166: *** Cannot find a kernel config file. Arrêt.

I updated the kernel module but it doesn't work.

Someone has an idea?
[/QUOTE]
Search the "Customization Tips & Tricks" section for "savage".

---

