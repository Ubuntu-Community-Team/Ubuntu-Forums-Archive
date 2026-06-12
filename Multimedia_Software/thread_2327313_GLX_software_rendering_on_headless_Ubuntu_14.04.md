---
title: "GLX software rendering on headless Ubuntu 14.04"
date: 2016-06-09
forum: Multimedia Software
---

### Post by bfree on 2016-06-09
I have a headless GLX/OpenGL rendering server that works great with GPU hardware using proprietary drivers (nvidia-340).


I want to be able to disable hardware GPU rendering and do some temporary software rendering (Mesa) for benchmarking purposes.

However, everything I've tried kills X/GLX rendering - with various error messages, depending the approach I take.  I've tried nouveau drivers, I've tried building Mesa from source, etc.

Can anyone point me to a group/resource that has working experience setting up GLX software rendering on Trusty?

Thanks!

---

### Post by T.J. on 2016-06-11
I can help you a bit. 

When you install the proprietary Nvidia driver, you actually replace Mesa's GLX with Nvidia's.  In order to properly benchmark software render, you will probably have to remove it in order to get some control over the X11 stack, although you can try disabling the GLX extension in /etc/X11/xorg.conf and see if Nvidia's driver will even load with GLX disabled.

Mesa is also hardware accelerated.  If you want to test strict software rendering on a default system, you will have to remove the Nvidia driver, so you are using Mesa. Then disable the GLX extension to force it to use software render.  

As a warning, it becomes extraordinarily slow if you do, and you may lose certain resolutions.

You should also install mesa-utils.  You will find the output of glxinfo to be useful.

---

