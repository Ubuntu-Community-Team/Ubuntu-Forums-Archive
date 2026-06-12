---
title: "Mplayer won't open"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by kiroro on 2008-02-09
I run gmplayer in termial and it says:

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
Segmentation fault (core dumped)

What problem is that?

---

### Post by jan quark on 2008-02-09
try installing the xscreensaver 
it is a wild guess but perhaps mplayer needs it

run this

```
sudo apt-get install xscreensaver-data xscreensaver-gl
```

I have this two installed and mplayer works on my machine

---

### Post by kiroro on 2008-02-09
I tried, but it says: 

xscreensaver-data is already the newest version.
xscreensaver-gl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by kiroro on 2008-02-09
I have the amd64, is that what causes the problem?

---

### Post by HermanAB on 2008-02-09
If you are running Compiz, then that may explain it.  Mplayer doesn't like Compiz...

---

### Post by kiroro on 2008-02-09
I don't even know what Compiz is...so frustrating, can't install mplayer, can't install realplayer...

---

### Post by kiroro on 2008-02-09
Someone please help me with this weird problem... installation went very well, just can't run it.

---

### Post by lijeb on 2008-03-09
permissions.  try sudo gmplayer

[http://ubuntuforums.org/archive/index.php/t-528943.html](http://ubuntuforums.org/archive/index.php/t-528943.html)
View Full Version : HOWTO: Use -vo xvidiv with MPlayer as a normal user (svgalib_helper module)

---

