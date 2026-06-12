---
title: "gspca_build and WebCams"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by phil79 on 2006-11-29
Can someone please help ??

I am trying to install "gspcav1-20060925"  :

ubuntu:/tmp/gspcav1-20060925> ls
changelog  Etoms/        gspca.h     Mars-Semi/  Sunplus/       utils/
Conexant/  gspca_build*  kgspca.err  Pixart/     Sunplus-jpeg/  Vimicro/
decoder/   gspca_core.c  Makefile*   Sonix/      Transvision/
ubuntu:/tmp/gspcav1-20060925>
ubuntu:/tmp/gspcav1-20060925> sudo ./gspca_build

 FATAL you need to install the Kernel Source for your running kernel
ubuntu:/tmp/gspcav1-20060925>


Errrr.......     ](*,) 

Thanks.

---

### Post by KingBahamut on 2006-11-29
Have to install source or kernel headers first. 

sudo apt-get install linux-headers-`uname -r` I believe should do it. 

Also be sure you have build essential installed 

sudo apt-get install build-essential

---

### Post by phil79 on 2006-12-02
Thanks for reply...installed them, seemed to work.

So I ran "gspca_build" an it seems to crash...

If I look at:

ubuntu:/tmp/gspcav1-20060925> more kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/tmp/gspcav1-20060925 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /tmp/gspcav1-20060925/gspca_core.o
  CC [M]  /tmp/gspcav1-20060925/decoder/gspcadecoder.o
  LD [M]  /tmp/gspcav1-20060925/gspca.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/gspcav1-20060925/gspca.mod.o
  LD [M]  /tmp/gspcav1-20060925/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'

---

### Post by dowgoldratio7 on 2007-05-05
First post, and 3 days into linux... I tried sudo ./gspca_build and got the same error as phil79: (I'm using gspcav1-20070426 if that makes any difference here)

 FATAL you need to install the Kernel Source for your running kernel

I then tried

sudo apt-get install linux-headers-`uname -r`

And I got this:


sudo apt-get install linux-headers-2.6.15-28-386
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-28
The following NEW packages will be installed:
  linux-headers-2.6.15-28 linux-headers-2.6.15-28-386
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 7763kB of archives.
After unpacking 79.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-28 2.6.15-28.53 [6907kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-28-386 2.6.15-28.53 [856kB]
Fetched 7763kB in 17s (448kB/s)
Selecting previously deselected package linux-headers-2.6.15-28.
(Reading database ... 77697 files and directories currently installed.)
Unpacking linux-headers-2.6.15-28 (from .../linux-headers-2.6.15-28_2.6.15-28.53_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-28-386.
Unpacking linux-headers-2.6.15-28-386 (from .../linux-headers-2.6.15-28-386_2.6.15-28.53_i386.deb) ...
Setting up linux-headers-2.6.15-28 (2.6.15-28.53) ...

Setting up linux-headers-2.6.15-28-386 (2.6.15-28.53) ...


So it appears to me that command worked. But I get the same error after:

sudo ./gspca_build
 
 FATAL you need to install the Kernel Source for your running kernel

Is there something else I need to do? Thanks in advance for any suggestions.

---

### Post by dowgoldratio7 on 2007-05-06
I came back to see what I missed... Turns out I hadn't installed the build-essential package
So I did this as well:

sudo apt-get install build-essential

And it seemed to work. Thanks, KingBahamut!

---

