---
title: "Graphics problems after upgrade to Dapper"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by dsjas297 on 2006-07-12
Okay, here's my problem:

After upgrading to Dapper using the iso image of the alternate install cd, I reboot my comp to see how my new Dapper installation runs.

Ubuntu starts up and then X crashes, leaving me with a text login.

I need to fix this problem.

Here is the output from the X log file:

```
(EE) GARTInit: Unable to open /dev/agpgart (No such device)
(EE) I810(0): AGP GART support is not available.  Make sure your kernel has
	agpgart support or that the agpgart kernel module is loaded.
(II) UnloadModule: "i810"
(II) UnloadModule: "ddc"
(II) UnloadModule: "int10"
(II) UnloadModule: "vbe"
(II) UnloadModule: "xaa"
(II) Unloading /usr/lib/xorg/modules/libxaa.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Thanks in advance for any help that I receive.

---

### Post by tseliot on 2006-07-13
Read this:
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

### Post by dsjas297 on 2006-07-13
I tried that before I posted. No luck either way.

Anyways, from the log file, I could see that at least one reason why X is not working could be the fact that it was not loading the agpgart module. However, the module exists in the same place that the log says it doesn't. Also, by using lsmod, I found that the kernel is loading the module.

---

### Post by dsjas297 on 2006-07-13
Problem solved.

After googling around a bit, I added the module intel-agp to the modules.conf file.

Everything appears to be working fine.

---

