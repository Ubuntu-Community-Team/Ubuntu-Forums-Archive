---
title: "GLEW Missing GL Version"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by ObeseOgre on 2007-12-15
I'm trying to use glew and i've installed the libglew-dev package but when I call glewInit() I get the "Error: Missing GL version".

I believe I have openGL 2.0 driver support.  

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)
```

glewinfo
```

GL_VERSION_2_0:                                                OK 
---------------
  glAttachShader:                                              OK
  glBindAttribLocation:                                        OK
  glBlendEquationSeparate:                                     OK
  glCompileShader:                                             OK
  glCreateProgram:                                             OK
  glCreateShader:                                              OK
  glDeleteProgram:                                             OK
  glDeleteShader:                                              OK
  glDetachShader:                                              OK
  glDisableVertexAttribArray:                                  OK
  glDrawBuffers:                                               OK
  glEnableVertexAttribArray:                                   OK

```

---

