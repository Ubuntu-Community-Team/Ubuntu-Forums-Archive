---
title: "ATI OpenGL corrupted video"
date: 2008-05-09
forum: Multimedia Software
---

### Post by iAnorak on 2008-05-09
I'm currently running Ubuntu 8.04 with an ATI Radeon X800 Pro and am encountering a weird (what I'm assuming is related to the framebuffer) issue. I installed the latest ATI driver off of the ATI website, as well as the Catalyst Control Center.

Running glxgears works fine. I can clearly see the gears turning. However, when I try to run a program that I've compiled (which uses gtkmm and gtkglext, along with a few other libraries), the image appears to be corrupted. Sometimes what appears is what used to be on screen (perhaps what used to be stored in the framebuffer). If I try resizing the window, for a split second I see what I'm supposed to see, but it quickly goes away.

Any idea what could be causing this? I'm assuming it's something to do with the graphics driver but I'm not sure. :confused:

---

