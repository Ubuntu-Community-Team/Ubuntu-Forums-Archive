---
title: "Trouble building ffmpeg with shared libs"
date: 2010-06-15
forum: Multimedia Software
---

### Post by Xenus98 on 2010-06-15
Hi, 

Im trying to build ffmepg with shared lib under ubuntu 8.04 hardy.
Im was following these instructions : 

[>> Install FFmpeg and x264 on Ubuntu Hardy Heron 8.04 LTS <<]("http://ubuntuforums.org/showpost.php?p=6963607&postcount=360")

But it was not for shared library.
So in the part 7. I added "--enable-shared" to the "configure" command
but when I compile ("make") I ve got an error:

"
/usr/bin/ld: /usr/local/lib/libopencore-amrnb.a(wrapper.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libopencore-amrnb.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libavcodec/libavcodec.so.52] Error 1
"

I read another thread saying how to resolve this error :

[>> trouble with ffmpeg and shared libs <<]("http://ubuntuforums.org/showthread.php?t=1211515")

but its still make the error when i follow these instructions...

I decided to add "--enable-pic" flag to "configure" but the error still happen.

Anybody can help please ?

---

### Post by mc4man on 2010-06-15
The error is referring to your libopencore-amrnb build, either find and install .deb packages or rebuild/install as shared

---

