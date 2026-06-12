---
title: "OpenGL fails to initialize"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by strattonbrazil on 2006-06-26
I'm having trouble running certain OpenGL games using the DOOM engine in and out of wine.  DOOM 3 gives me an error on this machine saying OpenGL can't be initialized, and so does Prey inside wine.  Other programs like Blender work fine as well as OpenGL code I compile myself.  

Please don't reply if you don't know the answer, cause it will just knock me out of the 'unanswered posts' section.  

This is the error: 

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Open X display
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 1024x768
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 1024x768
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

---

### Post by hanzomon4 on 2006-07-21
Are you using xgl?

---

