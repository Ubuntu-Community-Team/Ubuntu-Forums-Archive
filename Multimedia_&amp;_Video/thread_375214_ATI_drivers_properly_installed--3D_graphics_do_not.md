---
title: "ATI drivers properly installed--3D graphics do not load though"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by jinx182 on 2007-03-03
I have ATI drivers for my radeon 9800 Pro installed properly to my best knowledge, but when I try to run games like EVE or WoW through wine--or even 3D games designed for Linux I find off the Ubuntu repositories--all I get is a black area where 3D graphics are supposed to be and extremely poor performance with the mouse pointer.

fglrx says:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6286 (8.33.6)
```

glxinfo | grep render says:

```
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9800 Pro Generic
```


Can anyone help please?  If for some reason you can't respond on this thread because I am using ATI's drivers could you possibly email me if you have a solution?

---

### Post by Dekunuts on 2007-03-03
If you run stuff through wine, you have to make sure you add -opengl at the end of the command. So you could make a launcher on your desktop and put -opengl at the end off the command. This only works if your graphics card is installed correctly. check [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) for an ati driver guide.

---

