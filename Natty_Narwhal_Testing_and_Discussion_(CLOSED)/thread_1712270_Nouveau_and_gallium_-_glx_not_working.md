---
title: "Nouveau and gallium - glx not working"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2011-03-22
I am trying to set up nouveau and gallium to test here with nvidia cards. I can get nouveau to start, but basically I have to delete the xorg.conf file. Then, I get no glx:  

greenman@Wolfenstein:~$ glxinfo
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

Not sure what is wrong. I do have the libgl1-mesa-dri-experimental package installed. Maybe xorg.conf needs something?

---

### Post by doctordruidphd on 2011-03-22
OK, never mind.

What I was trying to do is come up with a way of switching between the nvidia and nouveau drviers, because quite frankly neither one is working very well: nvidia keeps crashing every time I run GIMP (but not other gtk apps), while nouveau is worthless for games. The problem is that installing one of them overwrites a whole bunch of files from the other, so it can't really be done by a script, without removing and installing packages as well.

Was a good idea, though..

---

