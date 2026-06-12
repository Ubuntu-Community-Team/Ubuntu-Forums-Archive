---
title: "gcc error when installing nForce drivers..."
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by Punio4 on 2006-06-16
Ok... tried installing the nForce drivers following all guides here on the forums.
Got all the packages i needed: the kernel source, the 3.4 gcc whatever...

And no matter what i type:

CC=/usr/bin/gcc-3.4 && export CC 
export CC=gcc-3.4 
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc

Tried everything... it still says
> 
You appear to be compiling the NVIDIA kernel module with a different compiler than the one that was used to compile the running kernel. This may be fine, but there are cases where this can lead to instability. The compiler used to compile the kernel was gcc 4.0; the current compiler is gcc 3.4.

What should I do?

---

