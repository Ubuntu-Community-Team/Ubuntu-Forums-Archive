---
title: "glxgears without 3d acceleration"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by Téragone on 2005-10-14
Since I was unable to run the ATI driver. I made a fresh install of Breezy without the xorg-driver-fglrx installed.

I try to run **glxgears -printfps**.

The gears move very slowly but the frame rate tell about 160 FPS. :confused: 

What is strange is that it's not glxgears that eat the CPU but the Xorg process.

Any Idea ?

AMD Athlon 64 3000+
ATI Radeon 9700 Pro 128 MB
Ubuntu Breezy AMD64 K8 kernel.

---

### Post by Téragone on 2005-10-14
Solved:

I compile my own version of glxgears from the source and now the gears move fast..

---

