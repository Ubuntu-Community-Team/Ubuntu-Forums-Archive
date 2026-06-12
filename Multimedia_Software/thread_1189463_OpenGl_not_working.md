---
title: "OpenGl not working"
date: 2009-06-16
forum: Multimedia Software
---

### Post by Poincare101 on 2009-06-16
All was working fine with opengl until a few days ago. When i tried to run openarena, the screen just flashed and nothing happened. So, i ran it from the command line, and this is what it gave me:
```
dhaivat@penguinToshiba:~/Desktop$ openarena
ioq3+oa 1.35 linux-i386 Sep 10 2008
----- FS_Startup -----
Current search path:
/home/dhaivat/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (12 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (204 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (15 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1720 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (1 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (610 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (234 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (89 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (988 files)
/usr/share/games/openarena/baseoa

----------------------
3873 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL_Init( SDL_INIT_VIDEO )... OK
Initializing OpenGL display
Estimated display aspect: 1.600
...setting mode 3: 640 480
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11

```
So, it seems like openGL (or SDL) may not be working.

---

### Post by Poincare101 on 2009-06-17
can someone tell me what's wrong?

---

### Post by Poincare101 on 2009-07-04
please! someone! I really need help!

---

