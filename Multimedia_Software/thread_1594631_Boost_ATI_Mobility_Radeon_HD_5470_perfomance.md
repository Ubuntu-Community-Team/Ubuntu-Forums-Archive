---
title: "Boost ATI Mobility Radeon HD 5470 perfomance"
date: 2010-10-12
forum: Multimedia Software
---

### Post by morefeo on 2010-10-12
Hi everybody,

I've got a laptop with a 1 GB ATI Mobility Radeon HD 5470 graphics card, and was walking around thinking how to boost it in perfomance.

I've got the default drivers suggested by Maverik (I think it's the last one, 10.9), and I've made some changes to the xorg.conf (see below), with an i5 2,4ghz processor and compiz enabled with some effects I get 800-1000 fps with fgl_glxgears and 2000~2500 fps with glxgears, is there any way, any tweaks to improve it?

I've made a lot of search, but information is old or unclear.


Xorg.conf :
> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
    Option "AGPMode" "8"
    Option "AGPFastWrite" "true"
    Option "DisableGLXRootClipping" "true"
    Option "AddARGBGLXVisuals" "true"
    Option "AllowGLXWithComposite" "true"
    Option "EnablePageFlip" "true"
EndSection

Thank you.

---

### Post by morefeo on 2010-10-13
Moo foo zoo?

---

### Post by morefeo on 2010-10-15
Sum sum, laka laka lakasum.

---

### Post by ashwinhgtx on 2010-10-16
I don't have an answer to your query. But I have a question. Are you having any problems using the proprietary driver on the 5470? I still haven't installed it as I'm scared that something might go wrong as I have some sensitive data on my laptop. Did you install it using the Additional Drivers utility? Is Compiz working okay for you? I just want to know if it's usable.

---

### Post by morefeo on 2010-10-19
Usable out of the box with the drivers from hardware drivers, some lagging effects while moving windows and some video player issues, ok with compiz.

---

