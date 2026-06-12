---
title: "nvidia-legacy blank screen problem"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by ogtifs on 2007-06-21
Hi

I'm trying to set up a lightweight desktop computer. Using Xubuntu and nv driver all is well, but under windows I had OpenGL and I am as yet unable to make it work here. The card is an old NVIDIA RIVA TNT2, so supported under the old legacy 7xxx drivers. Xubuntu correctly detected this as the nvidia-legacy-glx package and installed via restricted-drivers-manager. However on reboot I am presented with a black screen, and neither ctrl+alt+# nor ctrl+alt+backspace do anything. Any ideas?

I've attached xorg.conf and Xorg.0.log
There is only one monitor, plugged into the VGA port so the warning about multiple monitors seems redundant.
Everything works fine simply by replacing nvidia with nv in xorg.conf but then no OpenGL

Thanks in advance

---

