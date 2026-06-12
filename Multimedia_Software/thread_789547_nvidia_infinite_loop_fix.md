---
title: "nvidia infinite loop fix?"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Seks on 2008-05-10
[hi there, using nvidia geforce FX 5500 with nvidia-glx-new driver on a fresh, native ubuntu install]

In windows, in order to get my gfx card to not BSOD me with "infinite loop in nv4_disp.dll", I had to install a patch.

I have the same problem in hardy, just no error messages, X crashes completely or I am thrown back to the login screen after a few minutes of effects. Wobbily windows and glxgears work fine for a little bit but then everything locks up. Even WITH visual effects set to none it crashes as long as the driver is installed. I have tried envy.

Any suggestions, patches?

---

### Post by Seks on 2008-05-10
Nevermind. I found the solution.

adding

    Option "NvAGP" "1"

to "Device" in xorg.conf

---

