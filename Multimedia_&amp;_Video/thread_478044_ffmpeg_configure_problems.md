---
title: "ffmpeg configure problems"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by penguinchrissy on 2007-06-18
I'm trying to follow this site [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

when I get to sudo make install I run into problems here is my output

make -C libavutil   all
make[1]: Entering directory `/home/dj/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dj/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/dj/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/dj/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/dj/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2

---

### Post by penguinchrissy on 2007-06-19
here are some more logs on what happens when I do make and make install. I also tried editing /libavcode/x264.c as suggested in this forum [http://ubuntuforums.org/showthread.php?t=418883&highlight=configure+ffmpeg](http://ubuntuforums.org/showthread.php?t=418883&highlight=configure+ffmpeg). That seemed to get me farther but still not luck. Please help I'm going on a long trip and videos would be great to have!

---

