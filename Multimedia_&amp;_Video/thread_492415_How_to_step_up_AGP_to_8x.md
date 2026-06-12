---
title: "How to step up AGP to 8x"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by ajpug on 2007-07-04
Hi all.

I have an ATI Radeon x700 Pro, the AGP version. The problem is that in the dmesg it shows 
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[ 1996.212513] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[ 1996.212584] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode

the problem is that my card is AGP 8x, not 4x. How can I enable the 8x?
Also, do you know how to enable 3D acceleration?

Thanks a lot,
ajpug

---

### Post by ajpug on 2007-07-05
Anybody has any idea at all? I thought it was going to be something silly ... but the lack of replies is worrying me.
:(

ajpug

---

### Post by ajpug on 2007-07-10
I am very surprised nobody knew the answer.
In any event, I found the solution. Just add the following to your xorg.conf, in the appropriate section:
Option          "AGPMode"       "4"

ajpug

---

