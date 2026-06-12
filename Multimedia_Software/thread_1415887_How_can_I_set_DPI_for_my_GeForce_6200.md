---
title: "How can I set DPI for my GeForce 6200?"
date: 2010-02-25
forum: Multimedia Software
---

### Post by saltydog on 2010-02-25
I'm on Karmic, nvidia GeForce 6200 and nvidia-185 drivers.

My monitor is an LCD ACER p191w, 1440x900, but it can't be recognized by xorg. From the log:

```
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
```

This is also confirmed by running:

```
xdpyinfo | grep solution
resolution:    75x75 dots per inch

```

How can I force DPI to 89x87 in my xorg.conf?

---

