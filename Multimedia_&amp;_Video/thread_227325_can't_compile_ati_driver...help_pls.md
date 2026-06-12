---
title: "can't compile ati driver...help pls"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by KabalS on 2006-08-01
I recently downloaded the last ati drivers from the unofficialn ati wiki: ati-driver-installer-8.27.10-x86.run

I followed the instruction and when i call "LANG=C LANG_ALL=C ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper" I get this message:

....
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i486-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/i486-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/i486-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libgcc_s.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libXrandr.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/libXrender.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_gamma.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx.8S5wez'
/home/admin/Desktop/fglrx-install
Removing temporary directory: fglrx-install
...

Someone can help me?

---

### Post by Alyus on 2006-08-01
I had a similar problem with this driver.  On a whim I tried just running ati's installer instead of creating .deb's and it worked great.

---

