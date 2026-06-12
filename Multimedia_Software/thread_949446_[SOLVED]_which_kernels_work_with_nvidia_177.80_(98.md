---
title: "[SOLVED] which kernels work with nvidia 177.80? (9800 gt)"
date: 2008-10-16
forum: Multimedia Software
---

### Post by jyaan on 2008-10-16
I just got an ASUS 9800 gt ultimate, and installed the 177.80 driver manually from the nvidia site (*not* available from envy(ng) or otherwise)

It works fine after installing the driver, yet after restart (or even just shutdown and turn it on), gdm starts in low res. If I reinstall I get normal operation, but the issue persists on restart as usual. This means I have to go through this install every time I turn on my computer.

This has apparently been identified as a kernel issue; unfortunately don't have the specifics. Neither 2.6.24-19 nor 2.6.24.21 (both generic) have worked for me.


I would appreciate listings of any kernels (or solutions) working with 177.80 driver and nvidia 9800. Thank you.

---

### Post by psypher on 2008-10-16
check here for some help and the solution that worked for me:
[http://ubuntuforums.org/showthread.php?t=909460&page=2](http://ubuntuforums.org/showthread.php?t=909460&page=2)

---

### Post by jyaan on 2008-10-17
thanks for the redirect. i tried blacklisting nv and nvidia_new as suggested, but vesa is coming up at 800x600 still with the 'hardware cannot be detected' message. im going to move over to that thread, anyways.

---

### Post by jyaan on 2008-10-17
the kernel was not the problem, as erroneously mentioned (and believed by me =P) in one of the threads. i solved it by disabling both nv and nvidia_new in /etc/default/linux-restricted-modules-common and removing /etc/init.d/nvidia-kernel.

---

