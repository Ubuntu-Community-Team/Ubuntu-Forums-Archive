---
title: "ATI Mobilty U1 - Drivers"
date: 2008-05-06
forum: Multimedia Software
---

### Post by gunner_uk2000 on 2008-05-06
My laptop's VGA card identifies itself as ATI Mobilty U1, which is not even mentioned on ATI's website. The only place I was able to get drivers for it was on the manufactures website.

Anyone know if there are Linux drivers for this card? Or know what this card is actually known as to ATI?

Thanks,

Gunner

---

### Post by edlutz on 2009-01-17
The question was asked several months ago, but since it was not answered, here's a hint:
there are at least two different drivers that work well with U1 for acceletarion.
They are available on Ubuntu repositories.
Usually, the board is detected automatically during installation and a good driver is installed.
If for some reason you decide to try another driver, just install it with synaptic and change the corresponding reference on /etc/X11/xorg.conf.
I tried both drivers and they both worked fine.

---

