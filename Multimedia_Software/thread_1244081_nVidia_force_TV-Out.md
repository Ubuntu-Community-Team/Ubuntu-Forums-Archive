---
title: "nVidia force TV-Out"
date: 2009-08-19
forum: Multimedia Software
---

### Post by illektr1k on 2009-08-19
Doesn't seem to be a "force TV detect" button in the nvidia-settings :( 

Any ideas anyone? Cant really do the xorg.conf thing as the laptop does a whole bunch of different display configs, just doesnt detect when i go through a  S-Video -> RCA adapter.

---

### Post by illektr1k on 2009-08-26
Adding

```
Option "ConnectedMonitor" "TV"

```

to the devices section of the xorg.conf results in there permanently being available to select... A messy hack, but it works...

---

