---
title: "Trying to install NVIDIA driver in Xen on feisty"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by azelter on 2007-08-30
I'm currently running Xen 3.0-i386 on an AMD based PC running feisty. 
I am trying to get NVIDIA's driver working on Dom0. I have followed the instructions on [https://help.ubuntu.com/community/XenVirtualMachine/NVidiaOnXenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/NVidiaOnXenOnUbuntuEdgy)

When I do the patch -p1 < ~/patch-nv-1.0-9625-xenrt.txt I get the following output:
patching file nv.c
patching file nv-linux.h
Hunk #1 succeeded at 244 (offset 18 lines).
Hunk #2 succeeded at 776 (offset 42 lines).
Hunk #3 succeeded at 791 (offset 42 lines).
patching file nv-vm.c
Hunk #1 succeeded at 352 with fuzz 1.
Hunk #2 succeeded at 505 (offset -6 lines).
patching file os-agp.c
patching file os-interface.c
Hunk #1 succeeded at 533 (offset 6 lines).
Hunk #2 succeeded at 571 (offset 6 lines).

The patch seems to succeed. However, when I do make I get an error relating to the installer not being able to find my kernel headers. 

uname -a reports kernel 2.6.19-4-generic, however apt-get install linux-headers-$(uname -r) reports: E: Couldn't find package linux-headers-2.6.19-4-generic. This is because the package needed is: xen-headers-2.6.19-4-generic. I have this package installed and as a result the directory /usr/src/xen-headers-2.6.19-4-generic exists.

I can get therefore get around the kernel headers not found error by doing:
make SYSSRC=/usr/src/xen-headers-2.6.19-4-generic
However:
make install SYSSRC=/usr/src/xen-headers-2.6.19-4-generic
gives the following error:
The kernel you are installing for is a Xen kernel!
The NVIDIA driver does not currently work on Xen kernels......
*** Failed Xen sanity check. Bailing out! ***


I have a GeForce4 MX 4000 video card and am trying to install the NVIDIA-Linux-x86-1.0-9639-pkg1 driver from NVIDIA's website.
If anyone has ideas about where I can go from here I would be very grateful.

---

### Post by tseliot on 2007-08-31
try the installer for your kernel at this page:
[http://grizach.sc18.info/nvpatch/](http://grizach.sc18.info/nvpatch/)

---

### Post by azelter on 2007-09-03
Thanks very much for the link. There is no installer for my kernel. The latest Xen kernel available on feisty (with backports enabled) is 2.6.19. Other than compiling my own kernel I'm not sure I can get 2.6.20 or 2.6.21, which is what the patched drivers on the page you pointed me to have been compiled for. I think this page will still be useful, however, as it does have instructions on how do do the job yourself. I will try to follow these and report back...

---

### Post by kwalker on 2007-11-17
I have no need for virtualization and therefore no need for xen.  Somehow I have ended up in gutsy gibbon with a xen version of the kernel and now can't get envy to reinstall the nvidia drivers that worked before as it does not work with xen kernels.  Using adept to remove the linux-xen package didn't get me back to a generic kernel.  Is there a simple way to do that?

---

### Post by kwalker on 2007-11-17
Well, impatience worked ok this time.  I went into Adept (I use kubuntu) and removed a number of packages related to xen, rebooted, and voila, I have a generic kernel again and envy works so that I now have my screen resolution back.

---

