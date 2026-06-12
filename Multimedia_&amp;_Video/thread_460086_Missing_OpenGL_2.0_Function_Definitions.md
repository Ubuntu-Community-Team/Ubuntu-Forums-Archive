---
title: "Missing OpenGL 2.0 Function Definitions"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by xtrawurst on 2007-05-31
Hey,
I'm currently trying to develop an application using OpenGL 2.0 commands but all 2.0-specific function-definitions dont seem to be implemented. In particular I get the following linker errors:

```
libcore.so: undefined reference to `glDeleteProgram'
libcore.so: undefined reference to `glCompileShader'
libcore.so: undefined reference to `glCreateShader'
libcore.so: undefined reference to `glDeleteShader'
libcore.so: undefined reference to `glUseProgram'
libcore.so: undefined reference to `glAttachShader'
libcore.so: undefined reference to `glCreateProgram'
libcore.so: undefined reference to `glLinkProgram'
libcore.so: undefined reference to `glShaderSource'
libcore.so: undefined reference to `glDrawBuffers'

```

This list can easily be extended using more 2.0-specific glXYZ in my code. Since this is a linker error, the problem must be a missing **implementation** of the functions. Nevertheless they are **declared** somewhere in the OpenGL .h files.

The curious thing about this is, that my fglrxinfo tells me:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700
OpenGL version string: 2.0.6334 (8.34.8)
```

So everything seems to be be installed properly. On the other hand, the glew-command ```
glewIsSupported("GL_VERSION_2_0");
```
gives a false on my machine.

Any libXYZ oder libXYZ-dev packages I forgot to install? Any other hints?

Ubuntu: 7.04
Graphics Driver: fglrx 8.34.8 (from the repository)
Grapthics Card: ATI Raedon 9700 Mobile

Thanks!

---

### Post by xtrawurst on 2007-06-01
Can't anyone help? This thing is driving me insane...

---

### Post by koma77 on 2007-06-22
I've got the same problem! Did you manage to solve this?

---

### Post by FunkyRider on 2007-09-11
You need to install libglew-dev package,

#include <GL/glew.h>

compile agains the -lGLEW library

and call glewInit() before calling these functions.

---

