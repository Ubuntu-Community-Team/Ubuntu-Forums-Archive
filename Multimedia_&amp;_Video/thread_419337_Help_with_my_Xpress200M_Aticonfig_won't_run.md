---
title: "Help with my Xpress200M: Aticonfig won't run"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by blueknigh7 on 2007-04-22
I had no problems in Dapper or Edgy with my Compaq 2000 with an ATI Xpress 200M Graphics card.  I'm trying to install the latest proprietary drivers in order to run XGL and Beryl.  It worked in Edgy but I'm having a slight issues in Feisty.

I downloaded the latest ATI drivers from their website 8.36.5.  .Followed the instructions at: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) - though modified the package creation to create a feisty .deb

I get to the last step, and run "aticonfig --initial" but it doesn't work.  Here's the dump.

```

$ aticonfig --initial
Uninitialised file found, configuring.
Using xorg.conf
Saved back-up to xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbff5ca97 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7cf5f5b]
aticonfig[0x805bff7]
aticonfig[0x805c2a5]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7ca0ebc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:06 4754090    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:06 4754090    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c7d000-b7c7e000 rw-p b7c7d000 00:00 0 
b7c7e000-b7c80000 r-xp 00000000 03:06 8996104    /lib/tls/i686/cmov/libdl-2.5.so
b7c80000-b7c82000 rw-p 00001000 03:06 8996104    /lib/tls/i686/cmov/libdl-2.5.so
b7c82000-b7c83000 rw-p b7c82000 00:00 0 
b7c83000-b7c87000 r-xp 00000000 03:06 4752645    /usr/lib/libXdmcp.so.6.0.0
b7c87000-b7c88000 rw-p 00003000 03:06 4752645    /usr/lib/libXdmcp.so.6.0.0
b7c88000-b7c8a000 r-xp 00000000 03:06 4752634    /usr/lib/libXau.so.6.0.0
b7c8a000-b7c8b000 rw-p 00001000 03:06 4752634    /usr/lib/libXau.so.6.0.0
b7c8b000-b7dc6000 r-xp 00000000 03:06 8996098    /lib/tls/i686/cmov/libc-2.5.so
b7dc6000-b7dc7000 r--p 0013b000 03:06 8996098    /lib/tls/i686/cmov/libc-2.5.so
b7dc7000-b7dc9000 rw-p 0013c000 03:06 8996098    /lib/tls/i686/cmov/libc-2.5.so
b7dc9000-b7dcc000 rw-p b7dc9000 00:00 0 
b7dcc000-b7df1000 r-xp 00000000 03:06 8996106    /lib/tls/i686/cmov/libm-2.5.so
b7df1000-b7df3000 rw-p 00024000 03:06 8996106    /lib/tls/i686/cmov/libm-2.5.so
b7df3000-b7ee0000 r-xp 00000000 03:06 4752628    /usr/lib/libX11.so.6.2.0
b7ee0000-b7ee4000 rw-p 000ed000 03:06 4752628    /usr/lib/libX11.so.6.2.0
b7ee4000-b7ef1000 r-xp 00000000 03:06 4752649    /usr/lib/libXext.so.6.4.0
b7ef1000-b7ef2000 rw-p 0000d000 03:06 4752649    /usr/lib/libXext.so.6.4.0
b7ef2000-b7ef3000 rw-p b7ef2000 00:00 0 
b7ef3000-b7efa000 r-xp 00000000 03:06 4752671    /usr/lib/libXrender.so.1.3.0
b7efa000-b7efb000 rw-p 00006000 03:06 4752671    /usr/lib/libXrender.so.1.3.0
b7efb000-b7f00000 r-xp 00000000 03:06 4752669    /usr/lib/libXrandr.so.2.1.0
b7f00000-b7f01000 rw-p 00005000 03:06 4752669    /usr/lib/libXrandr.so.2.1.0
b7f01000-b7f0c000 r-xp 00000000 03:06 8962112    /lib/libgcc_s.so.1
b7f0c000-b7f0d000 rw-p 0000a000 03:06 8962112    /lib/libgcc_s.so.1
b7f0d000-b7f10000 rw-p b7f0d000 00:00 0 
b7f10000-b7f29000 r-xp 00000000 03:06 8962069    /lib/ld-2.5.so
b7f29000-b7f2b000 rw-p 00019000 03:06 8962069    /lib/ld-2.5.so
bff48000-bff5e000 rw-p bff48000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Any ideas?  I did some google searches, and it seemed that there was a patch previously to the 2.6.20 kernel because the ATI drivers didn't work.  But the searches also say that the new drivers are supposed to work.

fglxinfo still shows I'm using the Mesa driver - but I supposed that's because I haven't changed my Xorg file yet.  

```
fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

Thanks in advance!

---

### Post by incende on 2007-04-23
I had the same problem and had to add

```
Option      "AIGLX" "Disable"
```

to the Extensions section.

---

