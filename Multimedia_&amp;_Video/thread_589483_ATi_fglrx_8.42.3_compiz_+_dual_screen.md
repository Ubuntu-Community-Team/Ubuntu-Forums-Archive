---
title: "ATi fglrx 8.42.3 compiz + dual screen?"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Ferrat on 2007-10-24
Anyone gotten dual screen to work with compiz on with 8.42.3 driver?

My second screen keeps sending out backtrace when running fglrxinfo and compiz wont work, with just one screen it works great

---

### Post by happycampers on 2007-10-25
Same here on OpenSuse 10.2.  I get a stack trace when trying to start an OpenGL app on screen[1] or when querying (fglrxinfo / glxinfo) with the second monitor connected.  This didn't seem to happen for me under the pseudo dual-screen big-desktop option, but I run into other problems with that setup (artifacts in the corners, 2nd display refused to run at native resolution and runs at 4:3 stretched / squished.  Oh, and I had to manually move / symlink the Mesa libGL entries in /usr/lib to get openGL to work at all.  I get the artifacts / watermark corruption in the LR corner / mouse cursor described in many posts, but it seems much less frequent on 8.42 and I didn't get it to happen at all when running with AIGLX enabled (now if i could just get that to work in dual-head mode). On the upside, compositing works (at least in single-head mode), as does AIGLX.  Compositing without AIGLX is too slow to be of any use.  With AIGLX, it is better and, as phoronix advertised, seems to have little impact on 3D app performance (at least beyond the memory hit).  fgl_glxgears framerate went from around 320 to around 520.  Doom3 is more playable now at 800x600 / High than previously at 640x480 / Medium. Trying to run video with compositing enabled works, but clips other windows / menus, with or without video or openGL overlay enabled.  Here is the output of fglrxinfo on my box:

dhawkins@dadsdell:~> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release

*** glibc detected *** fglrxinfo: double free or corruption (top): 0x08915540 ***
======= Backtrace: =========
/lib/libc.so.6[0xb7c446e1]
/lib/libc.so.6(cfree+0x89)[0xb7c45d79]
/usr/X11R6/lib/modules/dri/fglrx_dri.so[0xb78f1c92]
/usr/lib/libGL.so.1[0xb7e69c61]
/usr/lib/libX11.so.6(_XFreeExtData+0x25)[0xb7d3b965]
/usr/lib/libX11.so.6(_XFreeDisplayStructure+0x2f6)[0xb7d47ca6]
/usr/lib/libX11.so.6(XCloseDisplay+0xea)[0xb7d339fa]
fglrxinfo[0x8048a3b]
/lib/libc.so.6(__libc_start_main+0xdc)[0xb7bf5f9c]
fglrxinfo[0x80488f1]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:02 5552929    /usr/bin/fglrxinfo
0804b000-0804c000 rw-p 00002000 08:02 5552929    /usr/bin/fglrxinfo
0804c000-08936000 rw-p 0804c000 00:00 0          [heap]
a5812000-a5813000 rw-p a5812000 00:00 0
a5e3c000-a5e3e000 rw-s 00002000 00:0e 11575      /dev/dri/card0
a5e3e000-ade3e000 rw-s 00003000 00:0e 11575      /dev/dri/card0
ade3e000-ae4f1000 rw-p ade3e000 00:00 0
ae4f1000-aebf1000 rw-s 00005000 00:0e 11575      /dev/dri/card0
b6a00000-b6a21000 rw-p b6a00000 00:00 0
b6a21000-b6b00000 ---p b6a21000 00:00 0
b6bbe000-b6bc8000 r-xp 00000000 08:02 4578623    /lib/libgcc_s.so.1
b6bc8000-b6bca000 rw-p 00009000 08:02 4578623    /lib/libgcc_s.so.1
b6bf1000-b6c15000 r-xp 00000000 08:02 4578587    /lib/libm-2.5.so
b6c15000-b6c17000 rw-p 00023000 08:02 4578587    /lib/libm-2.5.so
b6c17000-b6c1e000 r-xp 00000000 08:02 4578609    /lib/librt-2.5.so
b6c1e000-b6c20000 rw-p 00006000 08:02 4578609    /lib/librt-2.5.so
b6c20000-b79d9000 r-xp 00000000 08:02 5774342    /usr/lib/dri/fglrx_dri.so
b79d9000-b7a5e000 rw-p 00db9000 08:02 5774342    /usr/lib/dri/fglrx_dri.so
b7a5e000-b7bb9000 rw-p b7a5e000 00:00 0
b7bb9000-b7bbb000 r-xp 00000000 08:02 4578585    /lib/libdl-2.5.so
b7bbb000-b7bbd000 rw-p 00001000 08:02 4578585    /lib/libdl-2.5.so
b7bbd000-b7bc1000 r-xp 00000000 08:02 5547273    /usr/lib/libXdmcp.so.6.0.0
b7bc1000-b7bc3000 rw-p 00003000 08:02 5547273    /usr/lib/libXdmcp.so.6.0.0
b7bc3000-b7bc5000 r-xp 00000000 08:02 5547271    /usr/lib/libXau.so.6.0.0
b7bc5000-b7bc7000 rw-p 00001000 08:02 5547271    /usr/lib/libXau.so.6.0.0
b7bc7000-b7bdb000 r-xp 00000000 08:02 4578605    /lib/libpthread-2.5.so
b7bdb000-b7bdd000 rw-p 00013000 08:02 4578605    /lib/libpthread-2.5.so
b7bdd000-b7be0000 rw-p b7bdd000 00:00 0
b7be0000-b7d08000 r-xp 00000000 08:02 4578579    /lib/libc-2.5.so
b7d08000-b7d09000 r--p 00128000 08:02 4578579    /lib/libc-2.5.so
b7d09000-b7d0b000 rw-p 00129000 08:02 4578579    /lib/libc-2.5.so
b7d0b000-b7d0e000 rw-p b7d0b000 00:00 0
b7d0e000-b7d1b000 r-xp 00000000 08:02 5549115    /usr/lib/libXext.so.6.4.0
b7d1b000-b7d1d000 rw-p 0000c000 08:02 5549115    /usr/lib/libXext.so.6.4.0
b7d1d000-b7e35000 r-xp 00000000 08:02 5548672    /usr/lib/libX11.so.6.2.0
b7e35000-b7e39000 rw-p 00118000 08:02 5548672    /usr/lib/libX11.so.6.2.0
b7e39000-b7e3a000 rw-p b7e39000 00:00 0
b7e3a000-b7ec0000 r-xp 00000000 08:02 5552939    /usr/X11R6/lib/libGL.so.1.2
b7ec0000-b7ec2000 rw-p 00086000 08:02 5552939    /usr/X11R6/lib/libGL.so.1.2
b7ec2000-b7ec4000 rw-p b7ec2000 00:00 0
b7ec8000-b7ed4000 rwxp b7ec8000 00:00 0
b7ed9000-b7ee9000 rw-s 00004000 00:0e 11575      /dev/dri/card0
b7eeb000-b7eec000 rw-p b7eeb000 00:00 0
b7eec000-b7eed000 r-xp b7eec000 00:00 0          [vdso]
b7eed000-b7f08000 r-xp 00000000 08:02 4578572    /lib/ld-2.5.so
b7f08000-b7f0a000 rw-p 0001a000 08:02 4578572    /lib/ld-2.5.so
bff77000-bff8c000 rwxp bff77000 00:00 0          [stack]
bff8c000-bff8d000 rw-p bff8c000 00:00 0
Aborted

---

### Post by kikislater on 2007-11-20
Same problem ! :confused::mad:](*,):frown:
Ati sucks

---

### Post by dark_harmonics on 2007-12-09
I have now officially run into every problem you can run into with installing ATI. I also have this problem :(

---

