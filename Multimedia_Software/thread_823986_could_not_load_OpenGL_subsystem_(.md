---
title: "could not load OpenGL subsystem :("
date: 2008-06-09
forum: Multimedia Software
---

### Post by kikeonline on 2008-06-09
Hi Linux masters!!! I need you help!

I install openarena a while ago and everything worked fine, I played online and everything, but all of a sudden it stoped working, I got this error in the terminal "could not load OpenGL subsystem" .... Later on a wanted to try another but similar game so I install Tremulous but I get the Same Error.

Please Help!! Remember I used to play Openarena perfectly on this machine. I dont know what happened 


**TREMULOUS**

```
tremulous 1.1.0 linux-x86 Jun 16 2007
----- FS_Startup -----
Current search path:
/home/kike/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
QGL_Init: Can't load libGL.so.1 from /etc/ld.so.conf or current dir: No dynamic GL support in video driver
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```


**OPENARENA**

```
ioQ3 1.33+oa linux-i386 Oct 28 2007
----- FS_Startup -----
Current search path:
/home/kike/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (76 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (191 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (11 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1496 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (9 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (620 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (171 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (73 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (926 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
3573 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
QGL_Init: Can't load libGL.so.1 from /etc/ld.so.conf or current dir: No dynamic GL support in video driver
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```

---

### Post by kikeonline on 2008-06-10
please help me :(

---

### Post by kikeonline on 2008-06-10
no body?

---

### Post by lazlo on 2011-06-20
I know, old post .. but found this thread while having the same problem.

Simply run:

```
sudo apt-get install mesa-utils
```

That fixed it for me.

---

