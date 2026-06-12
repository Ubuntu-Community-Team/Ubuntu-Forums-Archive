---
title: "Stellarium problem with st_GL.so"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-02-25
Like the title says, when I try to start Stellarium, it sefaults thusly:

```
libEGL warning: use software fallback
libEGL warning: unable to load st_GL.so
QEglContext::createContext(): Unable to create EGL context: "Success (0x3000)" 
libEGL warning: use software fallback
QGLTemporaryContext: Error creating EGL context.
QGLTemporaryContext: Error creating EGL context.
QGLContext::makeCurrent(): Cannot make invalid context current
QGLContext::makeCurrent(): Cannot make invalid context current
QGLContext::makeCurrent(): Cannot make invalid context current
QGLContext::makeCurrent(): Cannot make invalid context current
QGLContext::makeCurrent(): Cannot make invalid context current
QGLContext::makeCurrent(): Cannot make invalid context current
QGLContext::makeCurrent(): Cannot make invalid context current
Segmentation fault (core dumped)
```

The file st_GL.so exists at /usr/lib/egl, where it has always been. Any idea what could be going on?

---

### Post by Yofel on 2011-02-25
I can confirm that - could be [https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725148](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725148)
since I'm not sure I filed it as [https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725326](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725326) (private until retraced)

---

### Post by sgage on 2011-02-25
> **Yofel said:**
> I can confirm that - could be [https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725148](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725148)
since I'm not sure I filed it as [https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725326](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/725326) (private until retraced)

Glad I'm not alone... I added myself to your bug report.

Thanks!

---

### Post by PaulW2U on 2011-02-25
I've added some info to bug #725148. I'm not sure how relevant it is but at least I could use stellarium in safe-mode under previous versions of Ubuntu due to bug #481669. Now, using 11.04, even that is not possible and now the program fails to display anything at all.

---

### Post by sgage on 2011-02-25
> **PaulW2U said:**
> I've added some info to bug #725148. I'm not sure how relevant it is but at least I could use stellarium in safe-mode under previous versions of Ubuntu due to bug #481669. Now, using 11.04, even that is not possible and now the program fails to display anything at all.

I've never had any trouble with Stellarium until today. I'm pretty sure it was fine yesterday. I did update to the new xserver and nvidia today...

---

### Post by PaulW2U on 2011-02-25
> **sgage said:**
> I've never had any trouble with Stellarium until today. I'm pretty sure it was fine yesterday. I did update to the new xserver and nvidia today...
I don't have a problem with 10.04, just 10.10 where I have to run in safe mode and now 11.04 where stellarium won't start at all. I'm not sure at this stage if the current problem is new or related to my ATI video card as per bug #481669.

---

### Post by sgage on 2011-02-25
> **PaulW2U said:**
> I don't have a problem with 10.04, just 10.10 where I have to run in safe mode and now 11.04 where stellarium won't start at all. I'm not sure at this stage if the current problem is new or related to my ATI video card as per bug #481669.

I've been running Stellarium in 11.04 right along with no issues until today.

---

### Post by daggerstab on 2011-02-28
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/724867](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/724867)

Does it work after the last update?

---

### Post by PaulW2U on 2011-02-28
> **daggerstab said:**
> [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/724867](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/724867)

Does it work after the last update?
For me yes but has crashed a couple of times within the first minute of use. Safe-mode, which I have to use when running Lucid or Maverick doesn't work at all and crashes with a segmentation fault. :(

When I have time I'll go through the bug reports and see if there's anything I can add to.

---

