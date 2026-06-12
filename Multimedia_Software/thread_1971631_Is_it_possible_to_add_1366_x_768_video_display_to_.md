---
title: "Is it possible to add 1366 x 768 video display to 10.04?"
date: 2012-05-02
forum: Multimedia Software
---

### Post by Manyette on 2012-05-02
Can anyone tell me if it is possible to add my supported native resolution of 1366 x 768 to 10.04 Lyric Lynx? It seems it should be possible, but I haven't been able to find a way to do so.

---

### Post by TBABill on 2012-05-02
My man with the USMC emblem as his avatar! Awesome!

Do you have the right driver installed? Wondering if the proprietary driver for your card would permit the higher resolution.

---

### Post by Manyette on 2012-05-02
Hi TBABill

Sorry, but I should have mentioned it's a Laptop with the I7 intel graphics.
The screen native resolution is 1366 x 768. It seems like it should be possible although xrandr says the maximum is 1024 x 768.

---

### Post by Manyette on 2012-05-03
<bump>

Would a newer kernel permit this?

---

### Post by BicyclerBoy on 2012-05-03
The HD3000 graphics in SBA i7 requires a recent kernel if you want more than 2d framebuffer.

The kernel should work with 10.04 LTS.
A package managed option would be:
[https://launchpad.net/~kernel-ppa/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~kernel-ppa/+archive/ppa?field.series_filter=lucid)

I would also use the xorg-edgers ppa to update the user-space Xorg & intel drivers.

---

