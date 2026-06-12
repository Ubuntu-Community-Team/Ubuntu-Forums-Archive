---
title: "HD DVD Playback / Extract - No AACS Keys"
date: 2010-06-28
forum: Multimedia Software
---

### Post by Suicidal State Machine on 2010-06-28
Hi, I'm trying to playback some HD DVDs using an external drive (the Xbox 360 USB drive). I'm following the guide here:

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I can launch the dumphd GUI but it doesn't read the disc as it reports "Loading aacskeys library... Failed". I've tried to install aacskeys-0.4.0c but I get the following error when I run make:


[~/applications/aacskeys-0.4.0c]
>> make "CONFIG=Debug" all
==== Building aacskeys ====
aacskeys.cpp
aacs_aes.cpp
aacs_ecdsa.cpp
cmac.cpp
cmac_aes.cpp
ioctl.cpp
src/ioctl.cpp: In member function ‘int Drive::resolvePath(const char*, char*, size_t)’:
src/ioctl.cpp:966: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:966: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:981: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:981: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:989: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:989: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:998: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:998: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:1005: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:1005: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:1016: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:1016: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:1024: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:1024: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:1034: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:1034: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:1046: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:1046: error: ‘fprintf’ was not declared in this scope
src/ioctl.cpp:1050: error: ‘stderr’ was not declared in this scope
src/ioctl.cpp:1050: error: ‘fprintf’ was not declared in this scope
make[1]: *** [obj/linux/Debug/ioctl.o] Error 1
make: *** [aacskeys] Error 2

Looks like it's missing an include file(?).  

Is there an easier way to do this?

---

### Post by Suicidal State Machine on 2010-07-03
I just realized that even though I was try to access the disc via dumpHD, even playback from the drive it's self doesn't work. Are there commercial SW players that will handle HD-DVD/BlueRay? I'm actually willing to pay for a solution at this point!

---

### Post by aglc2005 on 2010-09-13
> **Suicidal State Machine said:**
> I just realized that even though I was try to access the disc via dumpHD, even playback from the drive it's self doesn't work. Are there commercial SW players that will handle HD-DVD/BlueRay? I'm actually willing to pay for a solution at this point!

Have you found any solution to this? I am looking into trying to get the HD-DVD stuff going. I noticed that the /media/*HD-DVD NAME* folder is empty here.

---

