---
title: "mpegenc crash on Athlon XP 2600"
date: 2009-05-20
forum: Multimedia Software
---

### Post by walterp98@gmail.com on 2009-05-20
I'm using xubuntu 9.04 on an AMD XP 2600 with 1 gig ram.
 

I re-installed mjpegtools through synaptic (1:1.9.0-0) and even recompiled mjpegtools-1.9.0 from source with:

```

 cd /opt/software/mjpegtools-1.9.0
./configure
./make
sudo make install
 
```Yet when I try to run mpegenc, I get a crash.

 ```
wperz@wperz-desktop:~/work$ jpeg2yuv -n 30 -I p -f 29.97 -j "/tmp/Hells.Kitchen.S01D01/Main Menu VMGM/background.jpg"  2>/dev/null > tmp.yuv
wperz@wperz-desktop:~/work$ ls -l *yuv
-rw-r--r-- 1 wperz wperz 15552229 2009-05-19 22:45 tmp.yuv
wperz@wperz-desktop:~/work$ mpeg2enc -n n -f 8 -a 3 tmp.yuv -o "/tmp/Hells.Kitchen.S01D01/Main Menu VMGM/menu.m2v"
   INFO: [mpeg2enc] SETTING EXTENDED MMX for MOTION!
   INFO: [mpeg2enc] SETTING SSE and MMX for TRANSFORM!
Illegal instruction
``` Help?


Thanks in advance

---

