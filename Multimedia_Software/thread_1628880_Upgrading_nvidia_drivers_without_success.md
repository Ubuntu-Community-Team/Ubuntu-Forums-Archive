---
title: "Upgrading nvidia drivers without success"
date: 2010-11-23
forum: Multimedia Software
---

### Post by isahlos on 2010-11-23
Hi,

I'm trying to update the drivers to NVIDIA-Linux-x86-260.19.21.run (GeForce GT 220) but ran into several problems. I'm currently running Ubuntu 10.04. 

when running sudo sh NVIDIA-Linux-x86-260.19.21.run /var/log/nvidia-installer.log gives the following errors:


-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (260.19.21) is complete.
-> Searching for conflicting X files:
ERROR: Unable to open '/usr/lib/xorg/modules/libglx.so' for reading (No such
       file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/extensions/libglx.so' for reading
       (No such file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/libglx.so' for reading (No such
       file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/extensions/libglx.so' for reading
       (No such file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/libglx.so' for reading (No such
       file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/extensions/libglx.so' for reading
       (No such file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/libglx.so' for reading (No such
       file or directory)
ERROR: Unable to open '/usr/lib/xorg/modules/extensions/libglx.so' for reading
       (No such file or directory)

Any help appreciated!

---

### Post by efflandt on 2010-11-24
The GT 220 should work with any Ubuntu nvidia-current package in 10.04 or 10.10.  However, the X version changed between 10.04 and 10.10, so I do **not** think that you can simply use 10.10 packages in 10.04.

Issues installing nvidia drivers yourself using the .run file is that you have to blacklist nouveau, and the kernel modules would not be updated automatically during kernel updates or distribution upgrade.  So you may need to redo that after certain system changes.

But there is an easier way.  The x-swat repository has nvidia 260.19.21 for Maverick and Lucid.

Undo whatever you did with nvidia drivers, so you are able to reboot using default nouveau drivers.  Then from a terminal:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
```Then go to System > Administration > Hardware Drivers, "activate" nvidia, and reboot.  It should be as simple as that unless something is lingering from tampering with things.

I had already installed nvidia 260.19.21 in 64-bit 10.10 when I switched from GT 220 to GT 430, and even though the kernel did not recognize a model for the new card, video works great on the GT 430.

HDMI "audio" is another matter.  I believe that requires alsa 1.0.23, which comes with 10.10, but 10.04 has alsa 1.0.22. So I will not try to explain that here.

---

### Post by texla on 2011-01-04
> **efflandt said:**
> 
But there is an easier way.  The x-swat repository has nvidia 260.19.21 for Maverick and Lucid.

Undo whatever you did with nvidia drivers, so you are able to reboot using default nouveau drivers.  Then from a terminal:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
```Then go to System > Administration > Hardware Drivers, "activate" nvidia, and reboot.  It should be as simple as that unless something is lingering from tampering with things.


This worked great on my Maverick 64 bit Nvidia GeForce 8300 - finally looks like it should! ):P

---

