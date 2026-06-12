---
title: "Compiz not working with ATI open source drivers"
date: 2008-12-21
forum: Multimedia Software
---

### Post by crc294 on 2008-12-21
Hello all,

I am running Hardy. I have an ATI mobility radeon which I believe uses the r300 chip. I just installed the xf86-video-ati drivers, downloading them with git then compiling/installing. The performance appears to be great! However, I cannot get compiz to start. Here is what happens:

```
$ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 
```

The screen flickers then returns to normal. Not a very descriptive error message either. I have searched but have been unable to find any further information on this. Any ideas?

---

### Post by crc294 on 2008-12-22
bump

---

### Post by crc294 on 2008-12-23
xserver version: 1:7.3+10ubuntu10.2

compiz version: 1:0.7.4-0ubuntu7

---

### Post by Benanov on 2009-04-09
I have this as well; turns out that glxinfo told me I fell back to Mesa software rendering!

run glxinfo in a terminal and if it tells you you're using mesa (post log here) then we may have a bug.

--BK

---

