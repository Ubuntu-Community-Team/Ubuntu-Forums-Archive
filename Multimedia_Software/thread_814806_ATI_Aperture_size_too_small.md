---
title: "ATI Aperture size too small"
date: 2008-06-01
forum: Multimedia Software
---

### Post by Ran.Rutenberg on 2008-06-01
Hi,

When I had gutsy, I had 3d acceleration both when using the open and the propriety drivers for my ATI Radeon 9600. Since upgrading to hardy, I can't get the direct rendering to work at all.
When booting, a message about the aperture size is displayed. Looking for aperture in dmesg, I get:

```
$ dmesg | grep -i aperture
[   19.597465] Checking aperture...
[   19.597468] CPU 0: aperture @ e4000000 size 32 MB
[   19.597469] Aperture too small (32 MB)
[   19.597478] Aperture from AGP @ e4000000 size 4096 MB (APSIZE 0)
[   19.597480] Aperture too small (0 MB)
[   19.597481] Your BIOS doesn't leave a aperture memory hole
[   19.636014] Mapping aperture over 65536 KB of RAM @ 4000000
[   20.214066] agpgart: Aperture pointing to RAM
[   20.214110] agpgart: Aperture from AGP @ e4000000 size 4096 MB
[   20.214112] agpgart: Aperture too small (0 MB)
[   20.214151] agpgart: No usable aperture found.
[   20.214190] agpgart: Consider rebooting with iommu=memaper=2 to get a good aperture.
```

I tried booting with iommu=memaper=2, but it did not help.
Trying to change aperture size in the BIOS results in X server not displaying things properly: some parts of the windows on screen are missing. Furthermore, after a couple of minutes the X will completely freeze.

Video card: ATI Radeon 9600 (rv350).
Motherboard: Gigabyte ga-k8nsc-939 nForce3 250Gb

Thanks in advance,
Ran Rutenberg

---

### Post by Ran.Rutenberg on 2008-06-02
Bump...

---

### Post by prshah on 2008-06-03
> **Ran.Rutenberg said:**
> 
```
$ dmesg | grep -i aperture
[   19.597469] Aperture too small (32 MB)
[   19.597478] Aperture from AGP @ e4000000 size 4096 MB (APSIZE 0)
[   19.597480] Aperture too small (0 MB)
[   19.597481] Your BIOS doesn't leave a aperture memory hole
[   19.636014] Mapping aperture over 65536 KB of RAM @ 4000000
[   20.214066] agpgart: Aperture pointing to RAM
[   20.214110] agpgart: Aperture from AGP @ e4000000 size 4096 MB

```

Trying to change aperture size in the BIOS 
Motherboard: Gigabyte ga-k8nsc-939 nForce3 250Gb


I have BIOS aperture size options for only 64Mb and 128Mb... Can't see how you're getting 32Mb.

I also have an option called "BIOS memory hole 15M-16M" which is enabled; maybe you need to find the equivalent option for this on your board?

---

### Post by Ran.Rutenberg on 2008-06-03
> **prshah said:**
> I have BIOS aperture size options for only 64Mb and 128Mb... Can't see how you're getting 32Mb.

I also have an option called "BIOS memory hole 15M-16M" which is enabled; maybe you need to find the equivalent option for this on your board?

As I said, if I set the aperture size to anything but 32Mb X starts to be buggy, and parts of the screen just disappear.

I tried to find the BIOS option you mentioned but I couldn't. I've googled for this option, and I found out it is related to ISA cards which aren't used anymore and therefore I think this option may not be relevant.

Thanks,
Ran Rutenberg

---

