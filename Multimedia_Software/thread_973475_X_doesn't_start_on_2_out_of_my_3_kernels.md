---
title: "X doesn't start on 2 out of my 3 kernels"
date: 2008-11-06
forum: Multimedia Software
---

### Post by AlFrugal on 2008-11-06
I'm new to Ubuntu. I'm running Ubuntu 8.04. I use the nvidia 169.12 driver, installed from the 'restricted' repo.

My GRUB bootloader menu offers the choice of three Ubuntu kernels: 2.6.24-21, 2.6.24-19, and 2.6.24-17.

If I select 2.6.24-17, Ubuntu runs without problem, including Compiz.

If I select either of the other two kernels, X fails to start.

Xorg.O.log shows (EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found).

FWIW, /lib/modules contains folders for 2.6.24-21, 2.6.24-19, and 2.6.24-17 and each of these has an nvidia subfolder.

Why is X not starting on two of my three kernels?

---

