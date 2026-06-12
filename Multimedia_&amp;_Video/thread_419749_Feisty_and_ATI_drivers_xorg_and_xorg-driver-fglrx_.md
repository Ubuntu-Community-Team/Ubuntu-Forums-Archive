---
title: "Feisty and ATI drivers: xorg and xorg-driver-fglrx version mismatch"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by logg on 2007-04-23
I just upgraded to feisty and X does not work anymore (except when I use the vesa driver).

When using the fglrx driver, X reports the following error:

    [atiddxSetup] X version mismatch - detected X.org 7.2.0.0, required X.org 7.1.0.0

This seems natural when looking at the version numbers of the packages xorg-driver-fglrx and xorg:

    xorg-driver-fglrx    7.1.0-8.34.8+2
    xorg                       7.2-0ubuntu11

So do I need to wait for an update of the package xorg-driver-fglrx, downgrade xorg, or is there any other solution?

Thanks
/Anders

---

### Post by hyfans on 2007-04-23
use offical ATI fglrx driver 8.36.5. 
it claimed to support xorg7.2 and kernel 2.6.20.x.


but, as a bonus, you will not able to use Xvideo acceleration under this driver, at least , in my pc:lolflag: 


if you can, please share the steps, thx:popcorn:

---

### Post by logg on 2007-04-23
You mean official as in download from [www.ati.com?](www.ati.com?)

As far as I can see, the latest available version is only 8.35.5, at least for my card which is a Mobility FireGL V5200.

:guitar: 

/Anders

---

### Post by hyfans on 2007-04-23
recheck [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5.html)

and say sorry to you, your card is not supported in 8.36.5:(

---

### Post by hyfans on 2007-04-23
and only xorg7.1 supported.

sadly enough:mad:

---

### Post by blkmax on 2007-04-23
I get the following for 8.36.5 for my Radeon x600 Pro.

ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.m17159


Seems we need to wait for a new update from Nvidia. I tried to use the override function to go back to x7.1.x without any success. I guess I can't formulate it right.


Regards

Marc

---

### Post by hyfans on 2007-04-23
except the Xvideo and 2d acceleration problem, i can build 8.36.5 on feisty ,correctly by issuing this command.


./ati-xxxx.run --buildpkg Ubuntu/feisty

after that, you will get four debs to install.

then module-assistant build the fglrx module and restart get X working.

never see the warnging you mentioned.

did you try the command i said above?

---

### Post by logg on 2007-04-23
Update:

I downloaded the fglrx driver version 8.36.5 from ati.com and then built and installed the module by

    bash  ati-driver-installer-8.36.5-x86.x86_64.run --buildpkg Ubuntu/feisty
    dpkg -i xorg-driver-fglrx-dev_8.36.5-1_i386.deb

This driver indeed claims to work with X 7.2.0 (it does).

I can now start X with the fglrx driver, but direct rendering is missing. Here's what X reports:

  (EE) fglrx(0): GART is not initialized, disabling DRI
  (WW) fglrx(0): ***********************************************
  (WW) fglrx(0): * DRI initialization failed!                  *
  (WW) fglrx(0): * (maybe driver kernel module missing or bad) *
  (WW) fglrx(0): * 2D acceleraton available (MMIO)             *
  (WW) fglrx(0): * no 3D acceleration available                *
  (WW) fglrx(0): ********************************************* *

Also, when I try to load the fglrx kernel module, I get the following message (modprobe -v):

  install /sbin/lrm-video fglrx 
  FATAL: Error running install command for fglrx

Any ideas?

/Anders

---

### Post by hyfans on 2007-04-23
seems you did something wrong with the kernel module install.

try to manualy insert the module by using insmod

---

### Post by logg on 2007-04-24
Thanks,

Here's an update: I can now install the fglrx kernel module by

    modprobe fglrx

The solution was to first

    apt-get install --reinstall linux-restricted-modules-common linux-restricted-modules-generic

Then make sure the fglrx module was not disabled in /etc/default/linux-restricted-modules-common,
then reboot and finally

    depmod -a

and restart X...

But: I still don't get direct rendering, since the fglrx kernel module is too old. This is what X tells me:

  (II) fglrx(0): Kernel Module Version Information:
  (II) fglrx(0):     Name: fglrx
  (II) fglrx(0):     Version: 8.34.8
  (II) fglrx(0):     Date: Feb 20 2007
  (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
  (WW) fglrx(0): Kernel Module version does *not* match driver.
  (EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

:( 

/Anders

---

### Post by logg on 2007-04-24
Works now!

The problem was that I was using the fglrx kernel module packaged by Ubuntu (an older version)
together with the latest fglrx xorg driver from ATI. The solution was to use the latest xorg driver *and* the latest  kernel driver (8.36.5).

I just needed to follow the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

:guitar: 

/Anders

---

