---
title: "Dual Monitor with two X-Servers"
date: 2009-08-03
forum: Multimedia Software
---

### Post by flower1024 on 2009-08-03
Hi,

i have a motherboard with an NV 9400 Chipset.

I use my TV on the HDMI out. I want to put a second LCD on VGACRT out.

I want to use two mice, two keyboards and two complete independant X-Servers. So my girlfriend is able to watch TV while i am playing surfing working or anything else.

How is it possobly to accomplish this?

 - It would be ok to forget about 3D and use one of the free drivers (nv / nouveau)
 - It would be ok to buy a seperate card (are there any acceptable intel cards out there?)

kind regards
florian

---

### Post by flower1024 on 2009-08-04
i see two possibilites:
 - using Xephyr
 - using two graphic cards from different vendors (and two xorgs)

can anybody say something about the xephy solution? does it work properly?

---

### Post by djurny on 2009-08-04
i would say that 2 independent Xorg servers would do the job..
be sure to give each a unique server layout and unique input devices..

also check the -isolateDevice and -novtswitch options!

---

