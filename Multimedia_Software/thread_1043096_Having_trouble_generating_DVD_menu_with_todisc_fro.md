---
title: "Having trouble generating DVD menu with todisc from tovid"
date: 2009-01-18
forum: Multimedia Software
---

### Post by sumpm1 on 2009-01-18
Hey guys. I am getting an error when running the todisc command. I first encoded all of my DVD compliant files using the tovidgui, and now I want to create an animated menu from these files with todisc. All seems to be going well, and then I get an error. Here you can see the END of my todisc log file, after it has encoded all of the pictures. Please help me out here.

Thanks
 
```
encoding frame [1390], 271.19 fps, 77.0%, ETA: 0:00:01, ( 0| 0| 9)  
encoding frame [1400], 271.41 fps, 77.6%, ETA: 0:00:01, ( 2| 1| 6)  
encoding frame [1410], 271.97 fps, 78.1%, ETA: 0:00:01, ( 4| 1| 4)  
encoding frame [1420], 272.49 fps, 78.7%, ETA: 0:00:01, ( 6| 1| 2)  
encoding frame [1430], 270.58 fps, 79.2%, ETA: 0:00:01, ( 0| 0| 9)  
encoding frame [1440], 270.63 fps, 79.8%, ETA: 0:00:01, ( 0| 0| 9)  
encoding frame [1450], 270.63 fps, 80.4%, ETA: 0:00:01, ( 0| 1| 8)  
encoding frame [1460], 270.65 fps, 80.9%, ETA: 0:00:01, ( 0| 0| 9)  
encoding frame [1470], 270.66 fps, 81.5%, ETA: 0:00:01, ( 0| 0| 9)  
encoding frame [1480], 270.89 fps, 82.0%, ETA: 0:00:01, ( 1| 1| 7)  
encoding frame [1490], 271.23 fps, 82.6%, ETA: 0:00:01, ( 2| 1| 6)  
encoding frame [1500], 271.73 fps, 83.1%, ETA: 0:00:01, ( 4| 1| 4)  
encoding frame [1510], 272.15 fps, 83.7%, ETA: 0:00:01, ( 7| 1| 1)  
encoding frame [1520], 270.69 fps, 84.3%, ETA: 0:00:01, ( 1| 1| 7)  
encoding frame [1530], 271.19 fps, 84.8%, ETA: 0:00:01, ( 5| 1| 3)  
encoding frame [1540], 271.62 fps, 85.4%, ETA: 0:00:00, ( 6| 1| 2)  
encoding frame [1550], 272.00 fps, 85.9%, ETA: 0:00:00, ( 7| 1| 1)  
encoding frame [1560], 270.09 fps, 86.5%, ETA: 0:00:00, ( 0| 1| 8)  
encoding frame [1570], 270.56 fps, 87.0%, ETA: 0:00:00, ( 1| 1| 7)  
encoding frame [1580], 271.01 fps, 87.6%, ETA: 0:00:00, ( 3| 1| 5)  
encoding frame [1590], 271.32 fps, 88.1%, ETA: 0:00:00, ( 4| 1| 4)  
encoding frame [1600], 271.74 fps, 88.7%, ETA: 0:00:00, ( 6| 1| 2)  
encoding frame [1610], 272.18 fps, 89.3%, ETA: 0:00:00, ( 7| 1| 1)  
encoding frame [1620], 270.84 fps, 89.8%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1630], 271.12 fps, 90.4%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1640], 271.27 fps, 90.9%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1650], 271.30 fps, 91.5%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1660], 271.37 fps, 92.0%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1670], 271.31 fps, 92.6%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1680], 271.28 fps, 93.2%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1690], 271.21 fps, 93.7%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1700], 271.10 fps, 94.3%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1710], 271.08 fps, 94.8%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1720], 270.94 fps, 95.4%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1730], 270.81 fps, 95.9%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1740], 270.55 fps, 96.5%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1750], 270.49 fps, 97.1%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1760], 270.33 fps, 97.6%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1770], 270.32 fps, 98.2%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1780], 270.31 fps, 98.7%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1790], 270.29 fps, 99.3%, ETA: 0:00:00, ( 0| 0| 9)  
encoding frame [1800], 270.23 fps, 99.8%, ETA: 0:00:00, ( 0| 0| 9)  

clean up | frame threads | unload modules | cancel signal | internal threads |[transcode] encoded 1798 frames (0 dropped, 0 cloned), clip length  59.99 s
 done
[todisc]: Creating a blank mpeg for the vmgm menu
Running: jpeg2yuv -v 1 -f 29.970 -I p -n 1 -l 30 -L 1 -b1 -j 
/tmp/todisc-work.0/dummy.jpg | ffmpeg -f yuv4mpegpipe -i - -an -r 29.970 -s 
720x480 -tvstd ntsc -b 7000k -maxrate 8000k -bufsize 224KiB -aspect 4:3 -y 
/tmp/todisc-work.0/dummy.m2v
   INFO: [jpeg2yuv] Parsing & checking input files.
   INFO: [jpeg2yuv] YUV colorspace detected.

   INFO: [jpeg2yuv] Starting decompression
   INFO: [jpeg2yuv] Image dimensions are 720x480
   INFO: [jpeg2yuv] Movie frame rate is:  29.970030 frames/second
   INFO: [jpeg2yuv] Non-interlaced/progressive frames.
   INFO: [jpeg2yuv] Frame size:  720 x 480
   INFO: [jpeg2yuv] Number of Loops 30
   INFO: [jpeg2yuv] Now generating YUV4MPEG stream.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: rawvideo, yuv420p, 720x480 [PAR 1:1 DAR 3:2], 29.97 tb(r)
Output #0, mpeg2video, to '/tmp/todisc-work.0/dummy.m2v':
    Stream #0.0: Video: 0x0000, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 7000 kb/s, 29.97 tb(c)
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0
   INFO: [jpeg2yuv] Processing non-interlaced/interleaved /tmp/todisc-work.0/dummy.jpg, size 2310
   INFO: [jpeg2yuv] Rescaling color values.
Using mencoder to get length of /tmp/todisc-work.0/dummy.m2v
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
[todisc]:
[todisc]: =========================================================
[todisc]:
[todisc]: ffmpeg
-f s16le
-i /dev/zero
-t -ab
224k -ar
48000 -ac
2 -acodec
ac3 -y
/tmp/todisc-work.0/dummy.ac3 
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, s16le, from '/dev/zero':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
Invalid duration specification: -ab
[todisc]: todisc encountered an error:
```

---

### Post by rodrigth on 2009-02-04
I just ran into the same problem in both QDVDauthor (latest version, compiled from .tar) and in todisc. The problem can be solved by 

sudo apt-get install libavcodec-unstripped-51 libavutil-unstripped-49 libavformat-unstripped-52

Let me know if this works! You might need to enable the Medibuntu repositories: [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by mrtomservo on 2009-03-19
I can verify that your solution worked!  Thanks!

---

### Post by paulgault on 2009-04-05
I had the same problem and this solution worked for me also. thanks! :KS

---

### Post by sermoa on 2009-07-25
wow, the solution seems to work for me too, although i didn't manage to find all the packages. I used libavformat-unstripped-52 and it installed a couple more things with it, and now it seems to be working.

thanks for the advice!

my first post on ubuntu forums by the way! i so often find something helpful on here; today i thought i'd register just to show my appreciation for your solution. i would never have thought of it by myself!

---

