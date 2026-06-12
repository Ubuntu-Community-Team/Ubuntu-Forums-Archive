---
title: "Conflict between ATI driver and nvidia-glx, no libGLcore.so.1 without it"
date: 2009-10-30
forum: Multimedia Software
---

### Post by zak on 2009-10-30
After upgrading to 9.10, I had no direct rendering and painfully slow video; characters took upwards of five seconds to appear after typing them. I was advised to try running with no xorg.conf, and got much faster video, but still no direct rendering. With fast enough video to comfortably browse the log file, I found this:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
As I have an ATI card and was expecting X to default to the open-source Radeon driver, this seemed like a likely culprit. After removing nvidia-glx-96, I no longer have this problem, and the log indicates that direct rendering is enabled.

The problem now is that any 3D applications I attempt to use complain about a missing libGLcore.so.1, which is contained in the nvidia-glx packages. How can I get OpenGL support back without creating a driver conflict?

If it makes any difference, the card is a mobile FireGL v5200.

---

