---
title: "Triple Boot"
date: 2008-11-13
forum: Mac OSX
---

### Post by ticknubbs on 2008-11-13
I have a machine with 8.10 and Xp on it. I would really like to install OS X on it as well so I can actually use it. However, I cannot part with these other two OS's. Is there a way to install OS X and triple boot? I also have an external HD. Should I install OS X on that instead? I will also need some assistance in the route that I am directed. Thanks for any input. ~Nick

---

### Post by bashveank on 2008-11-13
If it's a Mac then you can.... I believe that you have to install OS X before any of the other OSes though...

---

### Post by handy on 2008-11-14
I think the easy (only?) way out (if you don't want to reinstall your existing OS's) is to use your external drive for OS X.

***[Edit:]** My answer is only appropriate to people running Apple hardware.*

---

### Post by bashveank on 2008-11-14
> **handy said:**
> I think the easy (only?) way out (if you don't want to reinstall your existing OS's) is to use your external drive for OS X.

It may not appear on the bootloader then though. I don't know for sure, I haven't tried installing OS X after other OSes, but that's my suspicion.

---

### Post by handy on 2008-11-14
> **bashveank said:**
> It may not appear on the bootloader then though. I don't know for sure, I haven't tried installing OS X after other OSes, but that's my suspicion.

I'm pretty sure that it must be installed first on the internal drive.

I'm quite sure it will work fine on an external drive though.

***[Edit:]** Again, this answer is only appropriate to those using an Apple computer.*

---

### Post by leeners on 2008-11-24
Hi,

Go to [www.intuitive.com.There](www.intuitive.com.There) is an feature by Dave Taylor called The Business Blog; look for an article entitled: "Ubuntu Linux, Yellowdog Linux and Mac OS X, all on one PowerBook?"where he featured how to set up a triple boot system using Ubuntu, Yellowdog Linux and OS X on a Powerbook." Hope this helps.

---

### Post by handy on 2008-11-25
I think you could easily have OS X, windows, & lots of Linux distro's on any of the EFI Macs, you just have to be careful how you use the first four partitions, e.g.

**sda1**: = 200Mb - is a reserved EFI file system, which you don't touch unless you really know what you are doing.

**sda2**: = ? size - partition allocated for OS X.

**sda3**: = ? size - partition for windows.

**sda4**: = ? size - partition allocated to a distro', or being solely a /boot partition, either way GRUB is installed & can be configured to call a variety of drive & partition combinations with distro's, BSD's or any other OS that can be loaded via GRUB.

OS X can not see more than these 4 partitions, so windows & GRUB need to be on partitions 3 &/or 4, if /swap is used it needs to be on a partition > or = to 5, rather than wasting one of the valuable earlier partition numbers.

I haven't bothered installing lots of distro's on my iMac as I just dual boot Leopard & Arch, & have another PC which is setup for testing.

For anyone interested in more details on this stuff, I created a wiki article incorporating it over here:

***_[http://wiki.archlinux.org/index.php/IMac_Aluminium](http://wiki.archlinux.org/index.php/IMac_Aluminium)_***

---

### Post by EnGorDiaz on 2008-11-25
well if you want to check out my thread in the sig

---

### Post by handy on 2008-11-25
> **EnGorDiaz said:**
> well if you want to check out my thread in the sig

Well done, great thread for the non-Apple hardware people, which of course answers the OP more than my posts have in this thread. :-)

---

