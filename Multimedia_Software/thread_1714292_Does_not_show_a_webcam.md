---
title: "Does not show a webcam"
date: 2011-03-25
forum: Multimedia Software
---

### Post by Zlatan on 2011-03-25
Hi, 10.10 does not show [this cam]("http://www.planetcams.eu/transl/watch.php?id=2859&type=1"), restricted extras installed. Pop-up says -application/x-mmsh decoder not found.
Anyone familiar with this? Thanks

---

### Post by no2498 on 2011-03-25
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto

---

### Post by Zlatan on 2011-03-30
> **no2498 said:**
> open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto

thanks for the reply. 
tried changing, tests for output do work but video in the link does not. v4l and v4l2 were available only for input where tests did not work, i have no cam on this laptop. and no auto plugin in input mode.
output lets me select following plugins: auto, x windows system (no Xv) and x window system (X11/XShm/Xv)

---

### Post by no2498 on 2011-03-30
set it to this output lets me select following plugins: auto
click the bottom test button

---

### Post by Zlatan on 2011-03-31
> **no2498 said:**
> set it to this output lets me select following plugins: auto
click the bottom test button

upper (output) test button shows OK and bottom one gives a popup: Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

---

### Post by no2498 on 2011-03-31
try installing xawty
it loads a cam grabber with it
try the can in xawtv

---

