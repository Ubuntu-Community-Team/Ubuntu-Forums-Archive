---
title: "Intrepid broke gspca! Bad luck for Logitech QuickCam Express Plus"
date: 2008-12-13
forum: Multimedia Software
---

### Post by gluonman on 2008-12-13
I've traveled the cosmos attempting to get my webcam to work. It worked alright in Hardy (granted it gave less-than-perfect image quality), but from the posts I've been reading it appears that the new kernel-integrated gspca module is super buggy. The new bugs in the kernel result in me not being able to compile the old 3rd party gspca module which is known to work. I guess there's also some issues with gstreamer and v4l, but the complexity of these bugs is a bit much for me to understand what I need to do.

At this point, I'm just going to sit around and wait until 1) some non-noobophobe responds to this post with a step-by-step solution that puts a smile on my face (and gratitude in my heart), or 2) Ubuntu develops the fix and releases it as an update.

For those of you who would like to help tackle my problem, I will disclose the necessary background information, and post some errors:

```
lsusb
``` produces the following output:

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

With the QuickCam being the device I'm interested in.

```
lsmod | grep gspca
``` produces the following output:

```
gspca_spca561          19328  0 
gspca_main             29312  1 gspca_spca561
videodev               41344  2 uvcvideo,gspca_main
usbcore               148848  5 uvcvideo,gspca_spca561,gspca_main,uhci_hcd
```

But this is the kernel-integrated module that's buggy, so it's not reliable for my purposes.

I have all the necessary dependencies installed to build the older 3rd party module: namely module-assistant gspca-source build-essential yaddyaddyadda.

My steps were as follows:

```
sudo m-a prepare
```

And the terminal output was:

```
Getting source for kernel version: 2.6.27-9-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
```

Then,

```
sudo m-a a-i gspca
```

And the module-assistant entered into its interactive mode and this happens:

[IMG]http://img399.imageshack.us/img399/7388/gspcafailmp8.png[/IMG]

So I attempted an alternative by gathering the gspca package from another source and trying to compile that, but there were errors.

The following is an exact copy of what my terminal looked like when I finished my attempt (errors included):

```
gluonman@Cygnus-X1:~$ wget -c http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
--2008-12-12 23:48:46--  http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
Resolving mxhaard.free.fr... 212.27.63.150
Connecting to mxhaard.free.fr|212.27.63.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 214717 (210K) [application/x-gzip]
Saving to: `gspcav1-20071224.tar.gz'

100%[==============================================>] 214,717     79.4K/s   in 2.6s    

2008-12-12 23:48:49 (79.4 KB/s) - `gspcav1-20071224.tar.gz' saved [214717/214717]

gluonman@Cygnus-X1:~$ tar -xvf gspcav1-20071224.tar.gz
gspcav1-20071224/
gspcav1-20071224/decoder/
gspcav1-20071224/decoder/gspcadecoder.c
gspcav1-20071224/decoder/gspcadecoder.h
gspcav1-20071224/decoder/gspcadecoder-OSX.c
gspcav1-20071224/decoder/gspcadecoder-OSX.h
gspcav1-20071224/Makefile
gspcav1-20071224/Vimicro/
gspcav1-20071224/Vimicro/vc032x_sensor.h
gspcav1-20071224/Vimicro/zc3xx.h
gspcav1-20071224/Vimicro/cs2102.h
gspcav1-20071224/Vimicro/vc032x.h
gspcav1-20071224/Vimicro/pas106b.h
gspcav1-20071224/Vimicro/icm105a.h
gspcav1-20071224/Vimicro/hv7131b.h
gspcav1-20071224/Vimicro/hv7131c.h
gspcav1-20071224/Vimicro/pb0330.h
gspcav1-20071224/Vimicro/ov7630c.h
gspcav1-20071224/Vimicro/mc501cb.h
gspcav1-20071224/Vimicro/tas5130c_vf0250.h
gspcav1-20071224/Vimicro/ov7620.h
gspcav1-20071224/Vimicro/tas5130c.h
gspcav1-20071224/Vimicro/hdcs2020.h
gspcav1-20071224/Etoms/
gspcav1-20071224/Etoms/et61xx51.h
gspcav1-20071224/Sonix/
gspcav1-20071224/Sonix/sn9cxxx.h
gspcav1-20071224/Sonix/sonix.h
gspcav1-20071224/utils/
gspcav1-20071224/utils/spcagamma.h
gspcav1-20071224/utils/spcausb.h
gspcav1-20071224/utils/spcaCompat.h
gspcav1-20071224/Conexant/
gspcav1-20071224/Conexant/cx11646.h
gspcav1-20071224/Conexant/cxlib.h
gspcav1-20071224/Pixart/
gspcav1-20071224/Pixart/pac207-OSX.h
gspcav1-20071224/Pixart/pac7311.h
gspcav1-20071224/Pixart/pac207.h
gspcav1-20071224/changelog
gspcav1-20071224/license
gspcav1-20071224/gspca_core.c
gspcav1-20071224/Transvision/
gspcav1-20071224/Transvision/tv8532.h
gspcav1-20071224/Makefile.kld
gspcav1-20071224/gspca.h
gspcav1-20071224/Sunplus/
gspcav1-20071224/Sunplus/spca501.dat
gspcav1-20071224/Sunplus/spca505.dat
gspcav1-20071224/Sunplus/spca508.dat
gspcav1-20071224/Sunplus/spca561-OSX.h
gspcav1-20071224/Sunplus/spca506.h
gspcav1-20071224/Sunplus/spca561.h
gspcav1-20071224/Sunplus/spca501_init.h
gspcav1-20071224/Sunplus/spca508_init-OSX.h
gspcav1-20071224/Sunplus/spca508_init.h
gspcav1-20071224/Sunplus/spca501_init-OSX.h
gspcav1-20071224/Sunplus/spca505_init.h
gspcav1-20071224/Sunplus-jpeg/
gspcav1-20071224/Sunplus-jpeg/spca500.dat
gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20071224/Sunplus-jpeg/spca500_init.h
gspcav1-20071224/gspca_build
gspcav1-20071224/READ_AND_INSTALL
gspcav1-20071224/Mars-Semi/
gspcav1-20071224/Mars-Semi/mr97311.h
gspcav1-20071224/cutlog.py
gluonman@Cygnus-X1:~$ cd gspcav1-20071224
gluonman@Cygnus-X1:~/gspcav1-20071224$ make clean
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
gluonman@Cygnus-X1:~/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/gluonman/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/gluonman/gspcav1-20071224/gspca_core.o
/home/gluonman/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/gluonman/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/home/gluonman/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/home/gluonman/gspcav1-20071224/gspca_core.c: At top level:
/home/gluonman/gspcav1-20071224/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/home/gluonman/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/gluonman/gspcav1-20071224/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/home/gluonman/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/gluonman/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/gluonman/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/home/gluonman/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/home/gluonman/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/gluonman/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/gluonman/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
gluonman@Cygnus-X1:~/gspcav1-20071224$ sudo make install
[sudo] password for gluonman: 
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
gluonman@Cygnus-X1:~/gspcav1-20071224$
``` 

At this point, my cam will work with Cheese, but it's super dark. It will also work with Xawtv, but again it is super dark. Whenever I open it with one of these programs, the green light on the cam will turn off when the program closes. When I try to access it in Kopete in "Settings -> Configure..." it's just a blank black square, and also causes the green light on the cam to go off. It does not work in Camorama or aMSN. aMSN just renders the same blank black square that Kopete gives, while Camorama gives me this:

[IMG]http://img408.imageshack.us/img408/8751/camoramafailoz3.png[/IMG]

And, of course, Camorama also turns off the green light on the cam.
Regarding the green light on the cam, I found that dmesg only contained information about gspca and my webcam when the green light was on.

```
[ 3996.688148] usb 2-2: USB disconnect, address 2
[ 3996.693913] gspca: disconnect complete
[ 3998.416118] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 3998.646011] usb 2-2: configuration #1 chosen from 1 choice
[ 3998.649222] gspca: probing 046d:092f
[ 3998.735149] gspca: probe ok
```

But when the green light was off, none of that information was in there.

My real goal, though, is to get my webcam to work in Kopete and aMSN so that my friends can see me. And a side-goal is to be able to improve the image quality once it is working. I need better resolution and I need to be able to adjust brightness more reasonably.

So you've seen everything I've seen. My errors, my compilation attempts. I've been all over the forums and found people who had fixes and solutions that didn't work for me. I tried patches to the gspca package, and tried a bunch of things, but I'm lost. Nothing has worked.

PLEASE, if you've actually been patient and kind enough to read over the necessary information and error messages that I've posted and have a solution, or at least an idea of what I can do, let me know. Feel free to ask me questions if you need more information while trying to help me.

I'll be keeping an eye on this thread for any productive solutions you wonderful people might post.

---

### Post by rcasha on 2008-12-28
I'm having similar problems - even before trying to replace the module I got cheese and xawtv working but showing a very dark image. Most others including skype, kopete etc. show static. Some applications give an error and quit.

Please post or email if you do find some solution.

---

### Post by mtopro on 2008-12-28
Don't know if this helps you as I am just a newbie, but this step by step took care of my webcam problems.  
[http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial#Install_Mercurial]("http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial#Install_Mercurial")


I noticed the information online to deal with the problem was rather limited so also this thread was posted.
[http://ubuntuforums.org/showthread.php?t=1023169]("http://ubuntuforums.org/showthread.php?t=1023169")


It appears that cam is supported under 046d:
[http://alpha.dyndns.org/ov511/cameras.html]("http://alpha.dyndns.org/ov511/cameras.html")

Please let me know if it ends up working for you too.:)

---

### Post by mgroat on 2009-01-10
I had the same problem, the solution to get Skype working was to run ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
``` When you're running xawtv, you can play with the brightness and exposure length until you get the picture looking the way you want it.

---

### Post by MerlinsLair on 2009-01-11
So in other words, I would need to go through all of that in the one link above (which by the way is very confusing for an amateur) just to get my Logitech webcam to work? Think I'll pass and just use the one I have on my vista laptop until the powers that be can work out an easier fix for us n00bs. Seeing as it's not a "make or break" kind of thing for me, I can wait.

---

### Post by riverberry on 2009-01-13
I got it to work in skype and cheese - logitech 2500 - and the image wasn't dark,  following the procedure at actionshrimps.com with some interaction with forums info I can't repeat. Now it's stopped and terminal says gspca module don't exist any more... so I have to give it a second try:guitar:

---

### Post by DOMiller on 2009-09-10
Greetin's,

I am also experiencing this exact problem.  Missing semaphore.h file and other errors, possibly dependent on the first.  Can't find any solutions online.  Is it still unsolved?  Tried Mercurial installation just in case, but it had no effect.

My webcam (PD1170) worked fine on same PC under Windows (nothing else did, but the webcam did).

If anyone found a working solution, please post.

---

### Post by alexpotato on 2010-05-03
> **mgroat said:**
> I had the same problem, the solution to get Skype working was to run ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
``` When you're running xawtv, you can play with the brightness and exposure length until you get the picture looking the way you want it.

This worked for me with a 046d:08a9 model Logitech Quick Cam in Ubuntu 9.10.

Any way to make this permanent? Currently, I just created an alias to launch Skype with the above command.

---

