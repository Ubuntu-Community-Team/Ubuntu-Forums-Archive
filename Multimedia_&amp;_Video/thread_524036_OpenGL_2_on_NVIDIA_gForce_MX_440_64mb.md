---
title: "OpenGL 2 on NVIDIA gForce MX 440 64mb"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by liebertx on 2007-08-12
for the last couple of months, i have unsuccessfully attempted to get my gpu set up with opengl 2* and glsl.  My graphics card is an nvidia mx 440 64mb.  the nvidia-glx package works, i also tried to get the newest 'NVIDIA-Linux-x86-1.0-9639.pkg1.run'(which supports the mx 440, and also *says* it is updated to opengl2.1) and compile an nvidia kernal.  both my custom kernel and the nvidia-glx both work the same, and are hardware accelerated.  unfortunately they both only supply opengl 1.5.  i later noticed that mesa0.7 has opengl2.1 support, but when i compiled it, i was only able to get software rendering.  i need to get opengl 2 working with my graphics card.  is there any way to make this happen? or is there any way i can get mesa to software-emulate features of opengl2/glsl and hardware accelerate as much as it can?  is this even the forum for me to ask in? any ideas?

---

### Post by tseliot on 2007-08-13
post the output of this command:
```
glxinfo
```

---

