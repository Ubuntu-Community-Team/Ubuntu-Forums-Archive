---
title: "How do I enable GL_EXT_framebuffer_object?"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Alaric on 2008-11-23
Hey guys,

I'm running a Dell Inspiron 1525 laptop with a GM965 graphics card.  I'm having some problems with an APP that requires GL_EXT_framebuffer_object, but I have no idea how to install it.  Direct rendering "just worked" with my fresh hardy 8.10 install, but glewinfo appears to confirm that I don't have the extension installed.  

```
alaric@alaric-laptop$ glewinfo | grep framebuffer
GL_EXT_framebuffer_blit:                                       OK [MISSING]
GL_EXT_framebuffer_multisample:                                OK [MISSING]
GL_EXT_framebuffer_object:                                     OK [MISSING]
GL_EXT_framebuffer_sRGB:                                       MISSING 
GL_NV_framebuffer_multisample_coverage:                        OK [MISSING]
GLX_EXT_framebuffer_sRGB:                                      MISSING 

```

Could I recompile GLEW or Mesa from source to enable this extension?

---

