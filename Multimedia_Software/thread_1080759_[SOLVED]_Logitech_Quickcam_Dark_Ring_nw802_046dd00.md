---
title: "[SOLVED] Logitech Quickcam Dark Ring nw802 046d:d001"
date: 2009-02-25
forum: Multimedia Software
---

### Post by jls_legalize on 2009-02-25
reading this thread: [http://ubuntuforums.org/showthread.php?t=621240&highlight=nw8xx&page=2]("http://ubuntuforums.org/showthread.php?t=621240&highlight=nw8xx&page=2")
and this other [https://dev.openwrt.org/browser/trunk/package/nw802-2.4/patches/100-compile_fix.patch?rev=12180]("https://dev.openwrt.org/browser/trunk/package/nw802-2.4/patches/100-compile_fix.patch?rev=12180")

I managed to get the webcam working with cheese and xawtv, does not work with skype and ekiga

#> sudo su
#> wget [http://dslitalia.bravehost.com/nw802-2.4.tar.gz](http://dslitalia.bravehost.com/nw802-2.4.tar.gz)
#> tar xzvf nw802-2.4.tar.gz 
## will create folder called nw802-2.4

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

#> tar xjf /usr/src/linux-source-2.6.27.tar.bz2
#> cd /home/<username>/nw802-2.4

## will need to change <username> to whichever name you logged on with

#> apt-get install module-assistant
#> m-a update,prepare

## might need to press Y to continue

#> cd /usr/src/linux-source-2.6.27
#> make oldconfig && make prepare
#> cp /usr/src/linux-headers-2.6.27-14-generic/Module.symvers /usr/src/linux-source-2.6.27/Module.symvers
#> cp /usr/src/linux-headers-2.6.27-14-generic/scripts/genksyms/genksyms /usr/src/linux-source-2.6.27/scripts/genksyms/genksyms
#> cp /usr/src/linux-headers-2.6.27-14-generic/scripts/mod/modpost /usr/src/linux-source-2.6.27/scripts/mod/modpost

#> cd /home/<username>/nw802-2.4

#> make clean
#> make

## should compile now ok

#> modprobe usbvideo
#> insmod nw8xx.ko

## Check with running

#> dmesg | more

## Should see details of Webcam now installed


legalize cannabis, coke, ero

---

### Post by mikilion on 2009-05-08
Hi,
I have this problem to make:

```

ln -sf /usr/src/linux-source-2.6.28/drivers/media/video/usbvideo/usbvideo.h .
ln -sf /usr/src/linux-source-2.6.28/drivers/media/video/usbvideo/usbvideo.c .
make -C /usr/src/linux-source-2.6.28/ SUBDIRS=`pwd` modules
make[1]: ingresso nella directory «/usr/src/linux-source-2.6.28»
  CC [M]  ~/nw802-2.4/nw8xx_jpgl.o
~/nw802-2.4/nw8xx_jpgl.c:114:33: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
~/nw802-2.4/nw8xx_jpgl.c:524:52: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c: In function ‘jpgl_processFrame’:
~/nw802-2.4/nw8xx_jpgl.c:524: error: ‘clamp’ undeclared (first use in this function)
~/nw802-2.4/nw8xx_jpgl.c:524: error: (Each undeclared identifier is reported only once
~/nw802-2.4/nw8xx_jpgl.c:524: error: for each function it appears in.)
~/nw802-2.4/nw8xx_jpgl.c:525:52: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:526:52: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:527:52: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:530:46: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:533:46: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:599:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:600:65: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:601:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:612:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:613:65: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:614:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:625:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:626:65: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:627:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:638:49: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:639:65: error: macro "clamp" requires 3 arguments, but only 1 given
~/nw802-2.4/nw8xx_jpgl.c:640:49: error: macro "clamp" requires 3 arguments, but only 1 given
make[2]: *** [~/nw802-2.4/nw8xx_jpgl.o] Errore 1
make[1]: *** [_module_~/nw802-2.4] Errore 2
make[1]: uscita dalla directory «/usr/src/linux-source-2.6.28»
make: *** [default] Errore 2

```

---

### Post by mikilion on 2009-05-12
I solved by applying patch "100-compile_fix.patch"

---

