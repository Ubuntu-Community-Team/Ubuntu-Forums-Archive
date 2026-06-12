---
title: "Stuck in Software Rendering using ATI driver"
date: 2011-05-12
forum: Multimedia Software
---

### Post by osarusan on 2011-05-12
I have an ATI Radeon HD 4770, using Natty x64 and the open source ati drivers.

I'm having some trouble with graphics, and I'm stuck in software rendering mode.


```
:~$ LIBGL_DEBUG=verbose glxinfo|grep render
libGL: OpenDriver: trying /usr/lib/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r600_dri.so
libGL error: failed to create dri screen
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```

As you can see, the r600 dri is failing somewhere and it is falling back to the software rasterizer. I didn't have this problem before Natty, but now I just can't seem to fix it. I've googled around and there's not too much info out there, but it was able to get me this far, and it seems that there may be some problems with the r600 and KMS, according to this page:
[https://bugs.freedesktop.org/show_bug.cgi?id=24357](https://bugs.freedesktop.org/show_bug.cgi?id=24357)

But now I am at an impass, because I am not all that versed in linux, and I don't know what the next step is. That bug report seems to imply that this can be fixed, but I don't know what to do. Can anyone help me?

---

### Post by handy on 2011-05-12
I'm using a HD 2600 Pro, GPU = R600.

I've been using the GIT driver stack for most of the last 18 months or so, with next to no problems, on Arch 64bit.

If you go to the first post in this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

& follow all of the instructions in the "Ubuntu Stuff:" section, in the order that they are laid out. You will have an upgraded kernel (which is working beautifully) & other upgraded packages (which are also working beautifully). This move will very likely solve the video problem that your computer is suffering from at the moment.

By the way, it may sound like it is heavy duty stuff to be changing your kernel & the other things that this how-to shows you how to do. In reality it is really all quite easy & painless. Don't be scared to hop in & follow the few steps involved. :)

---

### Post by osarusan on 2011-05-12
Hi handy,

Thanks for your reply.

I followed the instructions on the website and upgraded to the newest kernel. I was already using the xorg edgers PPA, so the kernel was really the only thing on the site that I hadn't already done. Unfortunately it hasn't changed. I'm still getting software rendering and a segmentation fault when I run glxgears.

Do you have any other suggestions?

---

### Post by alphacrucis2 on 2011-05-12
> **osarusan said:**
> 
Do you have any other suggestions?

How about trying the proprietary driver.

---

### Post by osarusan on 2011-05-13
Yeah, I can get fglrx to work. But I want to use the open source driver for now.

---

### Post by skywriter on 2012-03-11
Similiar bug. Ubuntu 10.04 kernel 3.0.0.16, xserver-org-video-radeonhd 1.3.


String from Xorg.0.log:
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so

$ LIBGL_DEBUG=verbose glxinfo|grep render
> libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
direct rendering: Yes
OpenGL renderer string: Software Rasterizer

---

