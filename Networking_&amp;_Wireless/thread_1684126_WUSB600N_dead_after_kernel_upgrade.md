---
title: "WUSB600N dead after kernel upgrade"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by WA1DH on 2011-02-08
I hate kernel upgrades, at least on my laptop. Every time I upgrade, I have to recompile the driver for my Linksys WUSB600N adapter or it doesn't work. Usually, this is no problem, as I have the driver saved in a .tar file and all I have to do is 'make' and 'make install' and it works.

BUT...

This time, I tried that, and I get this:
```
doug@dh-laptop:~/LOCAL/Software/RT3572_Linux_STA_v2.4.0.2$ make
make -C tools
make[1]: Entering directory `/home/doug/LOCAL/Software/RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/doug/LOCAL/Software/RT3572_Linux_STA_v2.4.0.2/tools'
/home/doug/LOCAL/Software/RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/doug/LOCAL/Software/RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/doug/LOCAL/Software/RT3572_Linux_STA_v2.4.0.2/os/linux modules
make: *** /lib/modules/2.6.35-25-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
```

So...  my saved driver file no longer works.

Any ideas?

Thanks.

---

### Post by chili555 on 2011-02-08
Do you have the kernel headers installed?```
sudo apt-get install linux-headers-generic
```I'd suggest you do 'make clean' first:```
sudo su
make clean
make
make install
exit
```

---

### Post by WA1DH on 2011-02-08
> **chili555 said:**
> Do you have the kernel headers installed?```
sudo apt-get install linux-headers-generic
```

This made it work.

Could you explain to me what this did? I assume the old headers (with which it previously worked) were deleted when the new headers were installed, and this restored them(?)

Much thanks.

---

### Post by chili555 on 2011-02-08
Kernel headers along with build tools are required to compile from scratch. Sometimes people make the mistake of installing solely the headers for their then running kernel only instead of the meta-package linux-headers-generic which automatically updates the headers every time a new kernel or, in Ubuntu-speak, linux image is installed by update. I am guessing you were one of those.

You got an updated kernel but no headers. Installing the -generic package will also install corresponding headers from now on.

Good luck and post back if we can help you further.

---

