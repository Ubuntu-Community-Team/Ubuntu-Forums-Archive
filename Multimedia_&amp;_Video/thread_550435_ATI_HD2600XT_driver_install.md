---
title: "ATI HD2600XT driver install"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by mikejordan on 2007-09-13
Can anyone help me out? I'm at it again today, trying to get this thing to work... I get this when trying to run 

sudo sh ./ati-driver-installer-8.41.7-x86.x86_64,run  --buildpkg Ubuntu/feisty

```
dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/x86_64-linux-gnu/lib64/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libgcc_s.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXrandr.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXrender.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_gamma.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libGL.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx.jI6221'
Removing temporary directory: fglrx-install.Zp6141

```

Thanks

---

### Post by isrich on 2007-09-14
I saw guys with fedora 7 x86_64 had problem there.
[http://www.phoronix.com/forums/showthread.php?t=5210](http://www.phoronix.com/forums/showthread.php?t=5210)

It may help.
let try.

---

