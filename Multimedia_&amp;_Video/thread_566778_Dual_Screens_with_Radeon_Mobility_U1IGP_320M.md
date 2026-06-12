---
title: "Dual Screens with Radeon Mobility U1/IGP 320M"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by Corgana on 2007-10-03
Yes, I've got direct rendering working, and I've been working on the dual-screen issue for at least the past 6 months.

Is there** ANY** way to get an extended desktop with this card? It's the only thing that's keeping me from switching to ubuntu full-time.

Even if I have to compile my own custom kernel, That's OK. This is just driving me crazy.

---

### Post by Corgana on 2007-10-15
Bump.

fglrx does not work with this card, and I'm thinking that the radeon and ati drivers can't handle dual-head.

I'd really hate to go back to windows, I was hoping with 7.10 and xorg 7.3 I could finally make the switch.

---

### Post by jetpeach on 2007-10-19
i too have the mobility U1, how did you get accelleration working?

---

### Post by Corgana on 2007-11-11
> **jetpeach said:**
> i too have the mobility U1, how did you get accelleration working?

Sorry about the delay, I've gone back to full-time windows so I don't check here much. Direct rendering worked right away for me with 7.10, And before I had to add the irqpoll parameter to the end of the ubuntu line in /boot/grub/menu.lst. There's a few threads around here about it I've seen.

---

