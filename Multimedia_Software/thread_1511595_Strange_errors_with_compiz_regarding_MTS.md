---
title: "Strange errors with compiz regarding MTS"
date: 2010-06-17
forum: Multimedia Software
---

### Post by Lord.Quackstar on 2010-06-17
For the past few hours, I have been trying hopelessly to get compiz to work on a dual screen setup with an old graphics card. Here are some specs

Card: ATI Radeon X800 XT
Driver: Native OS driver
Reported MTS (with 3D) 2048x2048
Resolution: 2048x768
Compiz Version: 1:0.8.4-0ubuntu15.1

(Yes, I pulled this compiz version from lucid-proposed)

And just to prove all of this, here's the console commands I tried

```
lordquackstar@quackdesk-linux:~$ glxinfo -l | grep -i max_texture_size
    GL_MAX_TEXTURE_SIZE = 2048

lordquackstar@quackdesk-linux:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc R420 JP [Radeon X800XT]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

lordquackstar@quackdesk-linux:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager

```

With some extensive googleing, I found a **[ closed launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/428769")** from April, **[a forum topic also from April]("http://swiss.ubuntuforums.org/showthread.php?p=9109871")** talking about the bug, and the **[changelog showing that its been fixed already]("http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.8.4-0ubuntu15/changelog")**. So why is it still not working for me?

---

