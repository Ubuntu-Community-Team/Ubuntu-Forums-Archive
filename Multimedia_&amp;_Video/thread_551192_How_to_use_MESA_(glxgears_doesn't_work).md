---
title: "How to use MESA (glxgears doesn't work)"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by Franckovish on 2007-09-14
I have a computer with a good CPU but a crappy old matrox 4mb video card.

Thus, I want to use Mesa's 3d emulation so I can support GLX.

Right now, I can't even run glxgears :
Xlib: extensions "GLX" missing on display "127.0.0.1:1.0"

My xorg.conf's driver is "mga" and the "Load "glx" is not commented in the modules.

Most threads that I read on this forum talk about having to compile mesa ?  I though mesa = Xlib = already part of the X server ... was I wrong ?

Any advices ?  (ps: I'm a noob)

Thanks

---

### Post by peabody on 2007-09-14
It could be mesa didn't even get installed

what does a "dpkg --list | grep mesa" give you in a terminal window?

---

### Post by Franckovish on 2007-09-14
dpkg --list | grep mesa
ii	libgl1-mesa-dri		6.5.2-3ubuntu8
	A free implementation of the OpenGL API -- D
ii	libgl1-mesa-glx		6.5.2-3ubuntu8
	A free implementation of the OpenGL API -- G
ii	libglu1-mesa		6.5.2-3ubuntu8
	The OpenGL utility library (GLU)
ii	mesa-common-dev		6.5.2-3ubuntu8
	Developer documentation for Mesa
ii	mesa-utils		6.5.2-3ubuntu8
	Miscellaneous Mesa GL utilities

---

### Post by peabody on 2007-09-14
next step is to look at /var/log/Xorg.0.log to see why glx is being disabled.

---

### Post by Franckovish on 2007-09-14
Since the log was quite long ... I cut and pasted what I though might be useful.  Let me know if there is something else I should paste ... of if I should paste it all (in multiple submits)

... lots of stuff

(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI

... More stuff 

(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX

... More stuff

(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0

... More stuff ...

---

### Post by peabody on 2007-09-14
Only thing that's shown is you don't have dri but that wouldn't explain why glxgears won't even run...

hmm, keep looking in the log for info related to glx

and for the record, what is your display adapter?

---

### Post by Franckovish on 2007-09-15
The video card is a Matrox Mystic 4mb

Here is a url to my xorg.conf
[http://francoisjanson.no-ip.com:8080/xorg.conf](http://francoisjanson.no-ip.com:8080/xorg.conf)

and to the logs
[http://francoisjanson.no-ip.com:8080/xorg.0.log](http://francoisjanson.no-ip.com:8080/xorg.0.log)

---

