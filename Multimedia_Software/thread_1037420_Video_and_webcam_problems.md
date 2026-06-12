---
title: "Video and webcam problems"
date: 2009-01-11
forum: Multimedia Software
---

### Post by polrosello on 2009-01-11
Hey everyone!

I just installed Ubuntu 8.10 on an old computer of ours for the first time... And it's great! The feeling of using a free and open-source operating system is amazing.  I do have a few problems, though...  Two, mainly.

**1) No video at all!**
Ok, not really true.  YouTube and other flash-based video work fine.  I'm just having issues playing video from files in my computer (sound, but no video).  Also, I'm using Skype and when I test my webcam I can't see anything (see the other problem for details).  The screen stays completely black.  I followed these instructions: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) Everything seemed to install fine without any errors but it did not solve the problem.  I also installed VLC media player but the same black screen appears.  Any ideas on what I could do to solve this problem?

**2) My webcam doesn't work with Skype!**

**[UPDATE] Problem solved.  Follow these instructions: [http://forum.skype.com/index.php?showtopic=225971](http://forum.skype.com/index.php?showtopic=225971)  Still looking for help on the first problem though...**

I might have to post this on the Skype forums as well but... Here it goes! I can see my image in flash-based online programs, but I get a black screen in Skype.  This is probably because of the video playback issues above.  However, the other person sees green static, which lead me to believe I *also* have a webcam driver problem.  The webcam is a Logitech Communicate STX, so the gspca driver *should* work.  When I try to install it, though, I get the following:

> REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mercedes/gspca/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/mercedes/gspca/gspcav1-20071224/gspca_core.o
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c: In function 'spca5xx_ioctl':
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function 'video_usercopy'
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c: At top level:
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:2609: error: unknown field 'owner' specified in initializer
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:2611: error: unknown field 'type' specified in initializer
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c: In function 'spca50x_create_sysfs':
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function 'video_device_create_file'
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function 'video_device_remove_file'
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c: In function 'spca5xx_probe':
/home/mercedes/gspca/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/mercedes/gspca/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/mercedes/gspca/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2

I'm really new to Linux, so I have no clue what this means.  I just followed the instructions on this video [www.linuxjournal.com/video/get-your-webcam-working-gspca](www.linuxjournal.com/video/get-your-webcam-working-gspca) , using the current location of the files instead of the old ones to try to install the drivers,  It would be great if you guys could enlighten me! How can I have my webcam work with Skype?

Thanks!

---

### Post by polrosello on 2009-01-17
Anyone?....

---

### Post by jbro on 2009-01-25
Unfortunately, I don't have any answers for you, but I am experiencing the same webcam problmes you mentioned and I can add some information so that perhaps someone else might be able to figure this out.

First, I have a Creative Live! Notebook Pro webcam (ID 041e:4051 Creative Technology, Ltd Live! Cam Notebook Pro). In Hardy, this camera worked great with all applications, but ever since I upgraded to Intrepid and kernel 2.6.27, the camera's performance has been bad. In Cheese, it "works", but I get about one frame every two to three seconds. In Gqcam, I get a mostly green image with some green static at the top of the image area. Skype, miraculously, seems to work. OpenCV (a computer vision package) can't even detect the camera, though in this case I may have to rebuild it from source.

I have tried rebuilding the gspca driver (my camera uses gspca_zc3xx) both from the Ubuntu gspca-source package and from the tarball from mxhard.free.fr. Both builds fail (they fail with the same errors you posted.) It seems that perhaps the source hasn't been updated for kernel 2.6.27. The gspca driver is included in the kernel, so obviously someone has patched the drivers so they at least build properly and "work".

It would be great to at least be able to get the sources patched to build with kernel 2.6.27. It's gotten to the point where I'm just going to try to find a camera that works better with Linux. (Itself a non-trivial task, the wiki claims my camera should work -- and it did, under 2.6.24.)

Regards,
Jay

---

