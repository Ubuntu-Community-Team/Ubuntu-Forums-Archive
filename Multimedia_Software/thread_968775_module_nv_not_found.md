---
title: "module nv not found"
date: 2008-11-02
forum: Multimedia Software
---

### Post by dcroxton on 2008-11-02
I just upgraded to Intrepid, and I can't use my nvidia card because the module is not found.

I have a dual-monitor setup, onboard Intel and pci card GeForce2 MX200.  I had the binary nvidia drivers installed (I don't know why; I can't use 3d since the onboard controller doesn't support it).  They aren't supported under the latest kernel, so I uninstalled them.  I have xserver-xorg-video-nv installed, but when I do "sudo modprobe nv," it tells me the module is not found.  In Xorg.0.log.old, the only line with nv in it is the following:

(--) PCI: (0@3:0:0) nVidia Corporation NV11DDR [GeForce2 MX200] rev 178, Mem @ 0xde000000/0, 0xc0000000/0, BIOS @ 0x????????/65536

I'm probably doing something dumb here, as I really don't understand the process, but I do know it has worked fine in the past.  I tried using an older kernel (I'm now on 2.6.24-21-generic), but it hasn't helped.  Any help would be appreciated.

---

