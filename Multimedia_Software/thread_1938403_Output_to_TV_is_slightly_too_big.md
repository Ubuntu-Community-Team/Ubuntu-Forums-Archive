---
title: "Output to TV is slightly too big"
date: 2012-03-09
forum: Multimedia Software
---

### Post by doriad on 2012-03-09
I am trying to use a tv as my monitor. It seems to work, but there are about a "taskbar worth" of pixels that aren't displayed around the edges (i.e. it seems to display slightly larger than the tv). Is there anything that can be done to fix this? The resolution seems correct (1920×1080) and everything looks good, I just can't see the edges.

Any ideas?

Thanks,
David

---

### Post by BicyclerBoy on 2012-03-10
This sounds like a classic over-scan problem.

The best solution is to try configure the TV to not over-scan by setting:
- the input to type "PC" (digital connection)
- find settings "just-scan"
- "direct pixel mapping"
- "one to one mapping"

Some TVs require you to select professional mode first.
 
If the TV (cheap model) has no over-scan controls then you can try the video card adjustment.
The nVidia video driver has excellent over-scan adjustment.
The intel driver needs some xrandr tricks.

---

