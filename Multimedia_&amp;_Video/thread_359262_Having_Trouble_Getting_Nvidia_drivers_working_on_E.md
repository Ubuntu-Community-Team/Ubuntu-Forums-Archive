---
title: "Having Trouble Getting Nvidia drivers working on Edgy"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by fatsheep on 2007-02-11
I just upgraded from Dapper to Edgy.  Everything works fine except for the Nvidia drivers.  Vesa drivers work fine but as soon as I install Nvidia drivers, Xserver fails with an error message:

> 
Error: API mismatch: the Nvidia kernel module has version 1.0-8776, this X module has the version 1.0-9629.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

[B]Fatal Server Error: 
No Screens Found[/B]


My graphics card is a Nvidia XFX Geforce 6600 GT (PCI-E) and I'm using method one of this guide to install the drivers: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1).

Any help would be greatly appreciated.

---

### Post by sayhello on 2007-02-11
That problem is to be expected when migrating from Dapper to Edgy. Amongst the changes is a kernel upgrade.

A kernel is what is called the operating system. People (and software vendors) often give this name to the whole package which the kernel is bundled with (UI, utility programs etc...) out of simplicity. The kernel is the piece of software that organizes and distributes hardware resources to other pieces of software.

Drivers, which act as a means of communication between the kernel and any hardware, need more access than regular programs and as such are built as extensions to the kernel, since the kernel is the brain of the OS and has acess everywhere. However, in your case while the drivers cannot be rebuilt since the source code is not open. You need to rebuild a piece of code that allows the kernel to use the driver, which would appear to be out of sync.

The easiest thing I can recommend you to do is to use envy, the script that automatically installs drivers for you and configures everything to work properly.

For installation instructions and download, go here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by chollis888 on 2007-02-13
I had this problem with Dapper, it turned out linux restricted modules has a nvidia driver in it also that caused the conflict

---

