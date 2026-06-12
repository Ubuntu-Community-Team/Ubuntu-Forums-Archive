---
title: "Stuck on MESA"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by lexaken on 2007-12-12
So, I am using an ATi AiW 9800 on Ubuntu 7.10
I have tried EVERY combination of EVERY install guide and I keep getting stuck with MESA!
I even (recently) formatted to try it on a clean install

```
alex@alex:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

I've about had it to my wit's end with this; I have been tooling around for ~6 hrs a day for the past 3 days trying to get this to work. All I want is some freaking 3d!!!!!

Any and all help is VERY MUCH APPRECIATED!

---

### Post by lexaken on 2007-12-12
I found this in my /var/log/Xorg.0.log

> (WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

> (WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


> (EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP

> (EE) AIGLX: Screen 0 is not DRI capable

---

### Post by sowelie on 2007-12-12
Hey Lexaken,

I had a similar problem...check out this post to see if it helps:

[http://ubuntuforums.org/showthread.php?t=427601.]("http://ubuntuforums.org/showthread.php?t=427601.")

Also, I used this guide and it worked for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

I have an ATI 9600 Pro, but I did also get it working on an all in wonder 9800 at one point.

---

### Post by lexaken on 2007-12-12
Sowelie, thanks but still no dice.

I checked dmesg and found this:

```
[   54.383770] [fglrx] Internal AGP is not supported in 2.6 kernel.
[   54.383918] [fglrx:firegl_unlock] *ERROR* Process 5502 using kernel context 0

```

```
[   41.622906] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   41.656732] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   41.656776] [fglrx] ASYNCIO init succeed!
[   41.656991] [fglrx] PAT is enabled successfully!
[   41.657015] [fglrx] module loaded - fglrx 8.43.2 [Nov  9 2007] on minor 0

```

Ugh, this **** just pisses me off.

---

### Post by lexaken on 2007-12-12
> alex@alex:~$ lsmod | grep agp
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp

In case it helps

---

### Post by LeBurt on 2007-12-13
I know how you feel, I've long abandoned any hope of having my 9600 All-In-Wonder to work in 3D. I've had pretty much every problem in the book (black screen, MESA, white screen) and NOTHING worked. I too have a feeling that AGP is the issue but apparently I'm not smart enough to resolve this one.

BTW, I had all the same DRI messages in Xorg.0.log. Tried a clean install after that and now am stuck at a black screen when I try fglrx (X won't start, crashes). This is the weirdest problem, it's not even consistent from one clean install to another. Hardware problem?

---

