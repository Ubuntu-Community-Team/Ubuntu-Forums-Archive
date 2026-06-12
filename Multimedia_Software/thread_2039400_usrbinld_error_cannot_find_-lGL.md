---
title: "/usr/bin/ld: error: cannot find -lGL"
date: 2012-08-08
forum: Multimedia Software
---

### Post by OffTravel on 2012-08-08
Hi, I istalled the fglrx ATI/AMD proprietary driver and now when i try to launch my OpenGL/SDL project i receive this message: **/usr/bin/ld: error: cannot find -lGL**
I have uninstalled the ati driver and I had have the same error with the open driver, so i tryed to reinstall the ati driver and the error persist.

I run Ubuntu 12.04 desktop, 64-bit. HD6870 [ATI Radeon HD 6800 Series]

---

### Post by sghpunk on 2013-01-01
I have the same trouble.
```
$ sudo ln -s /usr/lib/fglrx/libGL.so /usr/lib/libGL.so
```
This helps me.

---

