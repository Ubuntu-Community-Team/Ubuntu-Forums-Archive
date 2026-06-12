---
title: "Blender 3D - Jaunty"
date: 2009-05-21
forum: Multimedia Software
---

### Post by rp181 on 2009-05-21
Awhile back, i ws using Blender with no trouble. After jaunty was officially released, i switched from intrepid to jaunty. Now, blender is not working properly. 

This is what it looks like at startup:
[[IMG]http://img507.imageshack.us/img507/219/screenshot1e.th.png[/IMG]](http://img507.imageshack.us/my.php?image=screenshot1e.png)

And after scrolling/zooming in or out:
[[IMG]http://img507.imageshack.us/img507/9987/screenshotoiz.th.png[/IMG]](http://img507.imageshack.us/my.php?image=screenshotoiz.png)

Any help is appreciated.

---

### Post by monraaf on 2009-05-21
What's the vendor and model of your video card? It doesn't happen to be by any chance an ATI card :biggrin:

And what's the output of:

```

$ glxinfo|grep string

```

---

### Post by lukeiamyourfather on 2009-05-21
What graphics card are you using and what drivers? Looks like the video card drivers might not have OpenGL acceleration, or at least it might be broken in the drivers. Cheers!

EDIT: monraaf beat me to it.

---

### Post by rp181 on 2009-05-23
this is the output:

***-Home:~$ glxinfo|grep string
get fences failed: -1
param: 6, val: 0
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915G GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.4
***-Home:~$ 


Why would it work in ibex but not jaunty?

---

### Post by monraaf on 2009-05-23
Can you run blender from a terminal like this:

```

LIBGL_ALWAYS_SOFTWARE=1 blender-bin

```


I don't know much about what's going on with the Intel drivers, but if you don't see any corruption when run as above it's probably an issue with the Intel mesa 3D driver.

---

### Post by rp181 on 2009-05-23
Thanks! It is working better than before, because before, windowed mode was still fullscreen. Any moving progress bar and such would screw it up, but not anymore :).

How can i make a launcher for this? I tried making a launcher, and Alt-F2 with:
LIBGL_ALWAYS_SOFTWARE=1 blender-bin

But i get a error message. I think it is looking for a executable, instead of running it in terminal. Is it possible to make it so i can?

---

### Post by monraaf on 2009-05-23
try this:

```

sh -c "LIBGL_ALWAYS_SOFTWARE=1 blender-bin"

```

---

### Post by rp181 on 2009-05-23
Thanks again :D

---

### Post by NukeouT on 2009-05-29
Code:
 	sh -c "LIBGL_ALWAYS_SOFTWARE=1 blender-bin" 
I managed to open Blender in 9.04 using this code, but it is running slow. What can I do to fix it? Blender has turned itself into molasses.

---

### Post by monraaf on 2009-06-04
Yes, it's expected to be slower since it will be using your CPU to do all the OpenGL stuff. Besides buying a graphics card that does have good OpenGL support in Linux there's not much you can do.

---

### Post by jukzh on 2009-06-05
I'm too getting this messages:
```

get fences failed: -1
param: 6, val: 0

```with not normal window.
When run Blender or OpenGL test [application]("http://www.videotutorialsrock.com/opengl_tutorial/cube/cube.zip")
without that rescue prefix "LIBGL_ALWAYS_SOFTWARE=1", no idea yet what it means :p, actually I exported it as bash variable.
Thanks to Monraaf!!! :D
Regards,
JK

---

### Post by checoimg on 2009-08-11
Thanks!!! Im working all fine.

---

### Post by checoimg on 2009-08-21
> **monraaf said:**
> try this:

```

sh -c "LIBGL_ALWAYS_SOFTWARE=1 blender-bin"

```

what does  [COLOR=Red]sh -c[/COLOR]  do?

---

### Post by checoimg on 2009-08-21
I did this and got the Always Software command to run from the Applicatin/Graphics Main Menu.

Openned Gedit and write the code, stored it with a ".sh" estension.
Rght click on the new object and on permission activated the "allow to run as application"

Stored it on my home folder, right clicked on the Applications main menu and choosed Edit menus

Graphics Section and create new item

Name: Blender (always software)

On the command line wrote:  

gnome-terminal -x /home/[COLOR=Red]home user[/COLOR]/blender_AS.sh

and [COLOR=Lime]OK[/COLOR]

thats it just go to Appplications Graphics and click the new Blender (always software) icon

If someone needs images just post here and I'll get the pgn's.

---

