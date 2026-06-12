---
title: "Kdenlive crashes upon start"
date: 2011-10-20
forum: Multimedia Software
---

### Post by marer13 on 2011-10-20
Hi,

I've tried reinstalling Kdenlive (it was throwing out the MLT error message) and now when it starts it crashes. Here's the output from the console:

> marer13@marer13-Studio:~$ kdenlive
project monitor connected 
clip monitor connected 
detected format: YUV 4:2:2 (YUYV): YUYV
Size: 640x480: 1/30, 
Size: 352x288: 1/30, 
Size: 320x240: 1/30, 
Size: 176x144: 1/30, 
Size: 160x120: 1/30, 
Size: 800x600: 1/15, 
Size: 1024x768: 1/12, 
Size: 1280x1024: 2/15, 
Size: 1600x1200: 1/5, 
detected format: MJPEG: MJPG
Size: 640x480: 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, 
*** glibc detected *** kdenlive: munmap_chunk(): invalid pointer: 0x0000000001e83650 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f3a1d86fa96]
kdenlive(query_v4ldevice+0x37e)[0x70da1e]
kdenlive[0x70d4f2]
kdenlive[0x659b6e]
kdenlive[0x65d47f]
kdenlive[0x45b3b9]
kdenlive[0x47f6df]
kdenlive[0x44eb33]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f3a1d81830d]
kdenlive[0x44f501]
======= Memory map: ========
00400000-007a4000 r-xp 00000000 08:06 6044920                            /usr/bin/kdenlive
009a3000-009a4000 r--p 003a3000 08:06 6044920                            /usr/bin/kdenlive
009a4000-009aa000 rw-p 003a4000 08:06 6044920                            /usr/bin/kdenlive
009aa000-009ac000 rw-p 00000000 00:00 0 
00c7f000-01e9d000 rw-p 00000000 00:00 0                                  [heap]
7f3a015ae000-7f3a01b9d000 rw-p 00000000 00:00 0 
7f3a01b9d000-7f3a01ba4000 r-xp 00000000 08:06 6031968                    /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f3a01ba4000-7f3a01da3000 ---p 00007000 08:06 6031968                    /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f3a01da3000-7f3a01da4000 r--p 00006000 08:06 6031968                    /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f3a01da4000-7f3a01da5000 rw-p 00007000 08:06 6031968                    /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f3a01da5000-7f3a01da8000 r-xp 00000000 08:06 6169553                    /usr/lib/mlt/libmltvorbis.so
7f3a01da8000-7f3a01fa7000 ---p 00003000 08:06 6169553                    /usr/lib/mlt/libmltvorbis.so
7f3a01fa7000-7f3a01fa8000 r--p 00002000 08:06 6169553                    /usr/lib/mlt/libmltvorbis.so
7f3a01fa8000-7f3a01fa9000 rw-p 00003000 08:06 6169553                    /usr/lib/mlt/libmltvorbis.so
7f3a01fa9000-7f3a01fbd000 r-xp 00000000 08:06 6169560                    /usr/lib/mlt/libmltqimage.so
7f3a01fbd000-7f3a021bd000 ---p 00014000 08:06 6169560                    /usr/lib/mlt/libmltqimage.so
7f3a021bd000-7f3a021be000 r--p 00014000 08:06 6169560                    /usr/lib/mlt/libmltqimage.so
7f3a021be000-7f3a021bf000 rw-p 00015000 08:06 6169560                    /usr/lib/mlt/libmltqimage.so
7f3a021bf000-7f3a021c3000 r-xp 00000000 08:06 6169561                    /usr/lib/mlt/libmltvmfx.so
7f3a021c3000-7f3a023c2000 ---p 00004000 08:06 6169561                    /usr/lib/mlt/libmltvmfx.so
7f3a023c2000-7f3a023c3000 r--p 00003000 08:06 6169561                    /usr/lib/mlt/libmltvmfx.so
7f3a023c3000-7f3a023c4000 rw-p 00004000 08:06 6169561                    /usr/lib/mlt/libmltvmfx.so
7f3a023c4000-7f3a023c9000 r-xp 00000000 08:06 6169558                    /usr/lib/mlt/libmltdgraft.so
7f3a023c9000-7f3a025c8000 ---p 00005000 08:06 6169558                    /usr/lib/mlt/libmltdgraft.so
7f3a025c8000-7f3a025c9000 r--p 00004000 08:06 6169558                    /usr/lib/mlt/libmltdgraft.so
7f3a025c9000-7f3a025ca000 rw-p 00005000 08:06 6169558                    /usr/lib/mlt/libmltdgraft.so
7f3a025ca000-7f3a025cf000 r-xp 00000000 08:06 6169542                    /usr/lib/mlt/libmltoldfilm.so
7f3a025cf000-7f3a027ce000 ---p 00005000 08:06 6169542                    /usr/lib/mlt/libmltoldfilm.so
7f3a027ce000-7f3a027cf000 r--p 00004000 08:06 6169542                    /usr/lib/mlt/libmltoldfilm.so
7f3a027cf000-7f3a027d0000 rw-p 00005000 08:06 6169542                    /usr/lib/mlt/libmltoldfilm.so
7f3a027d0000-7f3a0293b000 r-xp 00000000 08:06 6029451                    /usr/lib/x86_64-linux-gnu/libsamplerate.so.0.1.7
7f3a0293b000-7f3a02b3a000 ---p 0016b000 08:06 6029451                    /usr/lib/x86_64-linux-gnu/libsamplerate.so.0.1.7
7f3a02b3a000-7f3a02b3b000 r--p 0016a000 08:06 6029451                    /usr/lib/x86_64-linux-gnu/libsamplerate.so.0.1.7
7f3a02b3b000-7f3a02b3c000 rw-p 0016b000 08:06 6029451                    /usr/lib/x86_64-linux-gnu/libsamplerate.so.0.1.7
7f3a02b3c000-7f3a02b44000 r-xp 00000000 08:06 6169547                    /usr/lib/mlt/libmltgtk2.so
7f3a02b44000-7f3a02d44000 ---p 00008000 08:06 6169547                    /usr/lib/mlt/libmltgtk2.so
7f3a02d44000-7f3a02d45000 r--p 00008000 08:06 6169547                    /usr/lib/mlt/libmltgtk2.so
7f3a02d45000-7f3a02d46000 rw-p 00009000 08:06 6169547                    /usr/lib/mlt/libmltgtk2.soKCrash: Application 'kdenlive' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/marer13/.kde/socket-marer13-Studio/kdeinit4__0

[1]+  Stopped                 kdenlive
marer13@marer13-Studio:~$ 

Any help will be appreciated

---

### Post by bbrhuft on 2011-11-02
I can't help other than say I have exactly the same problem. I just upgraded to version Kdenlive 0.8.2 using the recommended sunab repository, now Kdenlive crashes on start-up. 

Deleting kdenlive's settings file $HOME/.kde/share/config/kdenliverc does not help.

no more csLADSPA plugins
no more csLADSPA plugins
project monitor connected 
clip monitor connected 
detected format: YUV 4:2:2 (YUYV): YUYV
Size: 640x480: 1/30, 1/20, 1/15, 1/10, 1/5, 1/1, 
Size: 320x240: 1/30, 1/20, 1/15, 1/10, 1589/15625, 1/1, 
Size: 160x120: 1/30, 1/20, 1/15, 1/10, 1589/15625, 1/1, 
Size: 176x144: 1/30, 1/20, 1/15, 1/10, 1589/15625, 1/1, 
Size: 352x288: 1/30, 1/20, 1/15, 1/10, 1589/15625, 1/1, 
Size: 800x600: 1/30, 1/20, 1/15, 1/10, 1589/15625, 1/1, 
Size: 1024x960: 1/30, 1/20, 1/15, 1/10, 1589/15625, 1/1, 
Size: 1280x1024: 1/9, 1/5, 1/1, 
detected format: MJPEG: MJPG
Size: 640x480: 1/30, 1/30, 1/30, 1/30, 1/30, 1/30, etc.

---

