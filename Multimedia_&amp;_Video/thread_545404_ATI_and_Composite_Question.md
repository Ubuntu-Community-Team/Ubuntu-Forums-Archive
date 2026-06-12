---
title: "ATI and Composite Question"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by anomalz on 2007-09-07
I'm running 7.04 on a Thinkpad T60 w/ an ATI X1300 i have the Restricted Driver installed
fglrxinfo gives me:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6334 (8.34.8)

But when i enable the composite extension in my xorg.conf, the driver reverts back to the mesa driver

any ideas? i would like to run beryl again (had it running back in 6.06, then switched back to windows for some reason.. but im back now :) )

---

### Post by Steveway on 2007-09-07
If you use the restricted driver then you need to set up XGL.
There are plenty of How-to's for this, just search.

---

### Post by anomalz on 2007-09-07
thanks :)

---

