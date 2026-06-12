---
title: "glxgears with direct rendering: enabled vs disabled"
date: 2009-04-04
forum: Multimedia Software
---

### Post by theresonant on 2009-04-04
Hey all!

I keep trying to somehow improve the performance of my graphics card in Ubuntu, an Intel 945 GM Express which lies inside a HP 530 laptop, but fail every single time, in any way (divers, mesa updates or anything you could expect from an average beginner to try).

With Compiz active:
 - glxinfo says: direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
 - glxgears get: 
      3797 frames in 5.0 seconds = 755.890 FPS
      3680 frames in 5.0 seconds = 734.607 FPS
      3720 frames in 5.0 seconds = 742.423 FPS
 - glxgears window flickers like mad

I know that Compiz enables indirect rendering, and that means trouble for lots of 3D apps, including games. So I kill Compiz and start MetaCity. Results:

With Metacity active:
 - glxinfo says: direct rendering: Yes
 - glxgears get:
      4214 frames in 5.0 seconds = 842.724 FPS
      4381 frames in 5.0 seconds = 876.132 FPS
      4372 frames in 5.0 seconds = 874.230 FPS
 - glxgears window ok

Why is the difference between direct rendering and indirect rendering so small with glxgears? It's just around an extra 100 fps. With Compiz active, those results are normal, but without it I was expecting somewhere around 2000 fps. 

I know this is a driver issue, since in Windows my video card performs quite well, but it's laggy in Ubuntu when it has to do more than just the usual. And Intel has the drivers open-sourced... Now if I was just able to understand how drivers work, I'd have a go at improving it myself, but I know too little about Linux and everything :) It's not really fair to expect everything to be done by the community for free anyway :P

---

### Post by binbash on 2009-04-04
glxgears is not a benchmarking tool.

---

