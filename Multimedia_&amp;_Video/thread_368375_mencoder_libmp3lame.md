---
title: "mencoder libmp3lame"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by Bossieman on 2007-02-23
This is a problem I havent been able to solve

leif@Dimension-5000:~$ mencoder -idx out.ogg -ovc lavc -oac mp3lame -o out.avi
MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

MPlayer was compiled without libmp3lame support.
leif@Dimension-5000:~$ 

when I run locate libmp3lame.so I get

leif@Dimension-5000:~$ locate libmp3lame.so
/usr/lib/libmp3lame.so
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0
/usr/local/lib/libmp3lame.so
/usr/local/lib/libmp3lame.so.0.0.0
/usr/local/lib/libmp3lame.so.0
leif@Dimension-5000:~$ 

What can I do to solve this?

---

### Post by Bossieman on 2007-02-23
Anyone?

---

### Post by Ergo on 2007-02-23
Unfortunately, you may need to compile Mplayer from source.  For whatever reason, it does not know where your libraries are located.  You might want to check your PATH variable and see if the directory to access the libmp3*.so is located there as well.  Other than that, I am at a loss.

---

### Post by Bossieman on 2007-02-24
I solved it! Download lame source and configure with 

./configure --prefix=/usr

The just reinstall mplayer.

---

### Post by eggdeng on 2007-06-05
That works alright. Neat fix Bossieman, thanx.

---

