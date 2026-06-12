---
title: "n600 wireless dual band usb adapter (No idea how to get it working)"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by VeeroRith on 2012-11-02
Ok, so first off, I have been learning how to get linux running for a grand total of one day. . .  This morning. . .
I just barely managed to get Ubuntu 12.10 installed on my computer about 2 hours ago, and was trying to get the drivers for the N600 wireless adapter by Netgear, and I found what looked like proper driver files from googling about.  I extracted the tar.gz, and found the folders - 
lib
src
and a makefile

Upon looking up how to install said stuff, I was told to do a ./configure to make sure it is. .  well . .  configured.
And it says
./Configure: No such file or directory

Also, just using make gives me this tasty mess of confusing stuff.

```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build m=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
Wireless Extension is the only possible API for this kernel version 
Using Wireless Extension API
  LD      /home/tyler/downloads/Brdcmdrvr/build-in.o
  CC [M]  /home/tyler/downloads/Brdcmdrvr/src/shared/linux_osl.o
  CC [M]  /home/tyler/downloads/Brdcmdrvr/src/wl/sys/wl_linux.o
/home/tyler/downloads/Brdcmdrvr/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: no such file or directory
compilation terminated.
make [2]: ***[/home/tyler/downloads/Brdcmdrvr/src/wl/sys/wl_linux.o]Error 1
make [1]: *** [_module_/home/tyler/downloads/brdcmdrvr] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.o-17-generic'
make: *** [all] Error 2

```

Also, just so you know, I cannot get said ubuntu system wired to the internet.  It is downstairs, router is upstairs, thats a long freaking ethernet cable XD

If anyone could point me in the right direction of the correct driver, and how to install it let me know

Another note, that code i had to type out on my windows pc that i have next to the ubuntu, so caps may not be so accurate.  plus I have to transfer any files or patches over on a cd.  if that makes any difference. 

Thanks, 
Tyler

---

### Post by chili555 on 2012-11-02
> Another note, that code i had to type out on my windows pc that i have next to the ubuntu, so caps may not be so accurate. plus I have to transfer any files or patches over on a cd. if that makes any difference. Perfect. If you can do that, we can get this going. First, let's verify exactly what you have. Please insert the device and then run and post:```
lsusb
```Thanks.

---

