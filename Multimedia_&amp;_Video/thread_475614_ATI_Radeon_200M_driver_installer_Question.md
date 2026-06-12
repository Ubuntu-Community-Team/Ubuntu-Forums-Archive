---
title: "ATI Radeon 200M driver installer Question"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by euler_fan on 2007-06-16
Hello:

I am trying to install the driver for my video card. ```
glxinfo | grep rendering
``` says I do not have direct rendering.

I read some posts about installing similar drivers, and tried to patch them together as follows:

I went to the ATI website, found my driver install package, downloaded it, ran it (no errors reported) in automatic insall mode (as opposed to make custom packages mode), and

and did as follows, getting the errors reported:

```
jqmcclintic@jqmcclintic-laptop:~/Desktop$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf934a03 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb7db7b4a]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7d668cc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:04 1722122    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:04 1722122    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7d43000-b7d45000 rw-p b7d43000 00:00 0 
b7d45000-b7d47000 r-xp 00000000 03:04 3014679    /lib/tls/i686/cmov/libdl-2.4.so
b7d47000-b7d49000 rw-p 00001000 03:04 3014679    /lib/tls/i686/cmov/libdl-2.4.so
b7d49000-b7d4d000 r-xp 00000000 03:04 1721754    /usr/lib/libXdmcp.so.6.0.0
b7d4d000-b7d4e000 rw-p 00003000 03:04 1721754    /usr/lib/libXdmcp.so.6.0.0
b7d4e000-b7d50000 r-xp 00000000 03:04 1721693    /usr/lib/libXau.so.6.0.0
b7d50000-b7d51000 rw-p 00001000 03:04 1721693    /usr/lib/libXau.so.6.0.0
b7d51000-b7e7e000 r-xp 00000000 03:04 3014676    /lib/tls/i686/cmov/libc-2.4.so
b7e7e000-b7e80000 r--p 0012c000 03:04 3014676    /lib/tls/i686/cmov/libc-2.4.so
b7e80000-b7e82000 rw-p 0012e000 03:04 3014676    /lib/tls/i686/cmov/libc-2.4.so
b7e82000-b7e85000 rw-p b7e82000 00:00 0 
b7e85000-b7ea9000 r-xp 00000000 03:04 3014680    /lib/tls/i686/cmov/libm-2.4.so
b7ea9000-b7eab000 rw-p 00023000 03:04 3014680    /lib/tls/i686/cmov/libm-2.4.so
b7eab000-b7f71000 r-xp 00000000 03:04 1722096    /usr/lib/libX11.so.6.2.0
b7f71000-b7f74000 rw-p 000c5000 03:04 1722096    /usr/lib/libX11.so.6.2.0
b7f74000-b7f75000 rw-p b7f74000 00:00 0 
b7f75000-b7f81000 r-xp 00000000 03:04 1721559    /usr/lib/libXext.so.6.4.0
b7f81000-b7f82000 rw-p 0000c000 03:04 1721559    /usr/lib/libXext.so.6.4.0
b7f82000-b7f89000 r-xp 00000000 03:04 1721251    /usr/lib/libXrender.so.1.3.0
b7f89000-b7f8a000 rw-p 00006000 03:04 1721251    /usr/lib/libXrender.so.1.3.0
b7f8a000-b7f8c000 r-xp 00000000 03:04 1721411    /usr/lib/libXrandr.so.2.0.0
b7f8c000-b7f8d000 rw-p 00002000 03:04 1721411    /usr/lib/libXrandr.so.2.0.0
b7f93000-b7f9d000 r-xp 00000000 03:04 2981912    /lib/libgcc_s.so.1
b7f9d000-b7f9e000 rw-p 00009000 03:04 2981912    /lib/libgcc_s.so.1
b7f9e000-b7fa1000 rw-p b7f9e000 00:00 0 
b7fa1000-b7fba000 r-xp 00000000 03:04 2982013    /lib/ld-2.4.so
b7fba000-b7fbc000 rw-p 00018000 03:04 2982013    /lib/ld-2.4.so
bf920000-bf935000 rw-p bf920000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

I'm wondering what happened and if anyone can help me work around it.

Thanks in advance.

---

