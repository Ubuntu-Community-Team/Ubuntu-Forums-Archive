---
title: "installing ffmeg on 6.06"
date: 2008-05-29
forum: Multimedia Software
---

### Post by psykro on 2008-05-29
I am having a problem with installing ffmpeg on my 6.06 server.

I am using the tutorial [here]("https://wiki.ubuntu.com/ffmpeg") (Compiling ffmpeg from upstream svn snapshots option)

Everything goes fine until I get to the 'make' part of the process and then it seems to fail with the following output


```
gcc -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOUR CE -I"/root/ffmpeg-export-2008-05-27" -I"/root/ffmpeg-export-2008-05-27" -fomit-frame-pointer -pthread -Wdeclaration-after-statement -Wall -Wno-switch -Wdisable d-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -O3 -fno-math-errno -c -o libavcodec/libx264.o libavcodec                 /libx264.c
libavcodec/libx264.c: In function âX264_initâ:libavcodec/libx264.c:151: error: âstruct <anonymous>â has no member named âi_rc_methodâ
libavcodec/libx264.c:151: error: âX264_RC_CRFâ undeclared (first use in this function)
libavcodec/libx264.c:151: error: (Each undeclared identifier is reported only once
libavcodec/libx264.c:151: error: for each function it appears in.)
libavcodec/libx264.c:152: error: âstruct <anonymous>â has no member named âf_rf_constantâ
libavcodec/libx264.c:154: error: âstruct <anonymous>â has no member named âi_rc_methodâ
libavcodec/libx264.c:154: error: âX264_RC_CQPâ undeclared (first use in this function)
libavcodec/libx264.c:161: error: âstruct <anonymous>â has no member named âi_rc_methodâ
libavcodec/libx264.c:161: error: âX264_RC_ABRâ undeclared (first use in this function)
libavcodec/libx264.c:254: warning: assignment discards qualifiers from pointer target type
make: *** [libavcodec/libx264.o] Error 1

```

It would appear to be a problem with the libx264 codec (I think) but I am not sure what needs to be done.

Any assistance would be great.

Thanks

---

### Post by kostkon on 2008-06-02
If you do not necessarily want the SVN version, you can add the [*Medibuntu* repository]("http://medibuntu.org/") and install *FFmpeg* from there. This version has support for all the restricted formats (whereas the version of *FFmpeg* from the official repositories does not have support).

---

