---
title: "nvidia kernel compile failing 2.6.18 (version.h problems)"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by bogler on 2007-01-08
Hi

I have installed the 2.6.18 kernel through an update and i am attempting to build the nvidia kernel  . The NVIDIA file i plan on installing is the  NVIDIA-Linux-x86-1.0-8774-pkg1.run

I have changed $GCC to match ensure that the kernel cpmpiler and the nvidia-kernel compiler are the same and i am experiencing the following error message:

tail nvidia-installer.log
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: The kernel header file '/usr/src/linux-2.6.18/include/linux/version.h'
       does not exist.  The most likely reason for this is that the kernel
       source files in '/usr/src/linux-2.6.18' have not been configured.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

Could someone please let me know why the nvidia kernel compilation is failing?

Thanks in advance

bogler :)

---

### Post by tseliot on 2007-01-08
Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

