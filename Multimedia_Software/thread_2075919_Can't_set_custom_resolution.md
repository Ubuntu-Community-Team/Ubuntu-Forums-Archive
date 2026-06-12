---
title: "Can't set custom resolution"
date: 2012-10-24
forum: Multimedia Software
---

### Post by mycomputeralias62494 on 2012-10-24
I tried using this guide here to set my resolution to 1176x664 but it didn't work.
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

I got to the point where I input
xrandr --addmode HDMI-0 1176x664_60.00

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30


Edit: Oh and I am using a geforce 210 gpu

---

### Post by dbuday on 2012-12-06
Same problem here.
Same error output.

Anyone?

---

