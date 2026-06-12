---
title: "VirtualBox don't start machines"
date: 2011-01-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-01-06
Since a few kernel updates I can't start a virtual machine anymore (Windows XP, Ubuntu). I get the following error message:

```
The virtual machine 'Ubuntu 32 Bit' has terminated unexpectedly during startup because of signal 9.
```
As I remember I got during the starting of the host system (64 Bit) the error message that vboxdrv couldn't be loaded. There are even lot of lines of error messages from VirtualBox. A "modprobe vboxdrv" doesn't finish. It seems it's in an infinite loop then.

I downgraded my system some times ago to maverick and there was VirtualBox working without problems.

---

### Post by pressureman on 2011-01-06
VirtualBox hasn't worked at all since kernel package 2.6.37-9 (which I fortunately still have on my box for when I need to run VirtualBox.

I remember reading somewhere that something in the Ubuntu sauce (patches they apply to the vanilla kernel) is incompatible with VirtualBox 3.

You could try installing VirtualBox 4 maybe... [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by erkiha on 2011-01-06
Virtualbox 4.0 works perfectly with 2.6.37 kernels.

---

### Post by jfernyhough on 2011-01-06
I started a thread about this and marked it as solved. Searching is a good idea.

[http://ubuntuforums.org/showthread.php?t=1648132](http://ubuntuforums.org/showthread.php?t=1648132)

Basically the Ubuntu kernel is built with an option that the VirtualBox kernel drivers don't like, hence the virtual machines refuse to start. If you install a mainline kernel build it works fine.

The kernel setting VB doesn't like is: CONFIG_DEBUG_SET_MODULE_RONX=y 

I'm not sure if this has changed in recent builds; I've been using mainline since that thread to work around this problem.

---

### Post by Sworddragon on 2011-01-06
> **jfernyhough said:**
> I started a thread about this and marked it as solved. Searching is a good idea.

I have searched on "Virtual Box". Well, "VirtualBox" was better :P

---

### Post by jfernyhough on 2011-01-06
You called it VirtualBox in the thread title. ;)

But it happens. :)

---

### Post by Sworddragon on 2011-01-06
Thread title != searching :P

Dunno why I used "Virtual Box" because I'm calling it every time "VirtualBox". Today the kernel 2.6.37-12 is out but the flag hasn't changed. I will wait until the Ubuntu kernel has solved this problem.

---

