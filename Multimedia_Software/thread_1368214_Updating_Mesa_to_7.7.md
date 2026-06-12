---
title: "Updating Mesa to 7.7"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Azrael3000 on 2009-12-30
Hi,

I'm running Karmic and want to update Mesa to 7.7 since I have problems with Blender. However at the end of ./configure I get the following:

```

        prefix:          /usr/local
        exec_prefix:     ${prefix}
        libdir:          ${exec_prefix}/lib
        includedir:      ${prefix}/include

        Driver:          dri
        OSMesa:          no
        DRI drivers:     i810 i915 i965 mach64 mga r128 r200 r300 r600 radeon savage sis tdfx unichrome ffb swrast
        DRI driver dir:  ${libdir}/dri
        Use XCB:         no

        Gallium:         yes
        Gallium dirs:    auxiliary drivers state_trackers
        Winsys dirs:      drm
        Winsys drm dirs:
        Auxiliary dirs:  rbug draw translate cso_cache pipebuffer tgsi sct rtasm util indices vl
        Driver dirs:     softpipe failover trace identity svga i915
        Trackers dirs:   dri egl xorg

        Shared libs:     yes
        Static libs:     no
        EGL:             yes
        GLU:             yes
        GLw:             yes (Motif: no)
        glut:            no
        Demos:           no

        CFLAGS:          -g -O2 -Wall -Wmissing-prototypes -std=c99 -ffast-math -fno-strict-aliasing -fPIC
        CXXFLAGS:        -g -O2 -Wall -fno-strict-aliasing -fPIC
        Macros:          -D_GNU_SOURCE -DPTHREADS -DHAVE_POSIX_MEMALIGN -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM

```

After doing make I get in lib/

```

$ ls -l
total 205084
-rwxr-xr-x 1 *** ***    22281 2009-12-30 17:24 demodriver.so
-rwxr-xr-x 1 *** *** 12426110 2009-12-30 17:24 ffb_dri.so
-rwxr-xr-x 1 *** *** 12151028 2009-12-30 17:19 i810_dri.so
-rwxr-xr-x 1 *** *** 14340812 2009-12-30 17:19 i915_dri.so
-rwxr-xr-x 1 *** *** 16478746 2009-12-30 17:20 i965_dri.so
lrwxrwxrwx 1 *** ***       11 2009-12-30 17:24 libEGL.so -> libEGL.so.1
lrwxrwxrwx 1 *** ***       13 2009-12-30 17:24 libEGL.so.1 -> libEGL.so.1.0
-rwxr-xr-x 1 *** ***   212653 2009-12-30 17:24 libEGL.so.1.0
lrwxrwxrwx 1 *** ***       10 2009-12-30 17:16 libGL.so -> libGL.so.1
lrwxrwxrwx 1 *** ***       12 2009-12-30 17:16 libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x 1 *** ***  2047087 2009-12-30 17:16 libGL.so.1.2
lrwxrwxrwx 1 *** ***       11 2009-12-30 17:24 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 *** ***       20 2009-12-30 17:24 libGLU.so.1 -> libGLU.so.1.3.070700
-rwxr-xr-x 1 *** ***  1633058 2009-12-30 17:24 libGLU.so.1.3.070700
lrwxrwxrwx 1 *** ***       11 2009-12-30 17:24 libGLw.so -> libGLw.so.1
lrwxrwxrwx 1 *** ***       15 2009-12-30 17:24 libGLw.so.1 -> libGLw.so.1.0.0
-rwxr-xr-x 1 *** ***    36875 2009-12-30 17:24 libGLw.so.1.0.0
-rwxr-xr-x 1 *** *** 12303312 2009-12-30 17:20 mach64_dri.so
-rwxr-xr-x 1 *** *** 12477329 2009-12-30 17:21 mga_dri.so
-rwxr-xr-x 1 *** *** 12152840 2009-12-30 17:21 r128_dri.so
-rwxr-xr-x 1 *** *** 13262125 2009-12-30 17:21 r200_dri.so
-rwxr-xr-x 1 *** *** 13432410 2009-12-30 17:22 r300_dri.so
-rwxr-xr-x 1 *** *** 13555752 2009-12-30 17:22 r600_dri.so
-rwxr-xr-x 1 *** *** 13052974 2009-12-30 17:22 radeon_dri.so
-rwxr-xr-x 1 *** *** 12191501 2009-12-30 17:23 savage_dri.so
-rwxr-xr-x 1 *** *** 12454945 2009-12-30 17:23 sis_dri.so
-rwxr-xr-x 1 *** *** 11157025 2009-12-30 17:24 swrast_dri.so
-rwxr-xr-x 1 *** *** 12415863 2009-12-30 17:23 tdfx_dri.so
-rwxr-xr-x 1 *** *** 12084493 2009-12-30 17:23 unichrome_dri.so

```

As you can see I don't get the libOSMesa libraries. Is there anything I'm doing wrong?

Thanks in advance,
Arno

____________

Edit: Classical rtfm (closely). No ./configure needed.

---

### Post by dr_gap on 2010-01-17
> **Azrael3000 said:**
> Hi,


Edit: Classical rtfm (closely). No ./configure needed.

Could you elaborate?

---

### Post by Azrael3000 on 2010-01-17
Sure. Installation is also described here: [http://www.mesa3d.org/install.html](http://www.mesa3d.org/install.html)

Mesa has a few built in configurations, so you would only do something like
```
 $ make linux-x86
```

If you only enter
```
 $ make
```
then you'll see a list of available configuration and you should choose whatever fits your architecture.

Of course to finish up you need to do
```
 $ sudo make install 
```

Feel free to ask if you have any further questions.

BR
Arno

---

### Post by woop11 on 2010-01-26
Hi

i tried to compile mesa 7.7 today on 9.10 and it says i need libdrm >= 2.4.15. How can i get the dev packages for those (or make them from source)? (The repositories only have 2.4.14)

---

### Post by Azrael3000 on 2010-01-26
do you have xserver-xorg-dev installed? I installed 2.4.16 so I don't know about 2.4.17.

---

### Post by woop11 on 2010-01-26
sorry, i think i must have seen (the version) wrong because i just ran ./configure again and it worked this time. sadly diddnt help my cause but thanks anyway ;)

---

### Post by Yellow Pasque on 2010-01-26
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by adam814 on 2010-01-26
> **Temüjin said:**
> [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

+1

Much easier than building from source.  My only word of caution is that you may end up with a DRM version not matching the in-kernel one and need to upgrade your kernel (but you'd have ended up with that installing from source anyway).

---

