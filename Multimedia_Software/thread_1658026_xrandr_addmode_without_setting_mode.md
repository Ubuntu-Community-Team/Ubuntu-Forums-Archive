---
title: "xrandr addmode without setting mode?"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Kareeser on 2011-01-02
Hi everybody,

Finally got my Audio Authority 9A60 to work with my Panasonic rear projection TV. I even managed to tweak the modeline to eliminate the overscan, woo! (Someday, I'll write a guide to collate all of the scattered ones out there, heh)

Instead of doing it through xorg.conf, I did it through xrandr, since the results were viewable without restarting X.

Anyways, here's the script I ended up coding so I could set it up at the push of a button:

```

xrandr --newmode "panasonic" 74.176 1720 1870 1926 2200 940 1022 1028 1125 Interlace
xrandr --addmode VGA-1 "panasonic"
xrandr --output VGA-1 --mode "panasonic"

```

The problem lies in the second xrandr command. The "addmode" switch adds the new modeline to my VGA output, except because the output still considers a (default) non-working modeline of 1024x768 to be "preferred", xrandr will attempt that incorrect mode after adding the new mode to the output. The third xrandr command corrects this by explicitly setting the desired mode.

Is there any way I can add a mode using xrandr without it automatically auto-configuring and starting the output?

Solution could involve making an xorg.conf file, since I don't need one (hence there isn't one) right now, but I am not sure whether the modeline can be added to an output if it is not connected already. Since I am using a laptop, VGA-1 won't be connected most of the time.

**Edit**: A second solution could involve the --preferred switch in xrandr...

---

