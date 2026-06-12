---
title: "Segfault on nearly all audio editing programs"
date: 2012-06-24
forum: Multimedia Software
---

### Post by mlupton on 2012-06-24
For some reason every time I try to launch Ardour, LMMS, or Hydrogen I get the following line...
```
Segmentation fault (core dumped)
```
I tried reinstalling pulseaudio and restarting my computer after doing so, but the problem persisted. After running gdb with LMMS, I figured out it had something to do with libc-2.15.so, but other than that I have found no viable solutions. Please let me know if you find any solution. I am running 12.04 64-bit on an Asus machine.

---

### Post by mlupton on 2012-06-27
Bump

---

