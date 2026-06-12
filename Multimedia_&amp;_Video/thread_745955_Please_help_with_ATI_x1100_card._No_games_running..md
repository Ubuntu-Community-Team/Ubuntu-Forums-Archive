---
title: "Please help with ATI x1100 card. No games running."
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by SandmanXC on 2008-04-05
I have an ASUS X51RL laptop that comes with an ATI Radeon x1100 video card. I have enabled the restricted drivers by following the guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

Here are my glxinfo | grep direct and fglrxinfo:

```

$  glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

```

Now, the problem is that i have tons of problems when running 3d games, such as Open Arena, Urban Terror, UT2004. The textures are badly rendered and the fonts are uninteligible. By searching around forums and stuff, I understood that it may be from not having the latest drivers, or anyway a driver issue.

Please advise!

Edit: I have encountered the following problem: 

```

$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfbc99df ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7ced92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c96050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 17498854   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 17498854   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c72000-b7c73000 rw-p b7c72000 00:00 0 
b7c73000-b7c75000 r-xp 00000000 08:01 3343310    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c75000-b7c77000 rw-p 00001000 08:01 3343310    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c77000-b7c78000 rw-p b7c77000 00:00 0 
b7c78000-b7c7c000 r-xp 00000000 08:01 17499443   /usr/lib/libXdmcp.so.6.0.0
b7c7c000-b7c7d000 rw-p 00003000 08:01 17499443   /usr/lib/libXdmcp.so.6.0.0
b7c7d000-b7c7f000 r-xp 00000000 08:01 17499432   /usr/lib/libXau.so.6.0.0
b7c7f000-b7c80000 rw-p 00001000 08:01 17499432   /usr/lib/libXau.so.6.0.0
b7c80000-b7dc4000 r-xp 00000000 08:01 3343307    /lib/tls/i686/cmov/libc-2.6.1.so
b7dc4000-b7dc5000 r--p 00143000 08:01 3343307    /lib/tls/i686/cmov/libc-2.6.1.so
b7dc5000-b7dc7000 rw-p 00144000 08:01 3343307    /lib/tls/i686/cmov/libc-2.6.1.so
b7dc7000-b7dca000 rw-p b7dc7000 00:00 0 
b7dca000-b7ded000 r-xp 00000000 08:01 3343311    /lib/tls/i686/cmov/libm-2.6.1.so
b7ded000-b7def000 rw-p 00023000 08:01 3343311    /lib/tls/i686/cmov/libm-2.6.1.so
b7def000-b7edc000 r-xp 00000000 08:01 17499426   /usr/lib/libX11.so.6.2.0
b7edc000-b7ee0000 rw-p 000ed000 08:01 17499426   /usr/lib/libX11.so.6.2.0
b7ee0000-b7eed000 r-xp 00000000 08:01 17499447   /usr/lib/libXext.so.6.4.0
b7eed000-b7eee000 rw-p 0000d000 08:01 17499447   /usr/lib/libXext.so.6.4.0
b7eee000-b7eef000 rw-p b7eee000 00:00 0 
b7eef000-b7ef6000 r-xp 00000000 08:01 17499469   /usr/lib/libXrender.so.1.3.0
b7ef6000-b7ef7000 rw-p 00006000 08:01 17499469   /usr/lib/libXrender.so.1.3.0
b7ef7000-b7efc000 r-xp 00000000 08:01 17499467   /usr/lib/libXrandr.so.2.1.0
b7efc000-b7efd000 rw-p 00005000 08:01 17499467   /usr/lib/libXrandr.so.2.1.0
b7efd000-b7f07000 r-xp 00000000 08:01 3309635    /lib/libgcc_s.so.1
b7f07000-b7f08000 rw-p 0000a000 08:01 3309635    /lib/libgcc_s.so.1
b7f08000-b7f0b000 rw-p b7f08000 00:00 0 
b7f0b000-b7f25000 r-xp 00000000 08:01 3309581    /lib/ld-2.6.1.so
b7f25000-b7f27000 rw-p 00019000 08:01 3309581    /lib/ld-2.6.1.so
bfbb5000-bfbcb000 rw-p bfbb5000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by SandmanXC on 2008-04-05
bump

---

### Post by SandmanXC on 2008-04-08
bump

---

### Post by X51r-user on 2008-04-20
HI all,

   Just thought i would let you know I have the same laptop and that by using envy I have been able to get graphics up and running.

   I did have to make some corrections to the xorg.conf file to allow video play back ( Option          "TexturedVideo" "off"). 

   I also have been able to install a wifi driver, after two hours of bloody reading tech docs.  (Details of file name = madwifi-nr-r3366+ar5007).

   I only having a glitch when playing games its has a flicker looks more like a refresh problem, needs more research.

   Anyways thought we could help each other out considering with have the same laptop.  Also have you been able to get you synatics pad working.

---

