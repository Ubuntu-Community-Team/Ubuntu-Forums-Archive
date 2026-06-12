---
title: "3D acceleration? ... maybe"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by ajpug on 2007-07-05
Hi all.

I am currently using the open-source ATI drivers with my Radeon X700 PRO and according to the wiki [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html") my 3D acceleration is enabled.

The weird thing is that if I try to run Google earth, for example, the whole thing is super slow!
Also, I have noticed the following line in the output of 'glxinfo':

OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL

I am worried from "AGP 1x". Is this normal?
Another thing I have noticed is that in the hardware profile my video card is recognized as PCIE, but it is AGP!

Any help is very much appreciated.

ajpug

---

### Post by Motoxrdude on 2007-07-05
> **ajpug said:**
> Hi all.

I am currently using the open-source ATI drivers with my Radeon X700 PRO and according to the wiki [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html") my 3D acceleration is enabled.

The weird thing is that if I try to run Google earth, for example, the whole thing is super slow!
Also, I have noticed the following line in the output of 'glxinfo':

OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL

I am worried from "AGP 1x". Is this normal?
Another thing I have noticed is that in the hardware profile my video card is recognized as PCIE, but it is AGP!

Any help is very much appreciated.

ajpug

Post the output of
```
glxinfo | grep direct
```

---

### Post by ajpug on 2007-07-06
The output is:
direct rendering: Yes

ajpug

---

### Post by Motoxrdude on 2007-07-06
> **ajpug said:**
> The output is:
direct rendering: Yes

ajpug

You have direct rendering, but idk why its slow, very odd. What video card are you using? Are you using feisty? If so are you using the proprietary drivers(System>>Administation>>Restricted Drivers Manager)? 

When you enter in ```
glxgears
``` is it smooth or jerky?

---

### Post by ajpug on 2007-07-06
I am using an ATI Radeon x700 PRO, I am using Feisty and I am using the open source ati drivers.
When I enter "glxgears" a window appears for a second and then it disappears and the following error message  appears:
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting

Any idea what this is?

Thank you for your help.
ajpug

---

