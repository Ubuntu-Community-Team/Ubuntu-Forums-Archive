---
title: "How do I: Xinerama + nvida + i810 + glxgears?"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by borzwazie on 2006-12-06
Hi all -

So I have the following setup:

I have an IBM box here at work with builtin Intel video. I added an nVidia GF2MX400 pci card and managed to get dual display (Xinerama) working after a bit of messing about.

I know that using Xinerama disables DRI.

My question is this: When I run glxgears, I get this:

$ glxgears
Error: couldn't get an RGB, Double-buffered visual

Is is possible to get OpenGL rendering to work at all (even software!) in this config?

I have attached my xorg.conf file (xorg.conf.txt).

Thanks!

---

