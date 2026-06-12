---
title: "No OpenGL w/ Intel 945GC :("
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by xer0kill on 2007-10-18
This is what I get:
[I]SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
[/I]

When I try to play 3d games like OpenArena and Urban Terror. I recently had to swap out my motherboard/cpu (ASRock Conroe 1333-D667, and Core 2 Duo 1.8Ghz), and I'm stuck with Intel integrated graphics right now.
[B]
What I did:[/B]
1. Deleted my xorg.conf in order to get Gnome to load with the new graphics card
2. Installed the Intel driver with package manager
3. Noticed it never created a new xorg.conf, so I ran the xserver setup again.

I'm not expecting great performance by any means, I just want to get back into my games while I save up money for a decent card. Here's the relevant xorg.conf section:

Section "Device"
	Identifier	"Intel GMA9500 Integrated"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection


If anybody could help, or give me a clue as to the right direction to go in I'd be really appreciative! Thanks in advance!

---

### Post by peabody on 2007-10-18
What does "glxinfo | grep direct" say?

---

### Post by xer0kill on 2007-10-18
**glxinfo | grep direct gives me this:**
[I]Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
[/I]

Apparently you're on to something with that! I'm not sure how to proceed from here, but I'll be searching around and I'll let you know if I get it fixed! (of course I'll be checking back here for more help too..) Thanks!

---

### Post by xer0kill on 2007-10-18
Ok, I got it fixed! I actually found the solution in another thread on here (don't know why I couldn't find it earlier)

```
sudo apt-get remove nvidia-glx
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-dri libgl1-mesa-glx
```

found on [http://ubuntuforums.org/showthread.php?t=526505&page=4](http://ubuntuforums.org/showthread.php?t=526505&page=4)

---

