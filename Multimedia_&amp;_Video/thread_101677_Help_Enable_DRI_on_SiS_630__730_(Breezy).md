---
title: "Help? Enable DRI on SiS 630 / 730 (Breezy)"
date: 2005-12-10
forum: Multimedia &amp; Video
---

### Post by widjajayd on 2005-12-10
I try to enable DRI on my SIS 630 / 730 in ubuntu breezy 

I have Sis 630 onboard in ASUS TUSI-M motherboard.
it said from [www.winischhofer.net](www.winischhofer.net) it can work with dri

I have recompile my kernel, activate sisfb but no good result

if anyone have same experience installing this device 
please help

thanks before

---

### Post by ranf on 2005-12-10
The DRI wiki also says it works:
[http://dri.freedesktop.org/wiki/SiS](http://dri.freedesktop.org/wiki/SiS)

There is a HowTo for savage cards (installation of DRI snapshot) in the "Customization Tips & Tricks" forum which can be adapted to your SIS.

Instead of savage... file you need this most likely:
[http://dri.freedesktop.org/snapshots/archive/sis-20050628-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/archive/sis-20050628-linux.i386.tar.bz2)

---

### Post by widjajayd on 2005-12-10
Thank you, I have tried but I got an Error message 

I have download and install common-20050707-linux.i386.tar.bz2 without problem.

but when I tried to run sis-20050628-linux.i386.tar.bz2

it said The DRI drivers can not be installed without the latest kernel modules

Below is my steps and my error

Thank you for your help

```


tar -xjf sis-20050628-linux.i386.tar.bz2
cd dripkg
sudo ./install.sh


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


Dri.log

make DRM_MODULES=sis.o modules
make[1]: Entering directory `/home/kid/dripkg/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
.
.
.
  CC [M]  /home/kid/dripkg/drm/linux-core/drm_agpsupport.o
  CC [M]  /home/kid/dripkg/drm/linux-core/drm_scatter.o
  CC [M]  /home/kid/dripkg/drm/linux-core/drm_memory_debug.o
  CC [M]  /home/kid/dripkg/drm/linux-core/ati_pcigart.o
  CC [M]  /home/kid/dripkg/drm/linux-core/sis_drv.o
/home/kid/dripkg/drm/linux-core/sis_drv.c:62: error: `sis_PCI_IDS' undeclared here (not in a function)
/home/kid/dripkg/drm/linux-core/sis_drv.c:62: error: initializer element is not constant
/home/kid/dripkg/drm/linux-core/sis_drv.c:62: error: (near initialization for `pciidlist[0]')
make[3]: *** [/home/kid/dripkg/drm/linux-core/sis_drv.o] Error 1
make[2]: *** [_module_/home/kid/dripkg/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/kid/dripkg/drm/linux-core'
make: *** [sis.o] Error 2

My X version

X -version

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux edubuntu 2.6.12-satu #1 Sun Dec 11 01:10:45 EST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-satu (root@edubuntu) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Sun Dec 11 01:10:45 EST 2005
```

---

### Post by survival on 2005-12-17
my mainbroad alse use sis630 chipset. and i did like this....and meet the same problem ..............

root@ubuntu:/ # cd dripkg
root@ubuntu:/ # sudo ./install.sh
rm: cannot remove `dri.log': No such file or directory


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver:

Driver Name    : sis
Description    : Silicon Integrated Systems
Architecture   :
Build Date     : 20050630
Kernel Module  : sis

Optional Information

Driver Version      :
Special Description :

Press ENTER to continue or CTRL-C to exit.
^[[B^[[B^[[B^[[D


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will need to copy the DRI XFree86 driver modules to
your XFree86 directory.

The script will use the following XFree86 directory:

 /usr/X11R6

If this is correct press ENTER, press C to change or CTRL-C to exit.





DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.12-10-386
Module Directory : /lib/modules/2.6.12-10-386

If this is correct press ENTER, press C to change or CTRL-C to exit.




DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The following problems have occured:

        - XFree86 DRI directory does not exist

The script can create these directories for you.

Press ENTER to continue or CTRL-C to abort.






DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

dri.log


Makefile:163: *** Cannot find a kernel config file.  Stop.



****************************************8
help!!! i am on line now....waiting for you help!

thank you very much!!

---

### Post by ranf on 2005-12-17
[QUOTE=survival]Makefile:163: *** Cannot find a kernel config file. Stop.
[/QUOTE]
So `linux-headers-2.6.12-...' are installed?

---

### Post by survival on 2005-12-17
[QUOTE=ranf]So `linux-headers-2.6.12-...' are installed?[/QUOTE]


in my above words,that list contain this one..
Kernel Version : 2.6.12-10-386

does this mean what you said???

---

### Post by ranf on 2005-12-17
[QUOTE=survival]in my above words,that list contain this one..
Kernel Version : 2.6.12-10-386
[/QUOTE]
Ah, ok, I should read more carefully.

You can copy the config of the kernel from the /boot directory:
```

sudo cp /boot/config-2.6.12-10-386 /usr/src/linux-headers-2.6.12-10/.config

```

---

### Post by survival on 2005-12-17
[QUOTE=ranf]Ah, ok, I should read more carefully.

You can copy the config of the kernel from the /boot directory:
```

sudo cp /boot/config-2.6.12-10-386 /usr/src/linux-headers-2.6.12-10/.config

```[/QUOTE]


sorry ,in my /usr/src folder ,there is only one subfolder named rpm.
so ,i should "mkdir linux-header-2..6.12-10" right??? and then do the cp??

and just now , i upgrade my ubuntn from 5.04 to 5.10.
 i met a little problem. and i just wrote another "asking for help " file,
which address is:[http://www.ubuntuforums.org/showthread.php?p=582696#post582696](http://www.ubuntuforums.org/showthread.php?p=582696#post582696)


thank you !:)

---

### Post by ranf on 2005-12-17
[QUOTE=survival]sorry ,in my /usr/src folder ,there is only one subfolder named rpm.
so ,i should "mkdir linux-header-2..6.12-10" right??? and then do the cp??
[/QUOTE]
No that won't help you.

Please look for this savage howto. It has all the stuff listed that are required to Build DRI drivers.

---

