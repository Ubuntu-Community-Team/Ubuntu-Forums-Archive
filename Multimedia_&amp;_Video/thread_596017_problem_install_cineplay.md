---
title: "problem install cineplay"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by denar on 2007-10-29
how can i install cineplay-1.1-beta.run

i try ./cineplay-1.1-beta.run and i try sudo alien cineplay-1.1-beta.run and nothing happened

how can i install this.:confused:

---

### Post by DBAlex on 2007-10-29
Try doubleclicking the file and then press run in **Terminal**

If it complains about not being root **cd** in the terminal to the directory with the file and type **sudo ./cineplay-1.1-beta.run** or just **sudo cineplay-1.1-beta.run** (Cant remember which is correct)

Hope that helps!

:)

---

### Post by denar on 2007-10-29
Try doubleclicking the file and then press run in Terminal
i do but this happeend

zero@zero-desktop:~/Desktop$ ./cineplay-1.1-beta.run
Verifying archive integrity... All good.
Uncompressing CinePlay 1.1 for Fedora Core 5......
error: Failed dependencies:
        /sbin/ldconfig is needed by cineplay-1.1-1.i386
        /usr/bin/env is needed by cineplay-1.1-1.i386
        libGL.so.1 is needed by cineplay-1.1-1.i386
        libGLU.so.1 is needed by cineplay-1.1-1.i386
        libX11.so.6 is needed by cineplay-1.1-1.i386
        libXext.so.6 is needed by cineplay-1.1-1.i386
        libXmu.so.6 is needed by cineplay-1.1-1.i386
        libboost_filesystem.so.2 is needed by cineplay-1.1-1.i386
        libc.so.6 is needed by cineplay-1.1-1.i386
        libc.so.6(GLIBC_2.0) is needed by cineplay-1.1-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by cineplay-1.1-1.i386
        libgcc_s.so.1 is needed by cineplay-1.1-1.i386
        libgcc_s.so.1(GCC_3.0) is needed by cineplay-1.1-1.i386
        libgcc_s.so.1(GLIBC_2.0) is needed by cineplay-1.1-1.i386
        libm.so.6 is needed by cineplay-1.1-1.i386
        libm.so.6(GLIBC_2.0) is needed by cineplay-1.1-1.i386
        libpthread.so.0 is needed by cineplay-1.1-1.i386
        libpthread.so.0(GLIBC_2.0) is needed by cineplay-1.1-1.i386
        libqt-mt.so.3 is needed by cineplay-1.1-1.i386
        libstdc++.so.6 is needed by cineplay-1.1-1.i386
        libstdc++.so.6(CXXABI_1.3) is needed by cineplay-1.1-1.i386
        libstdc++.so.6(GLIBCXX_3.4) is needed by cineplay-1.1-1.i386
        /bin/sh is needed by olib-ffmpeg-0.4.9-1.i386
        faac >= 1.24 is needed by olib-ffmpeg-0.4.9-1.i386
        faad2 >= 2.0 is needed by olib-ffmpeg-0.4.9-1.i386
        lame >= 3.97 is needed by olib-ffmpeg-0.4.9-1.i386
        libSDL-1.2.so.0 is needed by olib-ffmpeg-0.4.9-1.i386
        libc.so.6 is needed by olib-ffmpeg-0.4.9-1.i386
        libc.so.6(GLIBC_2.0) is needed by olib-ffmpeg-0.4.9-1.i386
        libc.so.6(GLIBC_2.1) is needed by olib-ffmpeg-0.4.9-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by olib-ffmpeg-0.4.9-1.i386
        libc.so.6(GLIBC_2.2) is needed by olib-ffmpeg-0.4.9-1.i386
        libc.so.6(GLIBC_2.3) is needed by olib-ffmpeg-0.4.9-1.i386
        libdl.so.2 is needed by olib-ffmpeg-0.4.9-1.i386
        libdl.so.2(GLIBC_2.0) is needed by olib-ffmpeg-0.4.9-1.i386
        libdl.so.2(GLIBC_2.1) is needed by olib-ffmpeg-0.4.9-1.i386
        libfaac.so.0 is needed by olib-ffmpeg-0.4.9-1.i386
        libfaad.so.0 is needed by olib-ffmpeg-0.4.9-1.i386
        libm.so.6 is needed by olib-ffmpeg-0.4.9-1.i386
        libm.so.6(GLIBC_2.0) is needed by olib-ffmpeg-0.4.9-1.i386
        libm.so.6(GLIBC_2.1) is needed by olib-ffmpeg-0.4.9-1.i386
        libogg.so.0 is needed by olib-ffmpeg-0.4.9-1.i386
        libpthread.so.0 is needed by olib-ffmpeg-0.4.9-1.i386
        libz.so.1 is needed by olib-ffmpeg-0.4.9-1.i386
        /bin/sh is needed by olib-glew-1.4.0-1.i386
        /sbin/ldconfig is needed by olib-glew-1.4.0-1.i386
        libGL.so.1 is needed by olib-glew-1.4.0-1.i386
        libGLU.so.1 is needed by olib-glew-1.4.0-1.i386
        libX11.so.6 is needed by olib-glew-1.4.0-1.i386
        libXext.so.6 is needed by olib-glew-1.4.0-1.i386
        libXi.so.6 is needed by olib-glew-1.4.0-1.i386
        libXmu.so.6 is needed by olib-glew-1.4.0-1.i386
        libc.so.6 is needed by olib-glew-1.4.0-1.i386
        libc.so.6(GLIBC_2.0) is needed by olib-glew-1.4.0-1.i386
        libc.so.6(GLIBC_2.1) is needed by olib-glew-1.4.0-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by olib-glew-1.4.0-1.i386
        /bin/sh is needed by openlibraries-0.4.1-1.i386
        libGL.so.1 is needed by openlibraries-0.4.1-1.i386
        libGLU.so.1 is needed by openlibraries-0.4.1-1.i386
        libHalf.so.2 is needed by openlibraries-0.4.1-1.i386
        libIex.so.2 is needed by openlibraries-0.4.1-1.i386
        libIlmImf.so.2 is needed by openlibraries-0.4.1-1.i386
        libImath.so.2 is needed by openlibraries-0.4.1-1.i386
        libSDL-1.2.so.0 is needed by openlibraries-0.4.1-1.i386
        libboost_filesystem.so.2 is needed by openlibraries-0.4.1-1.i386
        libboost_python.so.2 is needed by openlibraries-0.4.1-1.i386
        libboost_regex.so.2 is needed by openlibraries-0.4.1-1.i386
        libboost_thread.so.2 is needed by openlibraries-0.4.1-1.i386
        libc.so.6 is needed by openlibraries-0.4.1-1.i386
        libc.so.6(GLIBC_2.0) is needed by openlibraries-0.4.1-1.i386
        libc.so.6(GLIBC_2.1) is needed by openlibraries-0.4.1-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by openlibraries-0.4.1-1.i386
        libc.so.6(GLIBC_2.4) is needed by openlibraries-0.4.1-1.i386
        libdl.so.2 is needed by openlibraries-0.4.1-1.i386
        libfaac.so.0 is needed by openlibraries-0.4.1-1.i386
        libfaad.so.0 is needed by openlibraries-0.4.1-1.i386
        libgcc_s.so.1 is needed by openlibraries-0.4.1-1.i386
        libgcc_s.so.1(GCC_3.0) is needed by openlibraries-0.4.1-1.i386
        libgcc_s.so.1(GLIBC_2.0) is needed by openlibraries-0.4.1-1.i386
        libglut.so.3 is needed by openlibraries-0.4.1-1.i386
        libjpeg.so.62 is needed by openlibraries-0.4.1-1.i386
        libm.so.6 is needed by openlibraries-0.4.1-1.i386
        libm.so.6(GLIBC_2.0) is needed by openlibraries-0.4.1-1.i386
        libogg.so.0 is needed by openlibraries-0.4.1-1.i386
        libopenal.so.0 is needed by openlibraries-0.4.1-1.i386
        libpng12.so.0 is needed by openlibraries-0.4.1-1.i386
        libpthread.so.0 is needed by openlibraries-0.4.1-1.i386
        libpthread.so.0(GLIBC_2.0) is needed by openlibraries-0.4.1-1.i386
        libqt-mt.so.3 is needed by openlibraries-0.4.1-1.i386
        libsqlite3.so.0 is needed by openlibraries-0.4.1-1.i386
        libstdc++.so.6 is needed by openlibraries-0.4.1-1.i386
        libstdc++.so.6(CXXABI_1.3) is needed by openlibraries-0.4.1-1.i386
        libstdc++.so.6(GLIBCXX_3.4) is needed by openlibraries-0.4.1-1.i386
        libtiff.so.3 is needed by openlibraries-0.4.1-1.i386
        libxml2.so.2 is needed by openlibraries-0.4.1-1.i386
        libz.so.1 is needed by openlibraries-0.4.1-1.i386
zero@zero-desktop:~/Desktop$

---

### Post by denar on 2007-10-29
some one download CinePlay and try install and took me how is it
[http://editopia.com/CinePlay]("http://editopia.com/CinePlay")

---

