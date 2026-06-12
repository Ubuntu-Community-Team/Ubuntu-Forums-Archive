---
title: "Green screen .. help please"
date: 2009-01-21
forum: Multimedia Software
---

### Post by ebike on 2009-01-21
Hi All,

I have been running Mythbuntu quite sucessfully for some time, however the last time I re-booted the machine, I have found that whenever I play a recording or watch liveTV all I get is a green screen, I can see the program content ... it just all green.

(There may have been some recent updates ... and this is the 1st time I have re-booted since ..)

It doesn't seem to be Xorg, the Plasma, or the Intel driver as I can use it fine as a normal computer in full color, it is only when I am using Mythtv for recordings (that previously were fine in full color) or LiveTV that I get the issue.

It seems the video decoding is broken for some reason. 

Can anyone tell me what to do to resolve this?

---

### Post by ebike on 2009-01-22
Ok, an update. It seems that xvmc is broke for resolutions > 720x560 with the latest intel driver.

A workaround is to use OpenGL as the renderer until the driver issue is resolved.

---

