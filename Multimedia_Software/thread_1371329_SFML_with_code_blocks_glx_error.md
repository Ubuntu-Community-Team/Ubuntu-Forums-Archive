---
title: "SFML with code blocks glx error"
date: 2010-01-03
forum: Multimedia Software
---

### Post by techrascal on 2010-01-03
i am trying to use the sfml library with code blocks and i am getting the following error

could not find matching glx visual on screen "0:0"

also when i try to open a game based on opengl i get the following error:
Error : Screen mode creation failed
Reason : Couldn't find matching GLX visual


this seems to be a problem with my graphics driver.

glxinfo output is this

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault


how do i configure my grapics driver for this?

thanks

---

