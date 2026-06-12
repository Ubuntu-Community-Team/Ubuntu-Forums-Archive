---
title: "Logitech Quickcam Dark Ring problem"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by canadiandude007 on 2007-11-23
Hello,

I have an old Logitech Quickam (with dark focus ring) that I'm trying to get to work on the latest Ubuntu version.

When doing an "lsusb" I found that the ID for the cam is 046d:d001 which coincides with a driver for DIVIO NW801/NW802. Reference here: [http://www.qbik.ch/usb/devices/showdev.php?id=307](http://www.qbik.ch/usb/devices/showdev.php?id=307)

I tried following the instructions by first downloading the cvs and patch software. Since the kernel is 2.6.22.14 I figured the following would work:

cvs -dserver:anonymous@nw802.cvs.sourceforge.net:/cvs root/nw802 login
cvs -z3 -dserver:anonymous@nw802.cvs.sourceforge.net:/cvs root/nw802 co -P nw802-2.4
cd nw802-2.4
cp Makefile.26 Makefile
patch -p0 < patch-2.6
make clean
make

The first line doesn't work whatsoever as it asks for a password, but I am able to grab the files and go into the nw802-2.4 folder, replace the Makefile and patch it.

When I run "make" there are problems with it finding the usbvideo.h and usbvideo.c files. I've tried finding them on the Internet, copying the data into a text file and saving the information into the appropriate directories.

However I'm still having problems and not sure if it's due to the Makefile or what.

Is there an "apt-get install" command I can run to grab the linux source so that the usbvideo.c file is included in it (or for that matter, all files are included)?

Any other thoughts of what to try? Errors I've received have been during the compilation of the files that they are referencing non-existent files.

Help please.

Thanks!

---

### Post by redfox7691 on 2007-11-27
If you use this command 

apt-get install linux-source

you download linux source archive so in your nw802 source directory you can

tar xjf /usr/src/linux-source-2.6.22.tar.bz2

The files usbvideo.c and usbvideo.h are in this directory:

linux-source-2.6.22/drivers/media/video/usbvideo/

But I've got a lot of copile error... so please, if you have some success on build nw802.ko module please post a message!

---

### Post by canadiandude007 on 2007-11-27
Hi,

Are you using the CVS version in nw802-2.4 folder or did you download from the Internet the nw802-2.4-0.0.99 package?

I know both are different.  The CVS version seemed the easiest and looked like patching it to 2.6 was ok.  The only problem I have is with the compile.

I downloaded the source and found the usbvideo.c and usbvideo.h files as you said.

So I changed the Makefile to read:
KERNEL_SOURCE ?= /usr/src/linux-source-2.6.22/

obj-m := nw8xx.o usbvideo.o
nw8xx-objs := nw8xx_jpgl.o nw802.o


default: 
        ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.h .
        ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.c .
        make -C ${KERNEL_SOURCE} SUBDIRS=`pwd` modules

clean:
        rm -f usbvideo.h usbvideo.c *.o *.ko *~ *.mod.c


Then when I did the "make" on that I decided to send the errors to errors.txt
# make > errors.txt

What showed up was this:
  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

So then I ran ...
# make oldconfig && make prepare

followed by a 
# make clean

followed by ...
# make > errors.txt

and got ...
#  make > errors.txt
/bin/sh: scripts/genksyms/genksyms: not found
make[2]: *** [/home/tmpuser/nw802-2.4/usbvideo.o] Error 127
make[1]: *** [_module_/home/tmpuser/nw802-2.4] Error 2
make: *** [default] Error 2

When I checked out the errors.txt file I got ...

ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.h .
ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.c .
make -C /usr/src/linux-source-2.6.22/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.22/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/tmpuser/nw802-2.4/nw8xx_jpgl.o
  CC [M]  /home/tmpuser/nw802-2.4/nw802.o
  LD [M]  /home/tmpuser/nw802-2.4/nw8xx.o
  CC [M]  /home/tmpuser/nw802-2.4/usbvideo.o

I'm not sure what Error 127 means, but I've seen Error 2 lots!

I'm documenting this essentially as I go, in case others have any luck with it.

---

### Post by canadiandude007 on 2007-11-27
Found a similar problem with 127 error in Ubuntu forums ...

[http://ubuntuforums.org/showthread.php?t=380611](http://ubuntuforums.org/showthread.php?t=380611)

And said to try running a "sudo m-a update,prepare" to resolve.

Did a check that m-a = module-assistant, so running ...

# apt-get install module-assistant

To install it, then will run the m-a update,prepare and see if I get any further.

---

### Post by canadiandude007 on 2007-11-27
After I did the installation of the module-assistant I found among the header files the file I was looking for, so I copied it to the source directory ...

# cp /usr/src/linux-headers-2.6.22-14-generic/Module.symvers /usr/src/linux-source-2.6.22/Module.symvers

Then a ...
# make clean
# make > errors.txt

got this on xterm ...
/bin/sh: scripts/genksyms/genksyms: not found
make[2]: *** [/home/tmpuser/nw802-2.4/usbvideo.o] Error 127
make[1]: *** [_module_/home/tmpuser/nw802-2.4] Error 2
make: *** [default] Error 2

and inside the errors.txt file I found this ...
ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.h .
ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.c .
make -C /usr/src/linux-source-2.6.22/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/tmpuser/nw802-2.4/nw8xx_jpgl.o
  CC [M]  /home/tmpuser/nw802-2.4/nw802.o
  LD [M]  /home/tmpuser/nw802-2.4/nw8xx.o
  CC [M]  /home/tmpuser/nw802-2.4/usbvideo.o
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'

So am getting closer

---

### Post by canadiandude007 on 2007-11-27
Then I have had to copy over the file ...

# cp /usr/src/<linux header source>/scripts/genksyms/genksyms /usr/src/linux-source-2.6.22/scripts/genksyms

Then got a modpost error ...

ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.h .
ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.c .
make -C /usr/src/linux-source-2.6.22/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/tmpuser/nw802-2.4/nw8xx_jpgl.o
  CC [M]  /home/tmpuser/nw802-2.4/nw802.o
  LD [M]  /home/tmpuser/nw802-2.4/nw8xx.o
  CC [M]  /home/tmpuser/nw802-2.4/usbvideo.o
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'

the script wasn't found so will need to add that ...

---

### Post by canadiandude007 on 2007-11-27
Easy way to find files you need ... just do a ...

# locate <name of file>

so I copied "modpost" into ../usr/src/linux-source-2.6.22/scripts/mod

Did a ...
#make clean

then ...

# make > errors.txt

I got no errors on the screen and my errors.txt file shows ...

ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.h .
ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.c .
make -C /usr/src/linux-source-2.6.22/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/tmpuser/nw802-2.4/nw8xx_jpgl.o
  CC [M]  /home/tmpuser/nw802-2.4/nw802.o
  LD [M]  /home/tmpuser/nw802-2.4/nw8xx.o
  CC [M]  /home/tmpuser/nw802-2.4/usbvideo.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/tmpuser/nw802-2.4/nw8xx.mod.o
  LD [M]  /home/tmpuser/nw802-2.4/nw8xx.ko
  CC      /home/tmpuser/nw802-2.4/usbvideo.mod.o
  LD [M]  /home/tmpuser/nw802-2.4/usbvideo.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'

So now looks like I've got the .ko file compiled.  Phew!

Will let you know what other snags I run into ...

---

### Post by canadiandude007 on 2007-11-27
Ok so now in my directory I have ...

ls
cvideopro.init    Makefile              nw802.o          proscope.init
d-link-350c.init  Makefile.26           nw8xx_jpgl.c     SpaceCam.init
DS3303u.init      Makefile.26_bak       nw8xx_jpgl.h     trust_space.init
errors1.txt       Makefile.bak          nw8xx_jpgl.o     Twinkle.init
errors2.txt       Module.symvers        nw8xx.ko         usbvideo.c
errors3.txt       mustek_300_mini.init  nw8xx.mod.c      usbvideo.h
errors4.txt       nw800.init            nw8xx.mod.o      usbvideo.ko
errors.txt        nw801.init            nw8xx.o          usbvideo.mod.c
kr651us.init      nw802.c               nw8xx_regedit.c  usbvideo.mod.o
kritter.init      nw802.init            patch-2.6        usbvideo.o


and doing a ...
# modprobe videodev

gave no errors

but trying ...
# insmod usbvideo.o 

gave ...

insmod: error inserting 'usbvideo.o': -1 Invalid module format

tried instead with ...
# insmod usbvideo.ko

and got as error ...
insmod: error inserting 'usbvideo.ko': -1 Unknown symbol in module

Any ideas??

---

### Post by JLTB on 2008-02-06
Hello,

Yet one more stubborn fool trying to get this module working.  I'm using an Irez Kritter Cam (802 chipset).

I think I may have gotten one baby step further, but I still can't get everything installed either.

Try:

```

sudo insmod usbvideo.mod.o

```

It appears there are some .mod.o files generated and the usbvideo one is accepted by insmod on my machine!  No trace of the nw802.mod.o though :-/.  There is an nw8xx.mod.o ... which is strange.

Anyone else with further luck?

---

### Post by Siftah on 2008-02-28
Thanks for the helpful info in this thread I've been able to get my module compiled and loaded;

Using the latest CVS code and following the above I managed to get a successful compile, I was then able to `modprobe usbvideo` and then `insmod nw8xx.ko`.

Output to dmesg was:
```

[438131.127520] nw802.c: Potentially NW8xx supported cam found ( supported vendor/product IDs )
[438131.130239] nw802.c: Detected bridge type : DivIO NW802
[438131.130995] videodev: "nw802 USB Camera" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/
[438131.131005] /build/buildd/linux-source-2.6.22-2.6.22/drivers/media/video/usbvideo/usbvideo.c: nw802 on /dev/video1: canvas=320x240 videosize=320x240
[438131.131047] usbcore: registered new interface driver nw802
[438131.131078] nw802.c: Module loaded

```

---

### Post by eduardomartin71 on 2008-04-17
Great Job to all of you!!!!!

I finally was able to compile the modules without errors.

The thing that is bugging me is that i get an error when i try to insert the module.
For instance:
eduardo@dell640:~/descargas/802/nw802-2.4$ sudo insmod nw8xx.mod.o
insmod: error inserting 'nw8xx.mod.o': -1 Unknown symbol in module

Any Help??

Thanks a lot!!!!

---

### Post by canadiandude007 on 2008-04-23
Hiya,

Do a 'dmesg' command and let me know the output.

Cheers!

---

### Post by canadiandude007 on 2008-05-21
Just for reference, here are the steps in one post:

Steps (to install Logitech Dark Ring webcam ... should also work with other Debian supported platforms)
--------------------------------------

#> sudo su
#> apt-get install cvs

## will install cvs package.

#> cvs -z3 -d:pserver:anonymous@nw802.cvs.sourceforge.net:/cvsroot/nw802 co -P nw802-2.4

## will create folder in pwd called nw802-2.4

#> cd nw802-2.4
#> cp Makefile Makefile.bak
#> apt-get install patch

## will install patch package (might need to load ISO CD of Ubuntu)

#> patch -p0 < patch-2.6
#> make clean
#> apt-get install linux-source

## will install linux source files under /usr/src (might need press Y to proceed)

#> cd /usr/src
#> ls -l

## will tell you which linux source file to unzip/decompress

#> tar xjf /usr/src/linux-source-2.6.22.tar.bz2
#> cd /home/<username>/nw802-2.4

## will need to change <username> to whichever name you logged on with

#> gedit Makefile

## change to read as follows ...

KERNEL_SOURCE ?= /usr/src/linux-source-2.6.22/

obj-m := nw8xx.o usbvideo.o
nw8xx-objs := nw8xx_jpgl.o nw802.o


default: 
	ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.h .
	ln -sf /usr/src/linux-source-2.6.22/drivers/media/video/usbvideo/usbvideo.c .
	make -C ${KERNEL_SOURCE} SUBDIRS=`pwd` modules

clean:
	rm -f usbvideo.h usbvideo.c *.o *.ko *~ *.mod.c

## then save file

#> apt-get install module-assistant
#> m-a update,prepare

## might need to press Y to continue

#> cd /usr/src/linux-source-2.6.22
#> make oldconfig && make prepare
#> cp /usr/src/linux-headers-2.6.22-14-generic/Module.symvers /usr/src/linux-source-2.6.22/Module.symvers
#> cp /usr/src/linux-headers-2.6.22-14-generic/scripts/genksyms/genksyms /usr/src/linux-source-2.6.22/scripts/genksyms/genksyms
#> cp /usr/src/linux-headers-2.6.22-14-generic/scripts/mod/modpost /usr/src/linux-source-2.6.22/scripts/mod/modpost

#> cd /home/<username>/nw802-2.4
#> make clean
#> make

## should compile now ok

#> modprobe usbvideo
#> insmod nw8xx.ko

## Check with running

#> dmesg | more

## Should see details of Webcam now installed

---

