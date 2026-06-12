---
title: "Fullscreen streaming lags"
date: 2010-07-07
forum: Multimedia Software
---

### Post by Flauwrens on 2010-07-07
Hey everyone

I have recently installed Ubuntu so I can dual boot with Windows 7 now. I'm very happy with it except for fullscreen streaming. Every time I hit the 'fullscreen' button, it starts lagging. This is not the case in Windows.

Fullscreen playback of 720p movies and stuff like that works great, the problem only occurs when it's a stream.
I did everything in the sticky post of this forum but nothing helped.

I googled the problem and I found out I needed a line enabling 'write-combining' in /proc/mtrr but I'm still pretty much a newbie new so I don't know if this is true.

```
$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back
reg02: base=0x120000000 ( 4608MB), size=  256MB, count=1: write-back
reg03: base=0x0d0000000 ( 3328MB), size=  256MB, count=1: uncachable
reg04: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable

```

---

