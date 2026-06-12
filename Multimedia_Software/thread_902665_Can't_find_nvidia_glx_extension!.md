---
title: "Can't find nvidia glx extension?!?"
date: 2008-08-27
forum: Multimedia Software
---

### Post by slanbarn on 2008-08-27
Yeah...

Ubuntu 8.04.1 nvidia driver 177.67 beta driver from nvidias site...

I installed the driver, and edited my xorg.conf to use the nvidia module... Reboot, and the system claims it cant find the nvidia glx extension, I can reinstall the driver and start gdm again, and everything works until next reboot...

Why is this? Where come this behaviour from? 

```

ls -l /usr/lib/xorg/modules/extensions
-rw-r--r-- 1 root root   24098 2008-06-13 03:26 libdbe.so
-rw-r--r-- 1 root root   49124 2008-06-13 03:26 libdri.so
-rw-r--r-- 1 root root  168062 2008-06-13 03:26 libextmod.so
lrwxrwxrwx 1 root root      16 2008-08-27 20:42 libglx.so -> libglx.so.177.67
-rwxr-xr-x 1 root root 1730576 2008-08-27 20:42 libglx.so.177.67
-rw-r--r-- 1 root root   34399 2008-06-13 03:26 librecord.so
-rw-r--r-- 1 root root   51923 2008-06-13 03:26 libxtrap.so

```

This is after a reboot, and reinstalled driver the module and symlink is there! But somehow during a reboot, the system is unable to find it?!?

---

