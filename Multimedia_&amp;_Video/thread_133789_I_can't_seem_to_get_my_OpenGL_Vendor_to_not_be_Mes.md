---
title: "I can't seem to get my OpenGL Vendor to not be Mesa"
date: 2006-02-20
forum: Multimedia &amp; Video
---

### Post by kaydot on 2006-02-20
```
kaydot@kubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

If someone could, step by step, guide me through fixing this, I'd be very, very happy. :D

---

### Post by dresnu on 2006-02-20
ati or nvidia? and what model?

---

### Post by subjectdenied on 2006-02-20
i have the same problem

---

### Post by zazery on 2006-02-21
I'm in the middle of figuring this out myself. It seems like the modules are being pointed to the Mesa ones installed, somehow it needs to be redirected to /usr/X11R6/lib where the proper ones were installed assuming they were installed correctly. I'm not sure how to change the link but you can check out your shared library dependencies for the fglrxinfo by typing the following.
```
ldd /usr/bin/glxinfo
  - or -
ldd /usr/X11R6/bin/fglrxinfo
```
Right now my libGL.so.1 points to /usr/lib/libGL.so.1, which I believe is incorrect.

---

### Post by torx on 2006-02-21
same problem! it's good to know i'm not alone on this.


I've been searching the old threads, and this is an output for a working one.

> linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e77000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7db7000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7da9000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c7b000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c69000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c66000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c63000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c5f000)
        /lib/ld-linux.so.2 (0xb7f23000)

---

### Post by zazery on 2006-02-21
Actually if that was the case then mine would work now. I fixed the linking by following these steps but it still hangs if I try to use the fglrx driver instead of the generic ATI drivers.

[LIST=1]
[*] If /etc/ld.so.conf does not exist, create it.
[*] Add the line"/usr/X11R6/lib" to ld.so.conf without the quotes.
[*] Type "sudo ldconfig" without quotes.
[*] Check if the dependency has been changed by typing "ldd /usr/bin/fglrxinfo" without quotes.
[/LIST]
My ldd output is as follows.
```
ldd /usr/X11R6/bin/fglrxinfo
linux-gate.so.1 =>  (0xffffe000)
libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e61000)
libX11.so.6 => /usr/lib/libX11.so.6 (0xb7da1000)
libXext.so.6 => /usr/lib/libXext.so.6 (0xb7d93000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c65000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c53000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c50000)
libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c4d000)
libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c49000)
/lib/ld-linux.so.2 (0xb7f17000)

```
Looking at the /usr/X11R6/bin/fglrxinfo? Do you get any errors? I get the following. Keep in mind that I'm getting 2 monitors to work.
```
/usr/X11R6/bin/fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

display: :0.0  screen: 1
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
Also when reading older posts, some talk about older versions of the ATI driver or possibly the nVida driver so be careful what you try.

---

