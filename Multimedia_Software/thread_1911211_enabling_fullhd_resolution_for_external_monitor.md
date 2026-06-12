---
title: "enabling fullhd resolution for external monitor"
date: 2012-01-18
forum: Multimedia Software
---

### Post by nivwusquorum on 2012-01-18
I recently bought an external monitor which supports fullhd resolution and I am trying to get it to work.

I am using fglrx as a driver and my card is ATI Radeonhd 34xx.

Initially I tried to set it using gnome-display-properties.

I wouldn't let me set resolution to higher than 1600x900 (which happens to be resolution of my primary laptop display).

Then I went on to try this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Finally I was trying to add custom xrandr mode created by cvt by when I was trying to add it to my device it printed:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

Anybody has some idea?

---

