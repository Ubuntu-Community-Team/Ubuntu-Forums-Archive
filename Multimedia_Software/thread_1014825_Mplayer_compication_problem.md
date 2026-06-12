---
title: "Mplayer compication problem"
date: 2008-12-18
forum: Multimedia Software
---

### Post by emiliorodo on 2008-12-18
Hello guys
I'm having some troublbe compiling Mplayer from source.I did an svn checkout, but when I tried to make it I got the following error:


libx264.c: In function 'X264_init':
libx264.c:167: error: 'x264_param_t' has no member named 'i_bframe_adaptive'
make[1]: *** [libx264.o] Error 1
make[1]: Leaving directory `/home/emil/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2

Any clue as to how I can fix this?

---

### Post by shirilover on 2008-12-18
You may just need to wait and then do an svn update.
Since the svn source is constantly changing, breakages will occur.

---

### Post by andrew.46 on 2008-12-18
Hi emiliorodo,

> **emiliorodo said:**
> 
libx264.c: In function 'X264_init':
libx264.c:167: error: 'x264_param_t' has no member named 'i_bframe_adaptive'
make[1]: *** [libx264.o] Error 1
make[1]: Leaving directory `/home/emil/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2


As shirilover has suggested a newer svn may help. But I suspect as well that you may have an older version of the x264 library in place. If you are not considering encoding to x264 / h264 you could try removing this library and recompiling. If you wish to encode to x264 you should still remove it and then install the git x264 in its place. Some more details can be seen here:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

All the best,

  Andrew

---

