---
title: "ffmpeg build issues: libx264"
date: 2008-08-27
forum: Multimedia Software
---

### Post by adam35413 on 2008-08-27
I tried to get the latest source from ffmpeg today and configure/install it.  I am getting a build error on this:

```
gcc -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I. -I"/usr/local/src/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -fasm -std=c99 -fomit-frame-pointer -pthread -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -O3 -fno-math-errno         -c -o libavcodec/libx264.o libavcodec/libx264.c
libavcodec/libx264.c: In function âX264_initâ:
libavcodec/libx264.c:224: error: âX264_ME_TESAâ undeclared (first use in this function)
libavcodec/libx264.c:224: error: (Each undeclared identifier is reported only once
libavcodec/libx264.c:224: error: for each function it appears in.)
libavcodec/libx264.c:256: warning: assignment discards qualifiers from pointer target type
make: *** [libavcodec/libx264.o] Error 1

```

I have updated my sources and have libx264-dev.  Does anyone have any ideas?

---

### Post by flying_surprise on 2008-08-28
X264_ME_TESA is a missing symbol of the repository version of libx264-dev. You need to download and compile a newer version of x264: 
git clone git://git.videolan.org/x264.git

Then configure: 
./configure --prefix=/home/ubuntu_user/apps/lib/x264 --disable-asm

For some reason, it didn't like the yasm in ubuntu repository so I had to disable asm, which will reduce the speed of x264 lib a bit.

Now, I will try to encode some video for my SonyEricsson phone. :-)

---

