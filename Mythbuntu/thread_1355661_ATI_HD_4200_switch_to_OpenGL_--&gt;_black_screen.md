---
title: "ATI HD 4200 switch to OpenGL --&gt; black screen"
date: 2009-12-15
forum: Mythbuntu
---

### Post by Markus72 on 2009-12-15
Hi,

I've got a brand new mainboard with ATI HD4200 IC.
Proprietary Ati drivers are installed and working.
fglrxinfo states that it's fine and also OpenGL is supported.

If I now check the OpenGL vertical synch option and watch TV, mythfrontend crashes - black screen, killing does nothing. Only a reboot helps.

Similar to that, the Mythfrontend stays black if I change the rendering engine from QT to OpenGL.

Neither the myth-logs nor the xorg log seem to give any clue.

Do you have? Help is very appreciated.

Thanks
Markus

---

### Post by nickrout on 2009-12-15
The obvious solution is to leave them at QT.

Is there a reason you want openGL, or are you just trying to break a system that was working ok? :)

---

### Post by Markus72 on 2009-12-16
Jepp, I like to break things ;-)

No, there were two reasons:

a) somewhere during the config I read to "use OpenGL on more powerful grafic cards"... maybe that's just nonsense...

b) I'd like to use the OpenGL vertical synch option

Simply: the TV playback is flickering a bit and I want to optimize it. I used it in my former system with an NV card.
Now it's a ATI...

And it shouldn't freeze anyway, right? :-)

Any clue?

Markus

---

### Post by nickrout on 2009-12-16
ati is generally a bad choice for myth. Beyond that I don't know how to fix your problem sorry.

---

### Post by Markus72 on 2010-01-07
I've got the impression that MPEG2 accelaration works nicely with ATI, only MPEG4 is currently not supported... but it's coming...

---

