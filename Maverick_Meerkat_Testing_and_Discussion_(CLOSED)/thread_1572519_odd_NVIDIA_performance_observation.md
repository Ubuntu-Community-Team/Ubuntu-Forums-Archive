---
title: "odd NVIDIA performance observation"
date: 2010-09-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by teachop on 2010-09-11
I have been beta-testing on several machines.  One is a nearly-new Dell E6510 w. core i7 and nvidia graphics.  It has been allergic to most linux I have tried on it, but this is the strangest thing yet:

I was trying to track bug 630299 down a bit and found out this:

Clean cross-compiling an arm linux (2.6.30 + busybox + qt/embedded):

    with nouveau driver = 90 minutes.

    with NVIDIA driver = 113 minutes.

What in the world?  The reason I started messing with this, is that I noticed that with proprietary NVIDIA enabled on this laptop, the interface is a jerky dog, doesn't scroll smoothly, and background tasks cause great disturbance in the user interface.  Like my old Sempron laptop, but this is an i7!  With the nouveau driver, except for the super annoying bug 630299 issue, all is well.

No idea...  yes I tried turning off compiz with NVIDIA, and it isn't helping.

---

### Post by MacUntu on 2010-09-11
Seeing something similar here. Eg. a fullscreen gnome-terminal lags when running 'cat /var/log/messages' while it runs fine when I unmaximize the window. With nouveau it always runs smooth and fast.

This might also be the problem for the terrible performance I'm seeing in Unity (UNE) from time to time: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/627531](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/627531)

---

