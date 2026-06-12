---
title: "Help Compiling ffmpegthumbnailer from source"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Yadda on 2009-02-09
Hello there, I am trying to compile ffmpegthumbnailer from source under 8.10 and I get the following error when I run make for both the 1.3.0 tar ball and the 1.4.0 tar ball:

```
moviedecoder.cpp: In member function ‘void MovieDecoder::convertAndScaleFrame(int, int, bool, int&, int&)’:
moviedecoder.cpp:308: error: invalid conversion from ‘int’ to ‘PixelFormat’
moviedecoder.cpp:308: error:   initializing argument 6 of ‘SwsContext* sws_getContext(int, int, PixelFormat, int, int, PixelFormat, int, SwsFilter*, SwsFilter*, double*)’
make[2]: *** [moviedecoder.lo] Error 1
make[2]: Leaving directory `/home/travis/sources/ffmpegthumbnailer-1.4.0/src/libffmpegthumbnailer'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/travis/sources/ffmpegthumbnailer-1.4.0/src'
make: *** [all-recursive] Error 1

```

I'm really don't have a clue at all. Please help.

Thanks

---

### Post by Yadda on 2009-02-09
I came up with a workaround. I backported the 1.3.0 package from jaunty from prevu. To get prevu working I used the instructions at: [https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu).

---

### Post by wesg on 2009-04-30
This post is a month old, but has anyone figured out how to do this any better? I'm on Jaunty, and I can't compile it because ofa  recursive directory problem or something.

---

### Post by Arup on 2009-04-30
Jaunty has it in repos, anything wrong with installing it?

---

### Post by wesg on 2009-04-30
I installed it from the repos once, but mediatomb didn't seem to find it.

---

### Post by wesg on 2009-04-30
OK, i figured it out. The required installation is libffmpegthumbnailer-dev , then in included --enable-ffmpegthumbnailer in the configure

---

