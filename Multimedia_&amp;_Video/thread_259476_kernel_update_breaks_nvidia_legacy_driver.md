---
title: "kernel update breaks nvidia legacy driver"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by nicco on 2006-09-17
The nvidia card stopped working after the last kernel update! (using 2.6.15-26-686). I have not changed xorg.conf or anything else.

Xorg.0.log ends with:
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDE000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

If I do "sudo modprobe nvidia", I get:

FATAL: Module nvidia_legacy not found.
FATAL: Module nvidia not found.
FATAL: Error running install command for nvidia

Please help!

---

