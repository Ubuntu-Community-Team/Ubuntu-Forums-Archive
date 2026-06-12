---
title: "MP4Box Aborting during conversion"
date: 2009-05-06
forum: Multimedia Software
---

### Post by lmbear2000 on 2009-05-06
I am trying to convert a movie from MKV to MP4. I am failing on the last step.

MP4Box -new output.mp4 -add video.h264 -add audio.m4a -fps 23.976

Does anyone know why it's aborting and how to fix it?:confused:

======= Memory map: ========
08048000-0806e000 r-xp 00000000 08:01 7220335    /usr/bin/MP4Box
0806e000-08070000 r--p 00026000 08:01 7220335    /usr/bin/MP4Box
08070000-08071000 rw-p 00028000 08:01 7220335    /usr/bin/MP4Box
09ca3000-0a6ca000 rw-p 09ca3000 00:00 0          [heap]
b78f9000-b7906000 r-xp 00000000 08:01 8291606    /lib/libgcc_s.so.1
b7906000-b7907000 r--p 0000c000 08:01 8291606    /lib/libgcc_s.so.1
b7907000-b7908000 rw-p 0000d000 08:01 8291606    /lib/libgcc_s.so.1
b7919000-b79f8000 rw-p b7919000 00:00 0 
b79f8000-b79fa000 r-xp 00000000 08:01 8306776    /lib/tls/i686/cmov/libdl-2.8.90.so
b79fa000-b79fb000 r--p 00001000 08:01 8306776    /lib/tls/i686/cmov/libdl-2.8.90.so
b79fb000-b79fc000 rw-p 00002000 08:01 8306776    /lib/tls/i686/cmov/libdl-2.8.90.so
b79fc000-b79fd000 rw-p b79fc000 00:00 0 
b79fd000-b7a12000 r-xp 00000000 08:01 8307754    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7a12000-b7a13000 r--p 00014000 08:01 8307754    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7a13000-b7a14000 rw-p 00015000 08:01 8307754    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7a14000-b7a16000 rw-p b7a14000 00:00 0 
b7a16000-b7b49000 r-xp 00000000 08:01 7249951    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7b49000-b7b51000 r--p 00132000 08:01 7249951    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7b51000-b7b5e000 rw-p 0013a000 08:01 7249951    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7b5e000-b7b62000 rw-p b7b5e000 00:00 0 
b7b62000-b7ba4000 r-xp 00000000 08:01 7249952    /usr/lib/i686/cmov/libssl.so.0.9.8
b7ba4000-b7ba5000 r--p 00041000 08:01 7249952    /usr/lib/i686/cmov/libssl.so.0.9.8
b7ba5000-b7ba8000 rw-p 00042000 08:01 7249952    /usr/lib/i686/cmov/libssl.so.0.9.8
b7ba8000-b7bcc000 r-xp 00000000 08:01 8306777    /lib/tls/i686/cmov/libm-2.8.90.so
b7bcc000-b7bcd000 r--p 00023000 08:01 8306777    /lib/tls/i686/cmov/libm-2.8.90.so
b7bcd000-b7bce000 rw-p 00024000 08:01 8306777    /lib/tls/i686/cmov/libm-2.8.90.so
b7bce000-b7d26000 r-xp 00000000 08:01 8306772    /lib/tls/i686/cmov/libc-2.8.90.so
b7d26000-b7d28000 r--p 00158000 08:01 8306772    /lib/tls/i686/cmov/libc-2.8.90.so
b7d28000-b7d29000 rw-p 0015a000 08:01 8306772    /lib/tls/i686/cmov/libc-2.8.90.so
b7d29000-b7d2d000 rw-p b7d29000 00:00 0 
b7d2d000-b7d41000 r-xp 00000000 08:01 7217303    /usr/lib/libz.so.1.2.3.3
b7d41000-b7d43000 rw-p 00013000 08:01 7217303    /usr/lib/libz.so.1.2.3.3
b7d43000-b7fbd000 r-xp 00000000 08:01 7217402    /usr/lib/libgpac-0.4.4.so
b7fbd000-b7fbe000 r--p 00279000 08:01 7217402    /usr/lib/libgpac-0.4.4.so
b7fbe000-b7fc2000 rw-p 0027a000 08:01 7217402    /usr/lib/libgpac-0.4.4.so
b7fc2000-b7fc4000 rw-p b7fc2000 00:00 0 
b7fd2000-b7fd7000 rw-p b7fd2000 00:00 0 
b7fd7000-b7ff1000 r-xp 00000000 08:01 8290323    /lib/ld-2.8.90.so
b7ff1000-b7ff2000 r-xp b7ff1000 00:00 0          [vdso]
b7ff2000-b7ff3000 r--p 0001a000 08:01 8290323    /lib/ld-2.8.90.so
Aborted

---

### Post by FakeOutdoorsman on 2009-05-06
What version of Ubuntu are you using?  Works fine for me with:
```
MP4Box -fps 23.976 -add video.h264 -add audio.m4a output.mp4
```
You could also try FFmpeg to combine these streams:
```
ffmpeg -i video.h264 -i audio.m4a -acodec copy -vcodec copy output.mp4
```
Then you could run it through MP4Box if you like:
```
MP4Box -add output.mp4 newoutput.mp4
```

---

### Post by lmbear2000 on 2009-05-06
I am using 8.10 and ffmpg did not work either.

---

