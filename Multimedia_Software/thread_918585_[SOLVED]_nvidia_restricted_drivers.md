---
title: "[SOLVED] nvidia restricted drivers"
date: 2008-09-13
forum: Multimedia Software
---

### Post by wfp on 2008-09-13
Just received a new computer, and put ubuntu on it everythings great but trying to enable nvidia accelerated driver and it looks like it's trying to download 2 files but getting this errror message > W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

---

### Post by wfp on 2008-09-13
Please help i got the nvida accelerated driver enabled was useing old kernal, but now i can not change screen resolution it stuck on 640+480 how can i change it.

---

### Post by xc3RnbFO8P on 2008-09-13
First try this:
atl+f2
gksudo displayconfig-gtk
see if your monitor is on that list.
If not:
Choose Generic
and resolution that your monitor supports

---

### Post by wfp on 2008-09-13
Dude you Rock thank you very much it worked my monitor was not on the list so chose generic and set the settings. Thanks

---

