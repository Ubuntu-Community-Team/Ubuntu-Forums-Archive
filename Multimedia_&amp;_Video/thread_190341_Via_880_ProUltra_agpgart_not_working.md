---
title: "Via 880 Pro/Ultra agpgart not working"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by yota on 2006-06-06
Hi,

I've had some difficulties in getting DRI and 3d acceleration to work on my ati 9600XT on an Asrock 775dual-880pro board, I put here the solution as a reference for other users of Via 880 pro/ultra based motherboards.

Apparently the chipset is not correctly supported in 2.6.15 kernel, but I've found a workaround on these threads:

[http://lists.debian.org/debian-kernel/2006/02/msg00510.html](http://lists.debian.org/debian-kernel/2006/02/msg00510.html)

[http://www.rage3d.com/board/showthread.php?t=33846233](http://www.rage3d.com/board/showthread.php?t=33846233)

I've modified the 
```

#define PCI_DEVICE_ID_VIA_PT880         0x0258

```
in
```

#define PCI_DEVICE_ID_VIA_PT880         0x0308

```
in include/linux/pci_ids.h on the kernel source.

After a kernel recompile everything works perfectly, full 3d and no more xf86_enodev errors.

Someone knows if it's already a known bug? How can I check and eventually file a bug notice? Apparently the kernel 2.6.16.19 of [www.kernel.org](www.kernel.org) still has the old define directive...

Thanks for any advice.

---

### Post by yota on 2006-06-15
The support for via PT880Pro/Ultra will be included in version 2.6.17 of the kernel, as can be seen at this link:

[http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7dd1d9b85cfb63eebf48fa13d3c5d25a3deb3a25](http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7dd1d9b85cfb63eebf48fa13d3c5d25a3deb3a25)

---

### Post by Cuppa-Chino on 2006-09-07
thank you, I have been trying to get my radeon to work for soooooo long... lets see if this works!

---

### Post by Cuppa-Chino on 2006-09-10
well it worked but now I still cannot get the driver to start...

maybe anyone here has an idea... [http://ubuntuforums.org/showpost.php?p=1478453&postcount=305]("http://ubuntuforums.org/showpost.php?p=1478453&postcount=305")

---

### Post by ice9mike on 2006-10-26
Has anybody confirmed if support for the Via PT880 exists in the new Edgy release? I have been trying to get the AGP working on the 64 bit version for sometime with no luck.

ice 9

---

### Post by Cuppa-Chino on 2006-10-26
supposedly the problem should have been fixed in 2.6.17 kernel but I now have a PCI X card and that works okay, sorry I cannot help more

---

