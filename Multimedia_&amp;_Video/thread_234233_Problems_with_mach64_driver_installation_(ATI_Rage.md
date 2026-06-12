---
title: "Problems with mach64 driver installation (ATI Rage Mobility)"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by fruchtschwert on 2006-08-11
Hallo everyone,

I have a Sony Vaio Laptop with a ATI Rage Mobility 8 MB graphics chip and Ubuntu Dapper running.
I tried to install the 3d accelerated dri driver as described in [this thread]("http://ubuntuforums.org/showthread.php?t=7200"). I'm already a little bit into Linux but I often encounter new problems, which are mostly not very serious.

According to this I have a problem with [the tutorial]("http://ubuntuforums.org/showthread.php?t=7200")  :o 

On my box I have **kernel 2.6.15-23-386** (the default dapper kernel) running.
I installed the appropriate **kernel-headers** and the **build essentials**.
I have the **gcc 4.0** compiler. Do I need more ?
On my AMD-machine there is no need for the linux-686-package, isn't it ?

Now to the main problem. I tried installing the [dri-packages]("http://dri.freedesktop.org/wiki/"). But the installer seems not to determine the right installaltion directories.

> 
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will need to copy the DRI Xorg driver modules to
your Xorg directories.

The script will use the following Xorg directories:

Xorg Dir         : /usr/X11R6
Xorg Modules Dir : /usr/X11R6/lib/modules
Xorg Library Dir : /usr/X11R6/lib

If this is correct press ENTER, press C to change or CTRL-C to exit.

==========================================================================

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The following problems have occured:

        - Xorg module directory does not exist
        - Xorg extensions directory does not exist
        - Xorg Linux OS directory does not exist

The script can create these directories for you.

Press ENTER to continue or CTRL-C to abort.



It says that the 3 directories do not exist ...
I'm using version **common-20060403-linux.i386.tar.bz2** of the dri package.
I'm using the default Dapper xorg-installation.

**How do I determine the right paths for the installation ?**

Thanks in advance !
Greeting from Germany

fruchtschwert

---

