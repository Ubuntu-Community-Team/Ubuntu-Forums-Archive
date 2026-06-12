---
title: "Kernel panic - Labtec Webcam Pro"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by wobster on 2005-12-30
Hi everyone,

as many people recommended the Labtec webcam I bought one myself recently. 
The cam is identified correctly but any access to /dev/video0 causes an immediate kernel panic - latest kernel on breezy. 

What could that be? Or, how can I grab the drivers output so that I can at least post it here? Anyone encountered that and has found a solution?


[Update]
I just installed the latest spca5xx driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html). That solved the problem. 
If any ubuntu maintainer is reading this: Please add it! I have gcc 4.0 so the module can only be loaded with modprobe --force-vermagic. That's pretty annoying (or can I add that commands in /etc/modules too?)

Anyway. Seems to work out.

---

### Post by heldal on 2006-01-11
My Labtec camera works (sort of) with the latest (20060101) spca5xx driver, but it's still not stable. A kernel-panic happens sooner or later if I move the camera around with a viewer running (camorama/gnomemeeting/spcaview etc). Maybe it's just my imagination, but it seems to freeze more frequent if there is more detail in the picture (especially bright daylight). More detail may possibly require more buffer-space in the kernel somewhere, but that's just a guess so far.

(update) Tried (20060101) with same result now on both a Dell i8200 laptop and an abit-based homebrew desktop. Both crashes every now and then when the camera is moved around, and when going fullscreen in gnomemeeting. Seems like gnomemeeting i re-initialising the camera when going fullscreen so this may be related to some race-condition in buffer-handling in the driver somewhere.

//per

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to download and build drivers for many webcams.

---

### Post by heldal on 2006-01-17
[QUOTE=chele]EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to download and build drivers for many webcams.[/QUOTE]

Well, a cool utility to download/compile/install doesn't help much. Btw, in my cast this isn't an ubuntu-specific problem. The Labtec Webcam Pro I have has been causing crashes with every distro/kernel-release/spca5xx-driver-release combination I've come across in the last year or so. Even custom-built kernels stripped to the minimum features necessary to support the computer used show the same symptom.

Wonder if the same problem apply to all cams supported by the spca-driver, or if its just the Labtec pro.

//per

---

