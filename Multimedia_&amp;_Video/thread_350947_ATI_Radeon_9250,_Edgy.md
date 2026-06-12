---
title: "ATI Radeon 9250, Edgy"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by EvilMarshmallow on 2007-02-01
I've been trying to get my Radeon 9250 working.  I'm close... I've got regular graphics working fine, but no 3D stuff.  Here's the output of a couple commands:

[INDENT]ben@ubuntu:~$ fglrxinfo
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

ben@ubuntu:~$ glxinfo | grep render
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".[/INDENT]

Of course, 3D apps crash when I try to run them.  Help?

---

### Post by mizar001 on 2007-02-01
no sure, but you must dowload linux drivers from ati. They are in an rpm form or something. You must convert them in deb packages and install. The procedure is shown on this guide :
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by EvilMarshmallow on 2007-02-01
Ok, I followed all the instructions that you linked to but I still have no information when I run

fglrxinfo

ben@ubuntu:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

2D seems ok but still no 3d apps.

---

### Post by EvilMarshmallow on 2007-02-02
Update:

I did a little googling this morning and read where a lot of people said that if you switch from nvidia to ATI you have to uninstall the nvidia driver to get OpenGL working again.

This seems reasonable as I know there are still nvidia files in my system somewhere.

Does anyone know how to uninstall these so they'll release the stranglehold they have on my graphics?

---

