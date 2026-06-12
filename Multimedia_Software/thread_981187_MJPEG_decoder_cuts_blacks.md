---
title: "MJPEG decoder cuts blacks"
date: 2008-11-13
forum: Multimedia Software
---

### Post by bearing on 2008-11-13
In JPEG pictures and MJPEG videos the YCbCr component values range from 0-255.

In other compressed video formats (like MPEG2) the YCbCr component values range from 16-235.

When I play MJPEG files in Dragon or Totem movie player the decoder probably expects 16-235 values from my MJPEG videos. All values below 16 are black and all values above 235 are white; pictures looks like crap.

How can I find out which decoder is used for my MJPEG files?

Is there some sort of configuration file in which I can change how YCbCr is converted to RGB?

---

