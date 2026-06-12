---
title: "/dev/fb0, where art thou?"
date: 2009-06-21
forum: Multimedia Software
---

### Post by jgauthier on 2009-06-21
Hey all,

    Seems like I am missing a /dev/fb0.  I DO have a /dev/.static/dev/fb0, however, it appears unusable.

 fbset -fb /dev/.static/dev/fb0
open /dev/.static/dev/fb0: No such device

I'm missing something.  I'm not sure what!  My framebuffer experience is a bit on the weak side.

I have attempted the following:
* Added vga=791 to grub (anyway to confirm?)
* Added Option "fbdev" "/dev/fb0" (X11.log said "no thanks")
* Verified vesafb is loaded as a module

I am not sure where to continue, and my searches have resulted in one of these.  Suggestions?

Thanks very much!

---

