---
title: "OpenGL issue with multi GPU"
date: 2013-02-19
forum: Multimedia Software
---

### Post by dushtbalak on 2013-02-19
My Machine specs

Processor core2duo 1.8 GHz
2 GB RAM
Onboard intel GM945 Graphics
Nvidia 6200 
3 monitors @ 1024x768

So i got the three monitors working ( 2 on nVidia and 1 on Intel) by setting the onboard card as primary and after installing the nvidia drivers by using the ubuntu extreme nvidia installer.

I had to edit the xorg.conf manually to add all the monitors but it worked and after enabling xinerama i was able to get the gnome DE on all three monitors.

[B][Problem] 
[/B]
My program uses openGL to draw and on the test machine with one GPU everything works fine. I tried the same program on the actual machine mentioned above and the openGL drawn widgets are corrupted on all displays but the primary display. Has anyone experienced this before? I absolutely have no idea on how to fix this. Not new to linux but its my first time encountering an issue like this.

---

