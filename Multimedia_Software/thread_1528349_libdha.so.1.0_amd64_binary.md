---
title: "libdha.so.1.0 amd64 binary"
date: 2010-07-10
forum: Multimedia Software
---

### Post by bubulescu on 2010-07-10
Hello,

 For the past few days I have been struggling to compile libdha provided by MPlayer, without success. Mainly because of complaining about missing asm/processor.h and a few others, with solutions varying from vaguely elegant to bigger hammer's brute-force. Whatever the course, the result(s) spelled "failure" to me so, now, I am about to lose weight by hair removal.
 What I want is to be able to use (x)vidix video driver, call it a whim, if you like, but it's not entirely true; the main reason is comparison for a permanent decision. At this point, I have svgalib.ko loaded and working, but no libdha. As a normal user I get
```
[nvidia_vid] Error occurred during pci scan: Operation not permitted

```
and if I try to search (pg_up, for example), MPlayer simply crashes. As root, I can run mplayer with xvidix(:nvidia or not), but all I get is a green area where the movie is suposed to be. I can hear sound, I can search, I get a nice
```

[nvidia_vid] Found chip: NV43 [GeForce 6600 PCIe]
libdha: DHA kernelhelper failed: No such file or directory
[nvidia_vid] arch 40 register base 0x7fdbb1b0a000
libdha: DHA kernelhelper failed: No such file or directory
[nvidia_vid] detected memory size 256 MB
[nvidia_vid] MTRR set up
[nvidia_vid] video mode: 1680x1050@32

```
but that's it.

 So, here's my question: does anyone have libdha.so.1.0 as a binary and willing to share it? (since compiling seems to be unavailable for me).
 Here's the result of `uname -a`:
```

Linux suis 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

```


Hopeful regards,
Vlad.

---

### Post by bubulescu on 2010-07-11
Anyone?

---

### Post by bubulescu on 2010-07-12
...no one?

---

### Post by bubulescu on 2010-07-16
...at least, does anyone know how to generate/copy/etc asm/processor.h, asm/cache.h and asm/system.h so I can compile the d**n thing?

 I have the sources, headers, everything, ran <make mrproper prepare modules_prepare headers_install> on both headers-only and full source (from apt-get); I did a full cleanup, even purged them and reinstalled them, same commands, nothing; I even built the kernel and installed it, nothing, even tried <make all> with oldconfig and defconfig, nothing. Everything I said was done multiple times.

I tried with 'touch', with symlink from arch/x86/include/asm/... and symlinks of the needed files from there, nothing; I relinked /usr/include/asm to point to arch/x86/include/asm, still nothing (it doesn't matter if it's an error or other, it will not work).

Nothing I do will get those header files in asm/. Is it even possible to compile libdha? If the sources are old/deprecated, why aren't they removed? Google didn't help, either, the closest result I got said to compile and install the kernel, the files would then be generated automatically. I did, it doesn't.


Isn't there anyone that knows something about libdha.so?!

---

### Post by bubulescu on 2010-07-22
I found an rpm with the binary, brute-copied it, and got as much as seeing the green window. The output is still the same. Today, after an update for some xorg libraries, after reboot, the -v option revealed these lines:
```

vidixlib: PROBING: nvidia
[nvidia_vid] Can't find chip
vidixlib: No suitable driver can be found.

```

It still makes me wonder why it showed them before but, now, at least, it's clear that my chip isn't supported. 

So, -vo gl:force-pbo:yuv=2:nomanyfmts:levelconv=0 will have to do, still. I'll mark this thread as [SOLVED].


Regards,
Vlad.

---

