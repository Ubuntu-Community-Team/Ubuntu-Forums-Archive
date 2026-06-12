---
title: "Quadro FX 3400 can't reach max resolution"
date: 2011-09-23
forum: Multimedia Software
---

### Post by doriad on 2011-09-23
I have an NVidia Quadro FX3400. According to this:

[http://reviews.cnet.com/graphics-cards/hp-nvidia-quadro-fx/4505-8902_7-30999343.html](http://reviews.cnet.com/graphics-cards/hp-nvidia-quadro-fx/4505-8902_7-30999343.html)

it has a very high max resolution (3840 x 2400). However, it works fine at 1920x1200, but when I try to go higher than that (my 30" monitor wants 2560x1600), it doesn't work. I am using the "additional driver" that Ubuntu 11.04 recommends. Higher resolutions are listed in the NVidia config window, but if I choose one, it says "mode not supported".

Any thoughts on how to get this card to output that resolution?

Thanks,

David

---

### Post by BicyclerBoy on 2011-09-23
Are you using DVI or DP cable ?
Because you can not go very high with HDMI or single link DVI.

---

### Post by doriad on 2011-09-24
My video card only has DVI ports, and I am just using a single one. It does have two ports though - if I plugged a second cable from the second port on the card to the second port on the monitor is that supposed to work?

Thanks,

David

---

### Post by BicyclerBoy on 2011-09-24
Only if it is an IBM T221.
I do not know of any modern monitor using dual/multi cables..
The multiple cable arrangement was used as a work-around to the video card limitations.

Are you sure your DVI cable is dual link; check wikipedia plug image/diagrams.

Maybe post the /var/log/Xorg.0.log file..

---

