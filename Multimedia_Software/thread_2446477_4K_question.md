---
title: "4K question"
date: 2020-07-01
forum: Multimedia Software
---

### Post by zkab on 2020-07-01
Don't know if this is the right forum to ask my question ...

I have an Intel NUC as media player to my 4K environment (TV & HTPC).
The NUC runs Ubuntu xfce 20.04 LTS and 'inxi' gives me:
Graphics:  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel bus ID: 00:02.0 
           Display: server: X.org 1.20.8 driver: modesetting unloaded: fbdev,vesa tty: 122x60 
           Message: Advanced graphics data unavailable in console. Try -G --display 

Do I have to do some settings in xfce when streaming 4K content from internet?
My TV & HTPC & HDMI & HDMI cables are all 4K ready ... so I don't want xfce & NUC to be the weak link ...

---

### Post by crip720 on 2020-07-01
Think it depends more on graphics driver.  Would google your CPU with 4K and see if it supports it.  Recent versions of Ubuntu should.

---

### Post by zkab on 2020-07-01
I found this on Intel FAQ ...

Does my processor support 4K video?
For 4K video support, you need:

3rd Generation Intel® Core™ Processor or higher with Intel® HD Graphics and the latest Intel® HD Graphics driver.
High-speed HDMI cable. Standard-speed HDMI cables won't support 4K.
Intel® Pentium® and Intel® Celeron® Processors do not support 4K video.

Since I have following I guess I am on the right track ...
CPU:       Topology: Dual Core model: Intel Core i5-3427U bits: 64 type: MT MCP arch: Ivy Bridge rev: 9 
           L2 cache: 3072 KiB 
           flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 18358

---

### Post by CatKiller on 2020-07-01
> **zkab said:**
> so I don't want xfce & NUC to be the weak link ...

It depends on the source. Outputting a 4K image is pretty trivial. Outputting 4K video is not that much harder. Outputting 4K video with hardware acceleration so that you get decent performance, since doing smooth 4K in software is out of reach for many processors, is where things start to get messy. For your own videos you can encode them with a codec that you know you have hardware support for, since older hardware doesn't have support for new codecs, and there are Linux media players that can use hardware acceleration. Online sources are rather interested in their bandwidth costs, so they aggressively move to newer, more efficient, codecs, which you might not have support for. Browser support for hardware acceleration is hit-and-miss in general, and they all used to disable it by default on Linux. You used to need to use a particular build of Chromium that enabled that hardware acceleration, but that's starting to change. Amazon arbitrarily restricts the resolution of their streams if they suspect you're using Linux.

---

### Post by Yellow Pasque on 2020-07-01
It seems like the HD4000 GPU does not support 4k officially, but you can hack it with xrandr to get 3840x2160@30Hz

---

