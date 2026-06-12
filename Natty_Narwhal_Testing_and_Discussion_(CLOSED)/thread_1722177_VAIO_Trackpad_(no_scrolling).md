---
title: "VAIO Trackpad (no scrolling)"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shoot2kill on 2011-04-05
Hi, I have a Sony VAIO laptop which has a multi-touch trackpad. The trackpad is working, although it is only recognizing single touches.

I don't really need the multi-touch aspect of it, however I would like to get the vertical scrolling working (right edge of trackpad)

Any help greatly appreciated.

Edit
----
Laptop model: VPCEB3J1E

---

### Post by crusstt on 2011-04-05
Hi,

I had the same issue and almost same model Vaio.

Add the following line to /etc/modprobe.d/psmouse.conf

options psmouse proto=imps

(it's the only line in my file)

Then restarted my pc.

If you search for LaptopSonyVaioFSeriesNatty in Goo... and go down to the Keyboard and Touchpad section there are different steps to do basically the same thing.

Hope it helps

---

### Post by onemanclapping on 2011-04-07
Works in HP mini 311 too! Cheers.

---

### Post by manzdagratiano on 2011-04-07
> **shoot2kill said:**
> Hi, I have a Sony VAIO laptop which has a multi-touch trackpad. The trackpad is working, although it is only recognizing single touches.

I don't really need the multi-touch aspect of it, however I would like to get the vertical scrolling working (right edge of trackpad)

Any help greatly appreciated.

Edit
----
Laptop model: VPCEB3J1E

You may want to try:

gconf-editor -> desktop -> gnome -> peripherals -> touchpad

and enable all the relevant options. I have a VAIO VGNAR520E, and my vertical scroll works, and my scroll_method is set to 1. I know that multi-touch may be enabled by setting it to 2, though I never tried that.

---

