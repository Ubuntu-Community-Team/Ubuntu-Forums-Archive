---
title: "open_gl totally broken"
date: 2009-07-22
forum: Multimedia Software
---

### Post by dea.dB.ear on 2009-07-22
So I have used blender for awhile and now I can't.

Everytime I try to start any opengl program, including fglrxinfo (which I'm not sure how it works) I get this:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10


I couldn't find much on the forums so I figured I'd ask.

Many thanks.

Im running 8.10 on a T60 with a Ati x1400

---

### Post by bender1234 on 2009-07-22
What kind of graphics card do you have, and which driver are you using?
What does ***glxinfo | grep OpenGL*** tell you?
(it should say something like:)

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9600M GT/PCI/SSE2
OpenGL version string: 3.0.0 NVIDIA 180.44
OpenGL shading language version string: 1.30 NVIDIA via Cg compiler
...........

Sounds like you have a problem with your driver. Have you had this problem all along, or have it appeared after you updated a driver?

---

