---
title: "ATI and nVidia cards in same system?"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Ventajou on 2009-08-12
Hi,

My computer has a built-in Radon Xpress 200 which works out of the box in Ubuntu. The only problem is that the DVI output is digital only so I can't use my 2nd monitor.

I am trying to get a PCI GeForce MX4000 to work as a second card without success... The card is detected and I'm even able to install the nvidia driver but Xorg won't load it, whether I try to manually setup xorg.conf to use both cards or only the nvidia.

Does anyone have experience with that?

The Xorg log does mention on the radeon driver that mergefb is not supported or something like that, then right after the nvidia driver gets unloaded.

Oh and I'm running Ubuntu 9.04 64bits if that makes a difference...

Thanks!

---

### Post by markbuntu on 2009-08-12
If you want to use just the nvidia you need to disable the ati in bios. The nvidia driver replaces many files in the x server with proprietary versions that will not work with other drivers so you cannot run both the nvidia and ati driver on the same system at the same time.

---

