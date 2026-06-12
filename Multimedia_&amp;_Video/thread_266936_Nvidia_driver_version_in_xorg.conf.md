---
title: "Nvidia driver version in xorg.conf"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by enopepsoo on 2006-09-28
Hello,

I used the Envy script to isntall drivers for my Nvidia 6500 card.  This is working awesome (screensavers etc), but in my xorg.conf it says this
```
Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6200?]"
    Driver         "nvidia"
EndSection
```
Which is wrong I think.  Is it ok?

Shouldn't it say 
```
        Option "RenderAccel" "true"
```
in there somewhere so I can get some kind of a performance boost?:confused: 

thanks!

---

### Post by tseliot on 2006-09-28
"RenderAccel" is set to "true" by default, therefore there's no need to put it in your xorg.conf any more.

You need to put it in your xorg.conf only if you want to disable it (and then  it would be "RenderAccel" "false").

---

