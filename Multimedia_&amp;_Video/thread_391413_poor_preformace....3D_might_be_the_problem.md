---
title: "poor preformace....3D might be the problem?"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by macm10 on 2007-03-23
hello i have a laptop with an ati x1800 i installed the driver like it says to on the wiki guide. my fglrxinfo command gives the following output:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

the ati control center doesnt help. does anyone know how to enable 3D acceleration, or fix this problem?

also where are my AA and AF, ect settings like in cataylst?

---

### Post by swamytk on 2007-03-23
1. Ensure that you have a section shown below in your xorg.conf file.
> Section "dri"
  Mode 0666
EndSection
2. Include the following line under "Section "Module""
>   Load "dri"

---

### Post by macm10 on 2007-03-23
the following was allread entered into xorg.conf....

---

### Post by macm10 on 2007-03-23
i have looked around on google and i still cant seem to find a solution to the problem...i can going to post my Xorg.conf in a few...

---

