---
title: "OpenGL on Ubuntu Server"
date: 2010-03-03
forum: Multimedia Software
---

### Post by moosehadley on 2010-03-03
Hi, I have a Ubuntu Server set up.
It has no monitor attached, I'm accessing it graphically through vnc4server.

It has no graphics card, and I want to get OpenGL to work on it, using software rendering.

Right now, when I try to run glxgears, I get this.
```
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't get an RGB, Double-buffered visual

```

Could anyone help me?

---

### Post by tgalati4 on 2010-03-03
Post the output of:

glxinfo

---

