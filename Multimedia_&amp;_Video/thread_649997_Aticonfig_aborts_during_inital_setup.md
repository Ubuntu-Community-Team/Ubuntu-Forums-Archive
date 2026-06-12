---
title: "Aticonfig aborts during inital setup"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by nessin on 2007-12-25
I'm trying to get the ATI fglrx driver on 7.10.  Following the Gusty install guide on the wiki I had no problem getting the driver downloaded, but when I run the aticonfig --initial command I get the following output:

```

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd549e5 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d0292b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cab050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:02 68324      /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:02 68324      /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c71000-b7c7b000 r-xp 00000000 08:02 2188       /lib/libgcc_s.so.1
b7c7b000-b7c7c000 rw-p 0000a000 08:02 2188       /lib/libgcc_s.so.1
b7c87000-b7c88000 rw-p b7c87000 00:00 0 
b7c88000-b7c8a000 r-xp 00000000 08:02 5554       /lib/tls/i686/cmov/libdl-2.6.1.so
b7c8a000-b7c8c000 rw-p 00001000 08:02 5554       /lib/tls/i686/cmov/libdl-2.6.1.so
b7c8c000-b7c8d000 rw-p b7c8c000 00:00 0 
b7c8d000-b7c91000 r-xp 00000000 08:02 7422       /usr/lib/libXdmcp.so.6.0.0
b7c91000-b7c92000 rw-p 00003000 08:02 7422       /usr/lib/libXdmcp.so.6.0.0
b7c92000-b7c94000 r-xp 00000000 08:02 7411       /usr/lib/libXau.so.6.0.0
b7c94000-b7c95000 rw-p 00001000 08:02 7411       /usr/lib/libXau.so.6.0.0
b7c95000-b7dd9000 r-xp 00000000 08:02 5548       /lib/tls/i686/cmov/libc-2.6.1.so
b7dd9000-b7dda000 r--p 00143000 08:02 5548       /lib/tls/i686/cmov/libc-2.6.1.so
b7dda000-b7ddc000 rw-p 00144000 08:02 5548       /lib/tls/i686/cmov/libc-2.6.1.so
b7ddc000-b7ddf000 rw-p b7ddc000 00:00 0 
b7ddf000-b7e02000 r-xp 00000000 08:02 5556       /lib/tls/i686/cmov/libm-2.6.1.so
b7e02000-b7e04000 rw-p 00023000 08:02 5556       /lib/tls/i686/cmov/libm-2.6.1.so
b7e04000-b7ef1000 r-xp 00000000 08:02 7405       /usr/lib/libX11.so.6.2.0
b7ef1000-b7ef5000 rw-p 000ed000 08:02 7405       /usr/lib/libX11.so.6.2.0
b7ef5000-b7f02000 r-xp 00000000 08:02 7426       /usr/lib/libXext.so.6.4.0
b7f02000-b7f03000 rw-p 0000d000 08:02 7426       /usr/lib/libXext.so.6.4.0
b7f03000-b7f04000 rw-p b7f03000 00:00 0 
b7f04000-b7f0b000 r-xp 00000000 08:02 7448       /usr/lib/libXrender.so.1.3.0
b7f0b000-b7f0c000 rw-p 00006000 08:02 7448       /usr/lib/libXrender.so.1.3.0
b7f0c000-b7f11000 r-xp 00000000 08:02 7446       /usr/lib/libXrandr.so.2.1.0
b7f11000-b7f12000 rw-p 00005000 08:02 7446       /usr/lib/libXrandr.so.2.1.0
b7f1c000-b7f1f000 rw-p b7f1c000 00:00 0 
b7f1f000-b7f39000 r-xp 00000000 08:02 2141       /lib/ld-2.6.1.so
b7f39000-b7f3b000 rw-p 00019000 08:02 2141       /lib/ld-2.6.1.so
bfd40000-bfd56000 rw-p bfd40000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Using 7.10 with a ATI Radeon HD2900 card.  Also, the ATI driver doesn't show up in the Restricted Drivers Manager, which I'm assuming means the driver isn't there, but when I do an apt-get it says it is installed.

---

