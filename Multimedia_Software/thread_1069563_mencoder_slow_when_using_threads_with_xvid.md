---
title: "mencoder slow when using threads with xvid"
date: 2009-02-14
forum: Multimedia Software
---

### Post by rvm4000 on 2009-02-14
xvid 1.2.0 supports multi-threaded encoding, so theorically it should be faster in dual core processors.

I downloaded [xvidcore-1.2.1.tar.bz2](http://downloads.xvid.org/downloads/xvidcore-1.2.1.tar.bz2) and compiled in my kubuntu hardy (amd64)

I also compiled and installed nasm 2.03.01-1, otherwise xvid was extremely slow.

But I realized that actually mencoder is slower when using threads with xvid.

This is the command-line I use:
```

mencoder -noodml -o $OUTPUT \
  -oac copy \
  -ovc xvid \
  -xvidencopts bitrate=1000 \
  $FILE

```

without the *threads* option it gives about 80 fps while encoding a 624x352 video.

If I use *threads=2*

```

mencoder -noodml -o $OUTPUT \
  -oac copy \
  -ovc xvid \
  -xvidencopts bitrate=1000:threads=2 \
  $FILE

```

I see that it's really using the two cores but encoding speed falls to 70 or 75 fps.

Actually the more threads I use, the slower it is. Using *threads=3* gives 28 fps. *threads=4* gives 15 fps.

Is this normal?

---

### Post by rvm4000 on 2009-02-14
I tried to compile the xvid daily snapshot ([xvid_latest.tar.gz](http://downloads.xvid.org/downloads/xvid_latest.tar.gz)). I noticed that this time it used yasm to compile the assembler code (instead of nasm), but still encoding is slower when using threads :(

I can't understand why *threads=2* is slower than *threads=1*...

BTW, I've uploaded the xvid 1.2.1 packages to [https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa) just in case someone else would like to test it and compare.

---

### Post by dankuoni on 2009-02-25
Thanks for the package. I just tried it, and two threads were a bit faster than only one thread (25fps vs. 20fps).

[CPU: Intel T5600@1.83GHz]

*dankuoni

---

### Post by rvm4000 on 2009-02-25
Did you use the i386 or the amd64 package?

---

### Post by mc4man on 2009-02-25
Can't help out cause still using a P4, but last week I wanted to see what was happening with Ht while doing something. The sysstat package proved useful. (mpstat

---

### Post by dankuoni on 2009-02-26
The i386 package.

I forogt to mention in my first post that using more than 2 threads slows everything down.

*dankuoni

---

