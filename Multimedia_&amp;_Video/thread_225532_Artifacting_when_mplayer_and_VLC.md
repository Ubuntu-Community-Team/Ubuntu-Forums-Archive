---
title: "Artifacting when mplayer and VLC"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by harryhoudini66 on 2006-07-29
This happens only when I use XGL/COmpiz session. I am sure it is related to the driver. Anyone know how to fix it?


I have an eVGA Nvidia 6800GT 256 PCI-X

---

### Post by harryhoudini66 on 2006-07-30
bump

---

### Post by croak77 on 2006-07-31
What video driver are you using in mplayer? Try changing it to opengl or opengl2.

---

### Post by harryhoudini66 on 2006-07-31
How do I do that? I downloaded the driver from the repositories.

---

### Post by croak77 on 2006-07-31
Run gmplayer, go to Preferences -> Video Tab. There should be a bunch of drivers to choose from. Or run mplayer from the command line with the -vo switch. mplayer -vo gl2 video.avi.

---

