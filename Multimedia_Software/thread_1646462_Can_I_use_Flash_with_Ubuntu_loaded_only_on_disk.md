---
title: "Can I use Flash with Ubuntu loaded only on disk"
date: 2010-12-15
forum: Multimedia Software
---

### Post by donnybb on 2010-12-15
I use a Ubuntu 10.04 disk to boot and run the operating system without a hard drive.
I would like to be able to access websites that use Flash. Is there a way to do that?

---

### Post by efflandt on 2010-12-16
Not without remastering the iso before writing the CD.  Actually I think installing flashplugin-installer would work for the remainder of that CD session, but would be gone the next time you boot.

If you could get a USB memory stick and your PC is capable of booting from USB, you could use Startup Disk Creator to make bootable live/install iso on USB, and could set persistent data to save settings and added programs, like flashplugin-installer or ubuntu-restricted-extras (which includes flash).  You could easily do that with 2 GB USB.

But for iso on USB you should avoid doing updates and cannot install extra video drivers, because things that happen during boot happen before the persistent data is loop mounted.

Or you could do a regular install to USB (flash or hard drive).  8 GB or larger is recommended.  But for regular install you have to make sure that you put grub on the USB (**Advanced** button in screen after you set your user for 10.04 or earlier).  In 10.10 or later grub location is set at bottom of manual partitioning screen.

---

