---
title: "LIRC receiver through devinput misbehaving"
date: 2008-08-18
forum: Multimedia Software
---

### Post by Skerit on 2008-08-18
I own a DVB-S2 Technotrend S2-3200 tv-tuner card, with built in IR receiver.

The receiver works just fine but its input is being treated as if it were a keyboard. (When using the terminal, for example, I can "type" with my remote)

I've tried setting up lirc to use the correct driver (devinput) in the hardware.conf file, but no luck.
The device is /dev/input/event8

I thought, once lirc was set up properly, this "functionality" disappears.

---

