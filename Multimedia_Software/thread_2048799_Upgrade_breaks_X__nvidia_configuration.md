---
title: "Upgrade breaks X : nvidia configuration"
date: 2012-08-27
forum: Multimedia Software
---

### Post by spillemw on 2012-08-27
Upgraded from Lucid.  All seems to work fine, except X (error message "failed to load session ubuntu").  I have now nailed it down to an nvidia issue (at least i think so).
In dmesg I get :

[   26.475527] NVRM: The NVIDIA GeForce FX 5200 GPU installed in this system is
[   26.475537] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers. Please
[   26.475540] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[   26.475543] NVRM:  information.  The 295.49 NVIDIA driver will ignore
[   26.475545] NVRM:  this GPU.  Continuing probe...
[   26.475559] NVRM: No NVIDIA graphics adapter found!
[   26.952656] ppdev: user-space parallel port driver
[   28.672808] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.672840] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   28.682921] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.35  Thu May 31 12:00:16 PDT 2012

As you can see I have downloaded and installed the legacy drivers that the system is asking for, but without any change.  I assume this may be because the probe for the graphics card comes before the nvidia driver is loaded.
I have tried removing everything nvidia and just reinstall the legacy driver, but that didnt work either.

It worked fine on Lucid by the way.  Dont understand why the upgrade should break this.  Not enough backwards comp testing I guess.

Any suggestions?

---

