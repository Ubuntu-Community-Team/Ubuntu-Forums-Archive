---
title: "can't get my logitech quickcam messenger to work"
date: 2008-05-21
forum: Multimedia Software
---

### Post by antimatter on 2008-05-21
Hello!
I've already tried all the howtos i found on this forum. this is probably because they're all written for older ubuntu releases. the latest thing i tried, was following the steps posted in this thread: [http://ubuntuforums.org/showthread.php?t=642015](http://ubuntuforums.org/showthread.php?t=642015)
but i cant install the modules in the module manager and i cant even find the spca5xx-source package anywhere on the package servers. m-a gives me the following error:


[I]

 /usr/bin/make -f debian/rules clean                                        &#8593;
 &#9474; make[1]: Entering directory `/usr/src/modules/qc-usb-source'               &#9646;
 &#9474; dh_testdir                                                                 &#9618;
 &#9474; dh_testroot                                                                &#9618;
 &#9474; /usr/bin/make VERSION_CODE=4 clean                                         &#9618;
 &#9474; make[2]: Entering directory `/usr/src/modules/qc-usb-source'               &#9618;
 &#9474; rm -f *.o qcset show *~ .\#* .*.cmd *.mod.c *.ko                           &#9618;
 &#9474; rm -rf .tmp_versions                                                       &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/qc-usb-source'                &#9618;
 &#9474; rm -rf debian/qc-usb-modules-*                                             &#9618;
 &#9474; rm -f debian/control.modules                                               &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/qc-usb-source'                &#9618;
 &#9474; /usr/bin/make -f debian/rules clean binary-modules                         &#9618;
 &#9474; make[1]: Entering directory `/usr/src/modules/qc-usb-source'  
 dh_testdir                                                                 &#9618;
 &#9474; dh_testroot                                                                &#9618;
 &#9474; /usr/bin/make VERSION_CODE=4 clean                                         &#9618;
 &#9474; make[2]: Entering directory `/usr/src/modules/qc-usb-source'               &#9618;
 &#9474; rm -f *.o qcset show *~ .\#* .*.cmd *.mod.c *.ko                           &#9618;
 &#9474; rm -rf .tmp_versions                                                       &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/qc-usb-source'                &#9618;
 &#9474; rm -rf debian/qc-usb-modules-*                                             &#9618;
 &#9474; rm -f debian/control.modules                                               &#9618;
 &#9474; dh_clean                                                                   &#9618;
 &#9474; dh_testdir                                                                 &#9618;
 &#9474; dh_testroot     
 dh_clean -k                                                                &#8593;
 &#9474; /usr/bin/make RELEASE=2.6.24-16-generic                                    &#9618;
 &#9474; LINUX_DIR=/usr/src/linux-headers-2.6.24-16-generic \                       &#9618;
 &#9474;                                                                            &#9618;
 &#9474; PREFIX=/usr/src/modules/qc-usb-source/debian/qc-usb-modules-2.6.24-16-gen  &#9646;
 &#9474; eric/usr \                                                                 &#9618;
 &#9474;                                                                            &#9618;
 &#9474; MODULE_DIR=/usr/src/modules/qc-usb-source/debian/qc-usb-modules-2.6.24-16  &#9618;
 &#9474; -generic/lib/modules/2.6.24-16-generic \                                   &#9618;
 &#9474;         install                                                            &#9618;
 &#9474; make[2]: Entering directory `/usr/src/modules/qc-usb-source'               &#9618;
 &#9474; make -C "/usr/src/linux-headers-2.6.24-16-generic"                         &#9618;
 &#9474; SUBDIRS="/usr/src/modules/qc-usb-source" modules V=1                       &#9618;
 &#9474; USER_OPT="-DHAVE_UTSRELEASE_H=1"                                           &#9618;
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
 test -e include/linux/autoconf.h -a -e include/config/auto.conf || (       &#8593; 
    &#9474; \                                                                          &#9618; 
    &#9474;         echo;\                                                             &#9618; 
    &#9474;         echo "  ERROR: Kernel configuration is invalid.";\                 &#9618; 
    &#9474;         echo "         include/linux/autoconf.h or                         &#9618; 
    &#9474; include/config/auto.conf are missing.";\                                   &#9618; 
    &#9474;         echo "         Run 'make oldconfig && make prepare' on kernel      &#9646; 
    &#9474; src to fix it.";        \                                                  &#9618; 
    &#9474;         echo;\                                                             &#9618; 
    &#9474;         /bin/false)                                                        &#9618; 
    &#9474; mkdir -p /usr/src/modules/qc-usb-source/.tmp_versions ; rm -f              &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/.tmp_versions/*                             &#9618; 
    &#9474; make -f scripts/Makefile.build obj=/usr/src/modules/qc-usb-source          &#9618; 
    &#9474;   gcc -m32 -Wp,-MD,/usr/src/modules/qc-usb-source/.qc-driver.o.d           &#9618; 
    &#9474; -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include    
 -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef   &#9618; 
    &#9474; -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common        &#9618; 
    &#9474; -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3   &#9618; 
    &#9474; -freg-struct-return -mpreferred-stack-boundary=2  -march=i586              &#9618; 
    &#9474; -mtune=generic -ffreestanding -maccumulate-outgoing-args                   &#9618; 
    &#9474; -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g                     &#9646; 
    &#9474; -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign       &#9618; 
    &#9474; -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s"            &#9618; 
    &#9474; -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"                                  &#9618; 
    &#9474; -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o                              &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/.tmp_qc-driver.o                            &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c  
 In file included from /usr/src/modules/qc-usb-source/qc-driver.c:47:       &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/quickcam.h:129:1: warning: "BIT" redefined  &#9618; 
    &#9474; In file included from include/linux/kernel.h:15,                           &#9618; 
    &#9474;                  from include/linux/cache.h:4,                             &#9618; 
    &#9474;                  from include/linux/time.h:7,                              &#9618; 
    &#9474;                  from include/linux/videodev2.h:59,                        &#9618; 
    &#9474;                  from include/linux/videodev.h:15,                         &#9618; 
    &#9474;                  from /usr/src/modules/qc-usb-source/quickcam.h:95,        &#9646; 
    &#9474;                  from /usr/src/modules/qc-usb-source/qc-driver.c:47:       &#9618; 
    &#9474; include/linux/bitops.h:6:1: warning: this is the location of the           &#9618; 
    &#9474; previous definition                                                        &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c: In function ‘qc_i2c_init’: 
 /usr/src/modules/qc-usb-source/qc-driver.c:824: error: ‘struct urb’ has    &#9618; 
    &#9474; no member named ‘lock’                                                     &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c:825: warning: assignment from   &#9618; 
    &#9474; incompatible pointer type                                                  &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c: In function ‘qc_isoc_start’:   &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c:1867: warning: assignment       &#9618; 
    &#9474; from incompatible pointer type                                             &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c: At top level:                  &#9618; 
    &#9474; /usr/src/modules/qc-usb-source/qc-driver.c:3009: error: unknown field      &#9618; 
    &#9474; ‘hardware’ specified in initializer                                        &#9646; 
    &#9474; make[4]: *** [/usr/src/modules/qc-usb-source/qc-driver.o] Error 1          &#9618; 
    &#9474; make[3]: *** [_module_/usr/src/modules/qc-usb-source] Error 2  
 make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'      &#9618; 
    &#9474; make[2]: *** [quickcam.ko] Error 2                                         &#9618; 
    &#9474; make[2]: Leaving directory `/usr/src/modules/qc-usb-source'                &#9618; 
    &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618; 
    &#9474; make[1]: Leaving directory `/usr/src/modules/qc-usb-source'                &#9618; 
    &#9474; make: *** [kdist_image] Error 2                                            &#9646; 
    &#9474; ^Y                                       


[/I]

help please! :(

---

### Post by linuxwizard on 2008-05-22
Did you try using your webcam before you started trying to install a driver ? Alot of Logitech webcams will works out of the box. Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by antimatter on 2008-05-25
yes. i've alreayd tried ekiga, camorama and cheese. no dice

---

### Post by S-99 on 2008-11-14
Necro'd. Try compiling the qc-usb-source package in the repos for hardy or intrepid depending on which ubuntu you're using.

EDIT: **** what i just said and ignore it. The qc-usb-source package in the repos for ubuntu of new and old don't isn't a driver for the quickcam messenger. Go [here](http://home.mag.cx/messenger/) and download the qc-usb-messenger driver which as of now is version 1.8. Don't pay attention to the 1.7 update because 1.8 is newer, better, and is in there.

Download it and follow the instructions for compiling it. It sucks your quickcam messenger isn't working out of the box. It has for me in ubuntu ever since feisty got released, but ever since feisty came out it never wanted to work out of the box for me in gyachi. It always worked in gyachi with the qc-usb-messenger driver though.

---

### Post by scunc_dvl on 2008-11-14
The driver sources keep giving me compile errors -

> qc-driver.c:1630: error: request for member &#8216;counter&#8217; in something not a structure or union

:-\

EDIT: I fixed much of my compile errors now. The symlink /lib/modules/`uname -r`/build must point to your relevant linux-headers directory (eg. /usr/src/linux-headers-2.6.26.8). [http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial) instructions were getting me tripped up...

---

### Post by scunc_dvl on 2008-12-01
I found out that for my Quickcam Messenger, identified as 046d:08da in 'lsusb', does -NOT- actually use the qc-usb drivers to work at all! It has a zc0301 chip and apparantly works (for me, anyway), using the gspca driver.

Hopefully you will be able to find the package *gspca-source*. It installs a tarball in your /usr/src directory..

Read the source's readme file here - 
```
less /usr/share/doc/gspca-source/README.Debian
``` 
compiling the driver. I still use "tar xvf ; make ; sudo make install" often and it just happened to work for me, after struggling with symlinks pointing to sources instead of kernel headers and vice versa. But I've just learned the modules assistant way of compiling seems a bit more reliable...sometimes...

I don't understand why there is a zc0301 module in addition to gspca, but qc-usb does NOT support this particular model of camera.. Despite having its id somewhere in their code.. :\

---

