---
title: "mplayer segmentation fault"
date: 2008-12-17
forum: Multimedia Software
---

### Post by NickD-NLUG on 2008-12-17
The subject says it all really, any time I start mplayer I get a segmentation fault:

username@hostname:~$ mplayer
Segmentation fault

These are the last entries from strace:

open("/dev/zero", O_RDWR)               = 3
mmap(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|0x40, 3, 0) = 0x41adf000
close(3)                                = 0
getpid()                                = 13933
getpid()                                = 13933
getpid()                                = 13933
getpid()                                = 13933
arch_prctl(ARCH_GET_FS, [0x7fe585f437a0]) = 0
futex(0x7fe598045738, FUTEX_WAKE, 2147483647) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 13933 detached

Operating system is:

Linux war 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

Video card is:

nVidia Corporation GeForce 8500 GT (rev a1)

Any ideas on what could be causing this?  Or further steps to take in order to diagnose the problem?

---

### Post by ironslave on 2008-12-27
you might want to try reinstalling your video card drivers, Segmentation faults are usually caused by that with ATI cards, i am not sure about Nvidia though

---

### Post by NickD-NLUG on 2009-02-07
> **ironslave said:**
> you might want to try reinstalling your video card drivers, Segmentation faults are usually caused by that with ATI cards, i am not sure about Nvidia though

Fixing a problem that stopped me being able to use glx has fixed this :)

[http://ubuntuforums.org/showthread.php?t=1021484](http://ubuntuforums.org/showthread.php?t=1021484)

---

