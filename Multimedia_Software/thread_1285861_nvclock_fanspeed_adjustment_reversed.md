---
title: "nvclock fanspeed adjustment reversed"
date: 2009-10-08
forum: Multimedia Software
---

### Post by moritz-s on 2009-10-08
I'm running a 9600 GT with the 190.x Nvidia drivers. I tried to manually reduce the fan speed of the card, which was the noisiest component at some point. The package nvclock and nvclock_gtk offer fan speed adjustment and recognize the card just fine. However, after reducing the speed from 65.1% (which was the default value), it always reverted back more or less instantly.

Annoyed, I tried increasing the fan speed to see if it'd stick -- it did. And it also significantly reduced the noise level. Apparently there is a bug and the adjustment works in reverse. Odd! A command line nvclock -i also reports a fan speed of 100% after adjustment.

This is on 9.10 beta now, but the same thing happened with 9.04.

Maybe this helps someone in the future.

---

