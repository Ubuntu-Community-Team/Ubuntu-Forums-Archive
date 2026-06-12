---
title: "GLX is not supported with the Composite Extension"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by ponx on 2007-04-08
Hi,

I have a GeForce 4 Ti4600 and I have the legacy nvidia driver installed (it wouldn't work with the latest unified driver; guess the card is quite old now...)

I now have a desktop with the resolution I want but I don't seem to have any 3D acceleration.

As far as I know all my config is fine, but when I checked the Xorg log I found this error:

"(EE) GLX is not supported with the Composite extension"

Anyone know how I get around this..?  (How do I, or indeed is it safe to, disable the Composite extension?)

ponx

---

### Post by Draek on 2007-04-13
I have the same problem, trying to figure out how to make it work.

---

### Post by dmoney on 2007-04-13
Just add this line to the bottom of your xorg.conf file(or change it if it already exists):

```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

---

