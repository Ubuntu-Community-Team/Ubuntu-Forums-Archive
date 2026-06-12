---
title: "trying to rebuild and reinstall ffmpeg but error"
date: 2009-11-03
forum: Multimedia Software
---

### Post by mibungu on 2009-11-03
ffmpeg$ ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
ERROR: libx264 version must be >= 0.78.


and then I can't make of course 

trying to get this going to edit .mts format video :(

how do I solve this:(

---

### Post by mc4man on 2009-11-03
If your using the current ffmpeg source (or any ffmpeg source after 9/24 or so) you'll need a current libx264 and headers (-dev)

You could ck. this guide for the x264 build, ect.
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)


............................ not suitable for all but...

 if using the current source and want to install pre-built packages then these would be suitable

Note these are 32 bit, also package wise you can have as many different libx264-XX as you wish/need, but only 1 -dev package. The -dev installed must match the libx264-XX you wish your build to use.

[http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libx264-78.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libx264-78.php)

[http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libx264-dev.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libx264-dev.php)

( direct download and install, the libx264-78 will install cleanly, do first, then the -dev ( remove current -dev if installed

---

### Post by mibungu on 2009-11-03
tried but getting the same error

---

