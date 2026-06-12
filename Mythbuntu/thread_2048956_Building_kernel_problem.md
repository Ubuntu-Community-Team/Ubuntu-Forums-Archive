---
title: "Building kernel problem"
date: 2012-08-27
forum: Mythbuntu
---

### Post by raptorjr on 2012-08-27
I upgraded to 12.04 yesterday, and it has kernel 3.2.0-29-generic.
I need to patch the kernel and rebuild it. I'm following a guide and everything seems to go fine until i do this command:

make-kpkg --rootcmd fakeroot --initrd kernel_image kernel_headers modules_image

It is supposed to make two packages, linux-image and linux-headers.
The problem is that the packages that is built is version 3.2.0-24, and not 3.2.0-29. Why? I want the same version that i already have, just with the patch.

What am i doing wrong?

/Stefan

---

