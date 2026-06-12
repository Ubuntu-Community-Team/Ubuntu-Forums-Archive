---
title: "Wolfenstein ET open gl problem"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Draken2910 on 2008-04-10
okay I am getting this detailed problem after installing then trying to run wolf et

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

I know i have my ati driver installed correctly i figured that out earlier after using ENVY so why is it not hardware accelerated if i plainly have eveything i need????

---

### Post by etlpkby on 2008-04-10
I've got Wolfy running on my Hardy 8.04 x86_64,,, so maybe I can help. :)

Have you recently updated your kernel? (via synaptic, for example)? You may need to re-install your video drivers. I have to do that with my Nvidia 9600 GeForce beta drivers if there's a kernel update...which has happen** a lot **recently with Hardy about to be released and out of beta ;)

Type "glxinfo"

Does it look like the one I've **attached** to this thread?

I had to reinstall my Nvidia video drivers to fix it.

Patrick/

---

