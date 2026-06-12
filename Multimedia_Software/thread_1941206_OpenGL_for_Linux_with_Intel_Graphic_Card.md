---
title: "OpenGL for Linux with Intel Graphic Card?"
date: 2012-03-15
forum: Multimedia Software
---

### Post by WG- on 2012-03-15
Hello,

For a assignment we are gonne use OpenGL. Now I was searching for drivers but I can't find none... I have a Intel GMA 4500M graphic card. 

I searched and found this page: [http://www.opengl.org/wiki/Getting_Started#Linux](http://www.opengl.org/wiki/Getting_Started#Linux) when I then click further for Intel I get end up with this page [http://www.opengl.org/wiki/OpenGL_in_Linux:_Driver_Installation](http://www.opengl.org/wiki/OpenGL_in_Linux:_Driver_Installation)

Also when I search on google I can't find anything for Intel. Do I need to understand that it is not possible to use OpenGL with a Intel card on Linux?

---

### Post by Yellow Pasque on 2012-03-15
> Do I need to understand that it is not possible to use OpenGL with a Intel card on Linux?
No, but you should understand that 3D/OpenGL drivers are installed by default.
```
sudo apt-get install mesa-utils
glxinfo
```

---

