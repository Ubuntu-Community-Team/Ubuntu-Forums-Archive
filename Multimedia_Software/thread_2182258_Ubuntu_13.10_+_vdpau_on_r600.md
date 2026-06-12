---
title: "Ubuntu 13.10 + vdpau on r600"
date: 2013-10-20
forum: Multimedia Software
---

### Post by fioan89 on 2013-10-20
Hi!

I've recently installed Ubuntu 13.10. Since it came with linux kernel 3.11 and mesa 9.2 the first three things that I tried to do were:
1. Enable dynamic power management for my HD 4570 (radeon.dpm=1)
2. Enable the radeon shader optimizations (R600_DEBUG=sb)
3. Install smplayer so that I can enjoy vdpau hardware acceleration.

No problem with the first 2 options. But with the third one... well I've just installed the libvdpau but no chance of getting the vdpau working. So I've just tried the old way I've used in 13.04: download the latest mesa (10.0) and compile it with the following options:

```
./configure --with-egl-platforms=x11,drm --with-dri-drivers=radeon  --with-gallium-drivers=r600 --enable-gbm --enable-shared-glapi  --enable-vdpau --enable-glx-tls --enable-gallium-llvm  --with-llvm-shared-libs
```

After a ```
sudo make install
``` the new mesa was installed and my vdpau accleration worked just fine. But just out of curiosity (I tought - hey - maybe my OpenGL will be bumped from 3.1 to 3.2 with the new version of mesa) I checked the glxinfo and to my surprise: opengl is at version 2.1
I had no other option but to reinstall ubuntu.

So does any of you know what can I do to get vdpau working with the curent mesa (9.2.1) without downgrading the opengl version ? Can any of you point me in the right direction. Maybe I did something wrong in the compiling process?

Thank you for your help!

John

---

### Post by Yellow Pasque on 2013-10-20
> Maybe I did something wrong in the compiling process?
Can you give output of ./configure?

---

### Post by fioan89 on 2013-10-21
This is the output: 
```

 prefix:          /usr/local
        exec_prefix:     ${prefix}
        libdir:          ${exec_prefix}/lib
        includedir:      ${prefix}/include

        OpenGL:          yes (ES1: no ES2: no)
        OpenVG:          no

        OSMesa:          no
        DRI drivers:     no
        DRI driver dir:  ${libdir}/dri
        GLX:             DRI-based

        EGL:             yes
        EGL platforms:   x11 drm
        EGL drivers:     builtin:egl_glx builtin:egl_dri2

        llvm:            yes
        llvm-config:     /usr/bin/llvm-config
        llvm-version:    3.2

        Gallium:         yes
        Target dirs:     dri-r600 vdpau-r600 
        Winsys dirs:     radeon/drm sw sw/dri 
        Driver dirs:     galahad identity noop r600 rbug trace 
        Trackers dirs:   dri vdpau 

        Shared libs:     yes
        Static libs:     no
        Shared-glapi:    yes

        CFLAGS:          -g -O2 -Wall -std=c99 -Werror=implicit-function-declaration -Werror=missing-prototypes -fno-strict-aliasing -fno-builtin-memcmp
        CXXFLAGS:        -g -O2 -Wall -fno-strict-aliasing -fno-builtin-memcmp
        Macros:          -D_GNU_SOURCE -DHAVE_PTHREAD -DTEXTURE_FLOAT_ENABLED -DUSE_X86_64_ASM -DHAVE_DLOPEN -DHAVE_POSIX_MEMALIGN -DGLX_INDIRECT_RENDERING -DGLX_DIRECT_RENDERING -DGLX_USE_TLS -DHAVE_PTHREAD -DUSE_EXTERNAL_DXTN_LIB=1 -DHAVE_ALIAS -DHAVE_MINCORE -DHAVE_LIBUDEV -DHAVE_LLVM=0x0302

        LLVM_CFLAGS:     -I/usr/lib/llvm-3.2/include  -D_GNU_SOURCE -D__STDC_CONSTANT_MACROS -D__STDC_FORMAT_MACROS -D__STDC_LIMIT_MACROS
        LLVM_CXXFLAGS:   -I/usr/lib/llvm-3.2/include  -D_GNU_SOURCE -D__STDC_CONSTANT_MACROS -D__STDC_FORMAT_MACROS -D__STDC_LIMIT_MACROS    -fvisibility-inlines-hidden -fno-exceptions -fPIC -Woverloaded-virtual -Wcast-qual
        LLVM_CPPFLAGS:   -I/usr/lib/llvm-3.2/include  -D_GNU_SOURCE -D__STDC_CONSTANT_MACROS -D__STDC_FORMAT_MACROS -D__STDC_LIMIT_MACROS

        PYTHON2:         python2

        Run 'make' to build Mesa
```

---

