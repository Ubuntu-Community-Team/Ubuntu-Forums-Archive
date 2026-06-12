---
title: "Drivers for ATI card?"
date: 2009-06-13
forum: Multimedia Software
---

### Post by Cam42 on 2009-06-13
Are there Ubuntu drivers out there for an ATI Rage Pro 3D card?
It's older, but I'd like to be able to use some of the desktop effects in ubuntu...

---

### Post by utnubuuser on 2009-06-13
the open source driver in the repos should give you 3d rendering.  You might have to make some changes in your xorg.conf file to get it set up properly.

have you tried > glxinfo | grep render to see what's installed?

---

### Post by Cam42 on 2009-07-02
Okay, how do I edit the xorg.conf? I found what I need to edit on another forum, I just can't figure out how to edit the file.
typed what you said into a terminal got > direct rendering: Yes
OpenGL renderer string: Software Rasterizer

what does this mean?

---

### Post by Cam42 on 2009-07-02
also, I figured out the card is an AGP ATI Rage 128 Pro

---

### Post by philcamlin on 2009-07-02
try envy :popcorn:

it detects your card then installs the driver

---

