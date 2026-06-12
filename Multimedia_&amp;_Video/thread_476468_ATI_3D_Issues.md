---
title: "ATI 3D Issues"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by Norst on 2007-06-17
Hi all, I'm very new to Ubuntu (and Linux in general) but I'm a pretty smart guy and know how to solve most issues on my own by searching the net and reading, but I'm a tad stuck here.

I've read and tried all of the common ATI install tutorials and seem to have done everything right. The drivers install and all expected things get loaded as far as I can tell. Except for the 3D part. When checking my Xorg.0.log to see why glrxinfo still reports the Mesa indirect I see this:

```
(II) fglrx(0): [pci] find AGP GART
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7c09000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

so I read somewhere to check that AGPGART it's being loaded with lsmod, I see the line:

```
agpgart                35400  2 fglrx,intel_agp
```

So here is where I'm stuck. 

Some info:
Motherboard is an ASUS P4GBX
Card is a ATI 9800XT
Did full build of ATI drivers and followed install tutorial for Feisty and all went well with no errors

If there is any info that would aid in solving this info please let me know and I will provide it as soon as possible.

Any help in finding a solution to this issue is greatly appreciated.

Norst

---

### Post by Norst on 2007-06-17
UPDATE:

ok it seems the issue is more with the intel-agp.ko module than the driver. There's a section here:

[http://www2.ati.com/drivers/linux/linux_8.12.10.html](http://www2.ati.com/drivers/linux/linux_8.12.10.html)

that mentions the ```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
``` error.

It states the following:

> This information applies to the following system configurations:

    * Linux kernel version 2.6.x
    * Any ATI Linux driver 

A blank screen may appear momentarily when X starts to load. The following error message (or similar) may appear on the text console or in /var/log/XFree86.0.log:
(EE) fglrx(0): [agp] unable to acquire AGP, error ""xf86_ENODEV""xf86_ENODEV""

This is not a problem with the display driver.

Version 2.6 kernels require a second kernel module in addition to agpgart, which should be named similar to the manufacturer of your motherboard AGP chipset. This error message should occur if the other agp module is not loaded.

This issue can be worked around as follows:

   1. First make sure that agpgart is loading properly.
   2. To find out which AGP controller your motherboard uses, issue the following command: lspci | grep AGP
   3. To find a list of AGP related kernel modules installed on your machine, issue the following command and look for a module (*.ko file) that suits your AGP Controller: ls /lib/modules/`uname -r`/kernel/drivers/char/agp
   4. Use the modprobe command (as root) to load the module. For example: On a motherboard using a VIA® AGP Controller, you would load the via-agp.ko using modprobe as follows (notice that the trailing .ko is omitted): modprobe via-agp

Check the modprobe manpage for more information on loading kernel modules.

   5. To verify that the AGP module is already loaded, run lsmod as root. With the X server running and the connection established, the usage count of this module must be greater than zero. 

If you cannot find a suitable agp module for your motherboard, then you may want to upgrade to the latest version of the Linux kernel, or check your motherboard manufacturer's website for more information.


so I do a sudo lsmod and see the line:
```

intel_agp              25244  0
```

I note that it's usage is 0. I try the ```
modprobe intel-agp
``` but nothing really seems to happen or change.

---

### Post by Kubunteando on 2007-06-17
Check this:

[http://ubuntuforums.org/showthread.php?p=2612364#post2612364](http://ubuntuforums.org/showthread.php?p=2612364#post2612364)

A similar thing was solved in:
[http://bbs.archlinux.org/viewtopic.php?pid=166921](http://bbs.archlinux.org/viewtopic.php?pid=166921)

But the distribution seems not to be Unbuntu, so you will need to find where is the proper configuration file...

---

