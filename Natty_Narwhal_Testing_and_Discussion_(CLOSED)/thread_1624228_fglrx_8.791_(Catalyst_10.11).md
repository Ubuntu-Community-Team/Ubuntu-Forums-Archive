---
title: "fglrx 8.791 (Catalyst 10.11)"
date: 2010-11-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-11-17
OK. Procedure looks to be the same as for 10.10, so I've updated [that thread](http://ubuntuforums.org/showthread.php?p=10084147).

Catalyst 10.11 has just been released:

[Page](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
[Direct link](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-11-x86.x86_64.run)

More information to come. Release notes not available yet...

OK. Downloaded and trying a plain 

$ ./ati-driver-installer-10-11-x86.x86_64.run --buildpkg Ubuntu/natty

Generated. Install? Why not.

Nope. dkms won't build, it'll need to be patched. Tsk, ioctl again!

---

