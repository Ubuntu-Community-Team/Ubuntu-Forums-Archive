---
title: "Two SBlives for DJ'ing"
date: 2006-02-23
forum: Multimedia &amp; Video
---

### Post by pksings on 2006-02-23
I have two identical SBlives (Not Dell) and the system only recognizes one at a time, sort of. In dmesg it shows two cards were found with different addresses, but only one shows in /proc/interrupts, lspci shows two cards. /proc/asound only contains card0 and /proc/asound/devices only shows card 0. So my current belief is that is an alsa configuration problem since the O/S recognizes two separate cards.

Is there a way to tell via modprobe.d or something to make one card at a specific address card0 and the other card1?  I have tried several different versions of asound.conf to no avail.

alsaconf doesn't exist and I cannot find which package would install it. I initially though alsa-utils but that does not. Or is this a kernel parameter?

I'm stumped...too much I don't know.

PK

---

