---
title: "WebGL issues"
date: 2011-03-16
forum: Multimedia Software
---

### Post by EtherealOne on 2011-03-16
I am having issues getting any browser to run WebGL (all tests return "This Browser does not support WebGL" on Chromium 10, Chrome-stable 10).

The results of glxinfo are : 
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series           
OpenGL version string: 3.3.10524 Compatibility Profile Context
OpenGL shading language version string: 3.30

I am using an ATI 4890 and running 64 bit Ubuntu.

---

### Post by papaours on 2011-03-17
Hey,
It seems they disabled webgl in Chrome, see [http://www.google.com/support/forum/p/Chrome/thread?tid=4ed2cebe3379b1a2&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=4ed2cebe3379b1a2&hl=en)

You have to add --ignore-gpu-blacklist to the chrome command line in the launcher to re-activate it.

However chrome still fails half of the time to display a webgl canvas when I refresh a page.

---

### Post by EtherealOne on 2011-03-17
Thank you very much, this appears to have worked.

---

