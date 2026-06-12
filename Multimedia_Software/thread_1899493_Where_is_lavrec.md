---
title: "Where is lavrec"
date: 2011-12-23
forum: Multimedia Software
---

### Post by gareththered on 2011-12-23
Hello everyone!

Does anyone know where lavrec has gone?  I've install the mjpegtools package on Oneiric but it is not in there.  The 'man' page for lavrec is there, but not the executable itself!

I've also searched 'packages.ubuntu.com' but it doesn't come up there neither.

Any ideas?

Thanks in advance.

---

### Post by gareththered on 2011-12-24
I think I can answer my own post here.  It might be useful for someone else.

mjpegtools doesn't support v4l2 as yet and the original v4l (without the 2) has been removed from the kernel.  This means that mjpegtools compiles without v4l support meaning no 'lavrec'.

---

