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

### Post by xtomga on 2007-05-04
I know it is old but maybe it will help someone.

The root of the problem is that ati driver installer does not work if dpkg-cross is installed at least in case when no architecture is selected during dpkg-cross configuration.

I'm not able to say if it is a fault of dpkg-cross or ati driver installer but uninstalling dpkg-cross definitely helps.

---

### Post by f.manzan on 2007-05-26
Hello, comment one line and work OK:

sh ../ati-driver-installer-8.36.5-x86.x86_64.run --keep --buildpkg Debian/unstable

cd fglrx-install/

joe packages/Debian/dists/sid/rules
       LD_PRELOAD= dh_shlibdeps --exclude=emul
comment prec line in:
#       LD_PRELOAD= dh_shlibdeps --exclude=emul
saving

packages/Debian/ati-packager.sh --buildpkg unstable

and you find 4 or 5 DEB package in previous directory

Bye bye
Federico Manzan

---

