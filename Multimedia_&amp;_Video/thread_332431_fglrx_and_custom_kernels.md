---
title: "fglrx and custom kernels"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Absurd on 2007-01-06
Good evening everyone.

Well, I've recently been compiling a custom kernel (due to boredom) and everything seems fine except that I can't get direct rendering to work.

when I enter "$ fglrxinfo" it tells me

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

and when I enter "$ glxinfo | grep direct" I get 

> direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I have the xorg-driver-fglrx installed and direct rendering works fine with the regular Ubuntu kernel.

So I'm wondering if anyone knows how I can get it working with a custom kernel.

---

### Post by pay on 2007-01-07
When you update the kernel you have to install the drivers again because the drivers are sorta like plugins for the kernel (atleast that's my understanding).

---

### Post by Absurd on 2007-01-07
Nah, I already tried that and no dice.

I'm going to try manually building the module tomorrow.

---

