---
title: "Nvidia driver not working with kernel 2.6.35-27"
date: 2011-03-11
forum: Multimedia Software
---

### Post by nbjensen on 2011-03-11
Hi,

I am running the newest Nvidia driver from nvidia.com, version 260.19.44. The built in proprietary Nvidia driver does not work properly.

Recently ubuntu was updated to a newer kernel 2.6.35.27 from 2.6.35.25. Under 2.6.35.25 the driver is working. Under 2.6.35.27 the desktop is not starting, and I can login to a 'console'. After login i try to run startx, and gets some errors. See attached Xorg.0.log.

I am running Ubuntu 10.10.

Any ideas?

Thank you very much.

---

### Post by realzippy on 2011-03-11
*NVIDIA: Failed to load the NVIDIA kernel module*

Reinstall the driver?

---

### Post by nbjensen on 2011-03-11
Did not know reinstalling the driver under the new kernel was needed :) It works now.

Thank you very much!

---

### Post by realzippy on 2011-03-11
Normally reinstalling in case of a kernel update is only necessary when installing the nvidia-driver manually....

---

