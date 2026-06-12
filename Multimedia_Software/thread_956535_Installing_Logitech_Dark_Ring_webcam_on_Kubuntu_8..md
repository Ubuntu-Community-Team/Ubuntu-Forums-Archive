---
title: "Installing Logitech Dark Ring webcam on Kubuntu 8.04"
date: 2008-10-23
forum: Multimedia Software
---

### Post by canadiandude007 on 2008-10-23
After getting an upgraded PC, I installed the latest version of Kubuntu 8.04 to take advantage of the KDE desktop.

No problems with the installation of my webcam following these steps:

Steps

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
## you will need to replace <version> with the numerical version
## example: 2.6.20

#> tar xjf /usr/src/linux-source-<version>.tar.bz2
#> cd /home/<username>/nw802-2.4

## will need to change <username> to whichever name you logged on with

#> gedit Makefile

## change to read as follows ...

KERNEL_SOURCE ?= /usr/src/linux-source-<version>/

obj-m := nw8xx.o usbvideo.o
nw8xx-objs := nw8xx_jpgl.o nw802.o


default: 
	ln -sf /usr/src/linux-source-<version>/drivers/media/video/usbvideo/usbvideo.h .
	ln -sf /usr/src/linux-source-<version>/drivers/media/video/usbvideo/usbvideo.c .
	make -C ${KERNEL_SOURCE} SUBDIRS=`pwd` modules

clean:
	rm -f usbvideo.h usbvideo.c *.o *.ko *~ *.mod.c

## then save file

#> apt-get install module-assistant
#> m-a update,prepare

## might need to press Y to continue

#> cd /usr/src/linux-source-<version>
#> make oldconfig && make prepare
#> cp /usr/src/linux-headers-<version>-generic/Module.symvers /usr/src/linux-source-<version>/Module.symvers
#> cp /usr/src/linux-headers-<version>-generic/scripts/genksyms/genksyms /usr/src/linux-source-<version>/scripts/genksyms/genksyms
#> cp /usr/src/linux-headers-<version>-generic/scripts/mod/modpost /usr/src/linux-source-<version>/scripts/mod/modpost

#> cd /home/<username>/nw802-2.4
#> make clean
#> make

## should compile now ok

#> modprobe usbvideo
#> insmod nw8xx.ko

## this has been tested to work with amsn
## to install ... run ...

#> sudo apt-get install amsn

## HOPE THIS HELPS!
## :)

---

### Post by mahutchinson on 2009-02-17
What does the line with the smiley face in the command mean ?

---

### Post by canadiandude007 on 2009-02-18
It should check out the files, or just go here:

[http://sourceforge.net/project/showfiles.php?group_id=52391](http://sourceforge.net/project/showfiles.php?group_id=52391)

to download the nw802 files needed.

---

