---
title: "ndiswrapper-utils-1.9 not installing"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Hexifford on 2009-02-13
Whenever I try to install the .DEB file that I get from the Ubuntu site, it says something about an 'invalid i386 architecture' or something.

Help. Why is this happening.

---

### Post by kevdog on 2009-02-13
Some of the latest kernels broke ndiswrapper, and you need to compile ndiswrapper from source after applying a patch to the source code.  I suspect this might be the case.

Just to confirm, are you sure you need ndiswrapper?  What wireless chipset do you have?

---

### Post by ohgodnotanother1 on 2009-02-13
Execute "uname -m" and see whether the output is i386.
If it's not, you are trying to install a package with the wrong architecture.

---

### Post by Hexifford on 2009-02-13
I figured it out, I just downloaded the AMD64 stuff instead.

---

