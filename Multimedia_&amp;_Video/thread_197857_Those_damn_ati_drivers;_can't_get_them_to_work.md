---
title: "Those damn ati drivers; can't get them to work"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by rutgerw on 2006-06-16
After I did a fresh install (via alternate install-cd) I tried via various ways to get my ati card working (for direct rendering).

I tried to install the driver via adept. I followed BinaryDriverHowto/Ati @ ubuntu wiki
  -fglrxinfo: couldn't find RGB GLX visual
Then I tried the drivers provided by Ati (version 8.25.18) (method 2 in the link provided in the Ubuntu wiki)
  -fglrxinfo: couldn't find RGB GLX visual
The I thought maybe I'm missing some GLX modules in my kernel. Dowloaded latest kernel from kernel.org, used my Slackware .config (same machine) and compiled it. I have managed several times without much difficulty to get the driver working on Slackware. I used the Ati-provided driver to try to compile the kernel modules... But no luck, they weren't getting compiled.

Then I tried an old version from the Ati website (8.24.8) to generate Ubuntu packages. You guessed it, the output from fglrxinfo was: Couldn't find RGB GLX visual.

Oh and yes, I have the driver (fglrx) in my xorg.conf, and 2D seems to be working fine.

Can anybody see what I'm doing wrong here? I'm new to Ubunutu, but I have several years of experience with Slackware Linux.

---

### Post by Galban on 2006-06-16
try this: [http://ubuntuforums.org/showthread.php?t=197471]("http://ubuntuforums.org/showthread.php?t=197471")

---

### Post by rutgerw on 2006-06-16
Tried this aswell, but I couldn't find the libGL.1.2.so in the extracted files or elsewere on my system... Nor could I modprobe agpgart.

Not being able to modprobe agpgart seems rather strange to me. I'm using the stock ubuntu kernel. I can not imagine that they did not enable the agpgart module. Perhaps they did not include this in a module, but build in the kernel itself??

---

### Post by rutgerw on 2006-06-18
Well I finally found the module in the ati driverpackage (version 8.24.8 ). Named libGL.so.1.2 instead of libGL.1.2.so (both names are mentioned is this thread: [http://ubuntuforums.org/showthread.php?t=197471)](http://ubuntuforums.org/showthread.php?t=197471)). But I still get a error message Error: couldn't find RGB GLX visual! I noticed that dmesg is reporting unknown symbols, fglrx: Unknown symbol no_iommu. So I recon it has something to do with the kernel that came with Ubuntu, which is not compatibel with the fglrx driver. But this also means that the driver is not loaded into the kernel while I do have a X session running, and the driver in xorg.conf is the fglrx driver. The Xorg.0.log states: 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

The make things even more strange there is also no /dev/dri/card0 (should be present when having a graphics card capable if direct rendering??)

Any thoughts, anyone??

---

### Post by flapane on 2006-06-18
same problem here, I attach my log and PLUS I have the /dev/dri/card0

flapane@a64:~$ dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 921 MBytes.
[fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
flapane@a64:~$

---

### Post by flapane on 2006-06-22
bump

---

### Post by saif on 2006-07-28
Hello, the subject says it all! :)

my laptop has the ati xpress 200m card, I have struggled a lot to get 3d to work, with no luck, on
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
it said that the new fglrx drivers don't support 3d, and that I should revert to an older driver, unfortunatly i still get the same error with dmesg
"fglrx: Unknown symbol no_iommu" if any1 has any clue how to get around this, I would really appreciate it!

---

### Post by Jaxilian on 2006-07-28
> **saif said:**
> Hello, the subject says it all! :)

my laptop has the ati xpress 200m card, I have struggled a lot to get 3d to work, with no luck, on
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
it said that the new fglrx drivers don't support 3d, and that I should revert to an older driver, unfortunatly i still get the same error with dmesg
"fglrx: Unknown symbol no_iommu" if any1 has any clue how to get around this, I would really appreciate it!


delete /usr/lib/libGL.so.1.2 first and replace it with the older one described in the guide you were trying.

---

### Post by saif on 2006-07-29
> 
delete /usr/lib/libGL.so.1.2 first and replace it with the older one described in the guide you were trying.

I assumed I don't need to do this, since I am using the 8.24 drivers, but I gave it a try, now instead of the no RGB extension i used to get with fglrx, i get *error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory*
and the same error in dmesg | grep fglex :  *fglrx: Unknown symbol no_iommu *

---

