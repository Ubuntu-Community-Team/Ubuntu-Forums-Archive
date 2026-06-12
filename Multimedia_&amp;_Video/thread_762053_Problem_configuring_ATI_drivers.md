---
title: "Problem configuring ATI drivers"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by Klaasvaak on 2008-04-21
k probeer mijn ATI drivers te configureren, maar alle aticonfig opdrachten die ik intik eindigen op Aborted (core dumped)
Een voorbeeld is:
I'm trying to configure my ATI drivers, but when I type an aticonfig code it always ends with "aborted (core dumped)
For example:

```


maarten@Fifi:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-6
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf8319de ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d4692b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cef050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:03 1781244    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:03 1781244    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ccb000-b7ccc000 rw-p b7ccb000 00:00 0 
b7ccc000-b7cce000 r-xp 00000000 03:03 995544     /lib/tls/i686/cmov/libdl-2.6.1.so
b7cce000-b7cd0000 rw-p 00001000 03:03 995544     /lib/tls/i686/cmov/libdl-2.6.1.so
b7cd0000-b7cd4000 r-xp 00000000 03:03 1783045    /usr/lib/libXdmcp.so.6.0.0
b7cd4000-b7cd5000 rw-p 00003000 03:03 1783045    /usr/lib/libXdmcp.so.6.0.0
b7cd5000-b7cd7000 r-xp 00000000 03:03 1783043    /usr/lib/libXau.so.6.0.0
b7cd7000-b7cd8000 rw-p 00001000 03:03 1783043    /usr/lib/libXau.so.6.0.0
b7cd8000-b7cd9000 rw-p b7cd8000 00:00 0 
b7cd9000-b7e1d000 r-xp 00000000 03:03 995541     /lib/tls/i686/cmov/libc-2.6.1.so
b7e1d000-b7e1e000 r--p 00143000 03:03 995541     /lib/tls/i686/cmov/libc-2.6.1.so
b7e1e000-b7e20000 rw-p 00144000 03:03 995541     /lib/tls/i686/cmov/libc-2.6.1.so
b7e20000-b7e23000 rw-p b7e20000 00:00 0 
b7e23000-b7e46000 r-xp 00000000 03:03 995545     /lib/tls/i686/cmov/libm-2.6.1.so
b7e46000-b7e48000 rw-p 00023000 03:03 995545     /lib/tls/i686/cmov/libm-2.6.1.so
b7e48000-b7f35000 r-xp 00000000 03:03 1783047    /usr/lib/libX11.so.6.2.0
b7f35000-b7f39000 rw-p 000ed000 03:03 1783047    /usr/lib/libX11.so.6.2.0
b7f39000-b7f46000 r-xp 00000000 03:03 1783049    /usr/lib/libXext.so.6.4.0
b7f46000-b7f47000 rw-p 0000d000 03:03 1783049    /usr/lib/libXext.so.6.4.0
b7f47000-b7f4e000 r-xp 00000000 03:03 1783110    /usr/lib/libXrender.so.1.3.0
b7f4e000-b7f4f000 rw-p 00006000 03:03 1783110    /usr/lib/libXrender.so.1.3.0
b7f4f000-b7f54000 r-xp 00000000 03:03 1783211    /usr/lib/libXrandr.so.2.1.0
b7f54000-b7f55000 rw-p 00005000 03:03 1783211    /usr/lib/libXrandr.so.2.1.0
b7f55000-b7f56000 rw-p b7f55000 00:00 0 
b7f59000-b7f63000 r-xp 00000000 03:03 995534     /lib/libgcc_s.so.1
b7f63000-b7f64000 rw-p 0000a000 03:03 995534     /lib/libgcc_s.so.1
b7f64000-b7f66000 rw-p b7f64000 00:00 0 
b7f66000-b7f80000 r-xp 00000000 03:03 995530     /lib/ld-2.6.1.so
b7f80000-b7f82000 rw-p 00019000 03:03 995530     /lib/ld-2.6.1.so
bf81d000-bf832000 rw-p bf81d000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Does anybody know what I can do about this?

---

### Post by theone85ca on 2008-04-23
hey im in the same boat, let me know if you fix it!

---

### Post by entropyjones on 2008-04-24
I am having the same issue. ATI Radeon X300. Should I post my xorg.conf?

---

### Post by fcmartins on 2008-06-27
Your xorg.conf file is probably corrupted. Try regenerating a new one with dpkg-reconfigure xserver-xorg.

---

