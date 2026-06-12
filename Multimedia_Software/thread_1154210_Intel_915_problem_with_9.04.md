---
title: "Intel 915 problem with 9.04"
date: 2009-05-09
forum: Multimedia Software
---

### Post by btermeli on 2009-05-09
Hi all,

I have a fresh installed 9.04 but problem with Intel 915 is appeared.

```
kbt@kbt-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
```

Detects my graphics card but;

```
kbt@kbt-laptop:~$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
kbt@kbt-laptop:~$ 
```
3D is not available.

I use my laptop with external monitor. However I cannot use them like mirror monitors. If I activate the mirror option, only resolution 1024*768 (4:3) is available. It cuts my laptop's output from right and left.
When I was using 8.04, I had a chance to choose different resolutions for laptop and external monitor but now I can't.

I have to use them like DUAL monitor but it reduce the performance. It is unbelievable slow and kills me :)

Do u have any suggestion???

---

