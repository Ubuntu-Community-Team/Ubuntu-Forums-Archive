---
title: "glx 1.3+ with Intel"
date: 2010-03-05
forum: Multimedia Software
---

### Post by kennyd on 2010-03-05
Hi there,

I need glx 1.3+ to run some executables:

```

$ glxinfo | grep version
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 2.0 Mesa 7.4
OpenGL shading language version string: 1.10

$ lspci | grep Display
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

$ glxinfo | grep Intel
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090326 2009Q1 RC2 x86/MMX/SSE2

```I've gone through some of the threads here and tried to just update everything.  I seem to not be able to get anything more current than 1.2.  It seems that most people don't have this problem if they have NVIDIA and most other people don't really need 1.3+.

---

### Post by vistovistor on 2010-04-14
bump, i have wasted a few hours trying to get this to work. I have the exact same outputs as your commands.

---

### Post by Schnippe on 2010-06-06
Me too:```

$ glxinfo | grep version
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
$ lspci | grep Display
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
$ glxinfo | grep Intel
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2

```

---

### Post by Yellow Pasque on 2010-06-06
> **Schnippe said:**
> Me too:```

$ glxinfo | grep version
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
$ lspci | grep Display
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
$ glxinfo | grep Intel
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2

```
Use the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by bobcollard on 2010-10-05
> **Temüjin said:**
> [COLOR=Red]What would happen if your disk died right now?[/COLOR]
I would replace it with a bigger HD and restore from a daily backup.  What about you?

---

### Post by bogdarnet on 2012-01-18
> **Temüjin said:**
> Use the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I'd like to do this... how?

---

### Post by bogdarnet on 2012-01-18
More specifically, I've added the repository, but I'm not sure how to get GLX 1.3 running from it...

---

