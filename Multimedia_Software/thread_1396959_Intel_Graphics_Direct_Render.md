---
title: "Intel Graphics Direct Render"
date: 2010-02-02
forum: Multimedia Software
---

### Post by sleepyjon on 2010-02-02
When I try to play a game that uses 3D graphics, I usually just get a blank screen. Running games using wine I get this error:

```

err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1107
  Current serial number in output stream:  1107

```

However:

```

$ glxinfo | grep direct
direct rendering: Yes

```

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

---

### Post by sleepyjon on 2010-02-02
Well, I spent a week thinking this over before I posted only to figure it out 30 seconds after hitting submit. If anyone else is having the same problem on a 64 bit install:

```

export LIBGL_DRIVERS_PATH=/usr/lib32/dri

```

Solved it for me!

---

### Post by quadomatic on 2010-04-02
> **sleepyjon said:**
> Well, I spent a week thinking this over before I posted only to figure it out 30 seconds after hitting submit. If anyone else is having the same problem on a 64 bit install:

```

export LIBGL_DRIVERS_PATH=/usr/lib32/dri

```

Solved it for me!

Oh my god, you have no idea how grateful I am for this. This had been a problem for me even on Arch! I used to get so many errors running 3D programs in WINE...now they actually work.

Half-Life actually even runs in D3D...it runs terribly, but it actually runs! And it's stable! I can play in OpenGL!

---

### Post by sleepyjon on 2010-04-02
> **quadomatic said:**
> Oh my god, you have no idea how grateful I am for this. This had been a problem for me even on Arch! I used to get so many errors running 3D programs in WINE...now they actually work.

Half-Life actually even runs in D3D...it runs terribly, but it actually runs! And it's stable! I can play in OpenGL!

glad it helped you.

---

### Post by andreselsuave on 2011-05-03
I have the same issue, in kubuntu natty 64 bit. Tried that fix, but didn't solve my problem. Do you have any other ideas?
However my video card is a Geforce 210

Thank you!

---

### Post by sleepyjon on 2011-05-04
> **andreselsuave said:**
> I have the same issue, in kubuntu natty 64 bit. Tried that fix, but didn't solve my problem. Do you have any other ideas?
However my video card is a Geforce 210

Thank you!

what does 
```
glxinfo | grep direct
```

 get you?

---

### Post by andreselsuave on 2011-05-05
> what does
Code:
```

glxinfo | grep direct

```
get you? 

```
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 

```

Andrés.

More info:

lshw -c video output:
```

*-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fc000000-fcffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:dc80(size=128) memory:fde00000-fde7ffff

```

I think It might be related to the nvidia drivers I am using. with 10.04 I was using I think 260 drivers for nvidia and with natty now I am using 270. However I didnt test starcraft II in this computer with the other drivers version...

---

### Post by andreselsuave on 2011-05-05
Additional info:

WINEDEBUG=+wgl wine Starcraft\ II.exe &> wine.log

Gives this output:
```

err:menubuilder:init_xdg error looking up the desktop directory
fixme:process:GetLogicalProcessorInformation ((nil),0x32dcc0): stub
trace:wgl:wglGetProcAddress func: 'glAccum'
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 2000
trace:wgl:X11DRV_WineGL_InitOpenglInfo GL version             : 2.1.2 NVIDIA 270.41.06.
trace:wgl:X11DRV_WineGL_InitOpenglInfo GL renderer            : GeForce 210/PCI/SSE2.
trace:wgl:X11DRV_WineGL_InitOpenglInfo GLX version            : 1.4.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Server GLX version     : 1.4.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Server GLX vendor:     : NVIDIA Corporation.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Client GLX version     : 1.4.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Client GLX vendor:     : NVIDIA Corporation.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Direct rendering enabled: **False**
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly

```

and a lot more crap... hehe
```
trace:wgl:has_opengl GLX is up and running error_base = 147
trace:wgl:register_extension_string ''
trace:wgl:register_extension     - 'wglGetIntegerv'
trace:wgl:register_extension     - 'wglFinish'
trace:wgl:register_extension     - 'wglFlush'
trace:wgl:register_extension_string 'WGL_ARB_create_context'
trace:wgl:register_extension     - 'wglCreateContextAttribsARB'
trace:wgl:register_extension_string 'WGL_ARB_create_context_profile'
trace:wgl:register_extension_string 'WGL_ARB_pixel_format_float'
trace:wgl:register_extension_string 'WGL_ATI_pixel_format_float'
trace:wgl:register_extension_string 'WGL_ARB_extensions_string'
trace:wgl:register_extension     - 'wglGetExtensionsStringARB'
trace:wgl:register_extension_string 'WGL_ARB_make_current_read'
trace:wgl:register_extension     - 'wglGetCurrentReadDCARB'
trace:wgl:register_extension     - 'wglMakeContextCurrentARB'
trace:wgl:register_extension_string 'WGL_ARB_multisample'
trace:wgl:register_extension_string 'WGL_ARB_pbuffer'
trace:wgl:register_extension     - 'wglCreatePbufferARB'
trace:wgl:register_extension     - 'wglDestroyPbufferARB'
trace:wgl:register_extension     - 'wglGetPbufferDCARB'
trace:wgl:register_extension     - 'wglQueryPbufferARB'
trace:wgl:register_extension     - 'wglReleasePbufferDCARB'
trace:wgl:register_extension     - 'wglSetPbufferAttribARB'
trace:wgl:register_extension_string 'WGL_ARB_pixel_format'
trace:wgl:register_extension     - 'wglChoosePixelFormatARB'
trace:wgl:register_extension     - 'wglGetPixelFormatAttribfvARB'
trace:wgl:register_extension     - 'wglGetPixelFormatAttribivARB'
trace:wgl:register_extension_string 'WGL_ARB_render_texture'
trace:wgl:register_extension     - 'wglBindTexImageARB'
trace:wgl:register_extension     - 'wglReleaseTexImageARB'
trace:wgl:register_extension_string 'WGL_NV_float_buffer'
trace:wgl:register_extension_string 'WGL_NV_texture_rectangle'
trace:wgl:register_extension_string 'WGL_EXT_extensions_string'
trace:wgl:register_extension     - 'wglGetExtensionsStringEXT'
trace:wgl:register_extension_string 'WGL_EXT_swap_control'
trace:wgl:register_extension     - 'wglSwapIntervalEXT'
trace:wgl:register_extension     - 'wglGetSwapIntervalEXT'
trace:wgl:register_extension_string 'WGL_EXT_framebuffer_sRGB'
trace:wgl:register_extension_string 'WGL_WINE_pixel_format_passthrough'
trace:wgl:register_extension     - 'wglSetPixelFormatWINE'
trace:wgl:wglGetProcAddress func: 'glAlphaFunc'
trace:wgl:wglGetProcAddress func: 'glAreTexturesResident'
trace:wgl:wglGetProcAddress func: 'glArrayElement'
trace:wgl:wglGetProcAddress func: 'glBegin'
trace:wgl:wglGetProcAddress func: 'glBindTexture'
trace:wgl:wglGetProcAddress func: 'glBitmap'
trace:wgl:wglGetProcAddress func: 'glBlendFunc'
trace:wgl:wglGetProcAddress func: 'glCallList'
trace:wgl:wglGetProcAddress func: 'glCallLists'
trace:wgl:wglGetProcAddress func: 'glClear'
trace:wgl:wglGetProcAddress func: 'glClearAccum'
trace:wgl:wglGetProcAddress func: 'glClearColor'
trace:wgl:wglGetProcAddress func: 'glClearDepth'
trace:wgl:wglGetProcAddress func: 'glClearIndex'
trace:wgl:wglGetProcAddress func: 'glClearStencil'
trace:wgl:wglGetProcAddress func: 'glClipPlane'
trace:wgl:wglGetProcAddress func: 'glColor3b'
trace:wgl:wglGetProcAddress func: 'glColor3bv'
trace:wgl:wglGetProcAddress func: 'glColor3d'
trace:wgl:wglGetProcAddress func: 'glColor3dv'
trace:wgl:wglGetProcAddress func: 'glColor3f'
trace:wgl:wglGetProcAddress func: 'glColor3fv'
trace:wgl:wglGetProcAddress func: 'glColor3i'
trace:wgl:wglGetProcAddress func: 'glColor3iv'
trace:wgl:wglGetProcAddress func: 'glColor3s'
trace:wgl:wglGetProcAddress func: 'glColor3sv'
trace:wgl:wglGetProcAddress func: 'glColor3ub'
trace:wgl:wglGetProcAddress func: 'glColor3ubv'
trace:wgl:wglGetProcAddress func: 'glColor3ui'
trace:wgl:wglGetProcAddress func: 'glColor3uiv'
trace:wgl:wglGetProcAddress func: 'glColor3us'
trace:wgl:wglGetProcAddress func: 'glColor3usv'
trace:wgl:wglGetProcAddress func: 'glColor4b'
trace:wgl:wglGetProcAddress func: 'glColor4bv'
trace:wgl:wglGetProcAddress func: 'glColor4d'
trace:wgl:wglGetProcAddress func: 'glColor4dv'
trace:wgl:wglGetProcAddress func: 'glColor4f'
trace:wgl:wglGetProcAddress func: 'glColor4fv'
trace:wgl:wglGetProcAddress func: 'glColor4i'
trace:wgl:wglGetProcAddress func: 'glColor4iv'
trace:wgl:wglGetProcAddress func: 'glColor4s'
trace:wgl:wglGetProcAddress func: 'glColor4sv'
trace:wgl:wglGetProcAddress func: 'glColor4ub'
trace:wgl:wglGetProcAddress func: 'glColor4ubv'
trace:wgl:wglGetProcAddress func: 'glColor4ui'
trace:wgl:wglGetProcAddress func: 'glColor4uiv'
trace:wgl:wglGetProcAddress func: 'glColor4us'
trace:wgl:wglGetProcAddress func: 'glColor4usv'
trace:wgl:wglGetProcAddress func: 'glColorMask'
trace:wgl:wglGetProcAddress func: 'glColorMaterial'
trace:wgl:wglGetProcAddress func: 'glColorPointer'
trace:wgl:wglGetProcAddress func: 'glCopyPixels'
trace:wgl:wglGetProcAddress func: 'glCopyTexImage1D'
trace:wgl:wglGetProcAddress func: 'glCopyTexImage2D'
trace:wgl:wglGetProcAddress func: 'glCopyTexSubImage1D'
trace:wgl:wglGetProcAddress func: 'glCopyTexSubImage2D'
trace:wgl:wglGetProcAddress func: 'glCullFace'
trace:wgl:wglGetProcAddress func: 'glDeleteLists'
trace:wgl:wglGetProcAddress func: 'glDeleteTextures'
trace:wgl:wglGetProcAddress func: 'glDepthFunc'
trace:wgl:wglGetProcAddress func: 'glDepthMask'
trace:wgl:wglGetProcAddress func: 'glDepthRange'
trace:wgl:wglGetProcAddress func: 'glDisable'
trace:wgl:wglGetProcAddress func: 'glDisableClientState'
trace:wgl:wglGetProcAddress func: 'glDrawArrays'
trace:wgl:wglGetProcAddress func: 'glDrawBuffer'
trace:wgl:wglGetProcAddress func: 'glDrawElements'
trace:wgl:wglGetProcAddress func: 'glDrawPixels'
trace:wgl:wglGetProcAddress func: 'glEdgeFlag'
trace:wgl:wglGetProcAddress func: 'glEdgeFlagPointer'
trace:wgl:wglGetProcAddress func: 'glEdgeFlagv'
trace:wgl:wglGetProcAddress func: 'glEnable'
trace:wgl:wglGetProcAddress func: 'glEnableClientState'
trace:wgl:wglGetProcAddress func: 'glEnd'
trace:wgl:wglGetProcAddress func: 'glEndList'
trace:wgl:wglGetProcAddress func: 'glEvalCoord1d'
trace:wgl:wglGetProcAddress func: 'glEvalCoord1dv'
trace:wgl:wglGetProcAddress func: 'glEvalCoord1f'
trace:wgl:wglGetProcAddress func: 'glEvalCoord1fv'
trace:wgl:wglGetProcAddress func: 'glEvalCoord2d'
trace:wgl:wglGetProcAddress func: 'glEvalCoord2dv'
trace:wgl:wglGetProcAddress func: 'glEvalCoord2f'
trace:wgl:wglGetProcAddress func: 'glEvalCoord2fv'
trace:wgl:wglGetProcAddress func: 'glEvalMesh1'
trace:wgl:wglGetProcAddress func: 'glEvalMesh2'
trace:wgl:wglGetProcAddress func: 'glEvalPoint1'
trace:wgl:wglGetProcAddress func: 'glEvalPoint2'
trace:wgl:wglGetProcAddress func: 'glFeedbackBuffer'
trace:wgl:wglGetProcAddress func: 'glFogf'
trace:wgl:wglGetProcAddress func: 'glFogfv'
trace:wgl:wglGetProcAddress func: 'glFogi'
trace:wgl:wglGetProcAddress func: 'glFogiv'
trace:wgl:wglGetProcAddress func: 'glFrontFace'
trace:wgl:wglGetProcAddress func: 'glFrustum'
trace:wgl:wglGetProcAddress func: 'glGenLists'
trace:wgl:wglGetProcAddress func: 'glGenTextures'
trace:wgl:wglGetProcAddress func: 'glGetBooleanv'
trace:wgl:wglGetProcAddress func: 'glGetClipPlane'
trace:wgl:wglGetProcAddress func: 'glGetDoublev'
trace:wgl:wglGetProcAddress func: 'glGetError'
trace:wgl:wglGetProcAddress func: 'glGetFloatv'
trace:wgl:wglGetProcAddress func: 'glGetIntegerv'
trace:wgl:wglGetProcAddress func: 'glGetLightfv'
trace:wgl:wglGetProcAddress func: 'glGetLightiv'
trace:wgl:wglGetProcAddress func: 'glGetMapdv'
trace:wgl:wglGetProcAddress func: 'glGetMapfv'
trace:wgl:wglGetProcAddress func: 'glGetMapiv'
trace:wgl:wglGetProcAddress func: 'glGetMaterialfv'
trace:wgl:wglGetProcAddress func: 'glGetMaterialiv'
trace:wgl:wglGetProcAddress func: 'glGetPixelMapfv'
trace:wgl:wglGetProcAddress func: 'glGetPixelMapuiv'
trace:wgl:wglGetProcAddress func: 'glGetPixelMapusv'
trace:wgl:wglGetProcAddress func: 'glGetPointerv'
trace:wgl:wglGetProcAddress func: 'glGetPolygonStipple'
trace:wgl:wglGetProcAddress func: 'glGetString'
trace:wgl:wglGetProcAddress func: 'glGetTexEnvfv'
trace:wgl:wglGetProcAddress func: 'glGetTexEnviv'
trace:wgl:wglGetProcAddress func: 'glGetTexGendv'
trace:wgl:wglGetProcAddress func: 'glGetTexGenfv'
trace:wgl:wglGetProcAddress func: 'glGetTexGeniv'
trace:wgl:wglGetProcAddress func: 'glGetTexImage'
trace:wgl:wglGetProcAddress func: 'glGetTexLevelParameterfv'
trace:wgl:wglGetProcAddress func: 'glGetTexLevelParameteriv'
trace:wgl:wglGetProcAddress func: 'glGetTexParameterfv'
trace:wgl:wglGetProcAddress func: 'glGetTexParameteriv'
trace:wgl:wglGetProcAddress func: 'glHint'
trace:wgl:wglGetProcAddress func: 'glIndexMask'
trace:wgl:wglGetProcAddress func: 'glIndexPointer'
trace:wgl:wglGetProcAddress func: 'glIndexd'
trace:wgl:wglGetProcAddress func: 'glIndexdv'
trace:wgl:wglGetProcAddress func: 'glIndexf'
trace:wgl:wglGetProcAddress func: 'glIndexfv'
trace:wgl:wglGetProcAddress func: 'glIndexi'
trace:wgl:wglGetProcAddress func: 'glIndexiv'
trace:wgl:wglGetProcAddress func: 'glIndexs'
trace:wgl:wglGetProcAddress func: 'glIndexsv'
trace:wgl:wglGetProcAddress func: 'glIndexub'
trace:wgl:wglGetProcAddress func: 'glIndexubv'
trace:wgl:wglGetProcAddress func: 'glInitNames'
trace:wgl:wglGetProcAddress func: 'glInterleavedArrays'
trace:wgl:wglGetProcAddress func: 'glIsEnabled'
trace:wgl:wglGetProcAddress func: 'glIsList'
trace:wgl:wglGetProcAddress func: 'glIsTexture'
trace:wgl:wglGetProcAddress func: 'glLightModelf'
trace:wgl:wglGetProcAddress func: 'glLightModelfv'
trace:wgl:wglGetProcAddress func: 'glLightModeli'
trace:wgl:wglGetProcAddress func: 'glLightModeliv'
trace:wgl:wglGetProcAddress func: 'glLightf'
trace:wgl:wglGetProcAddress func: 'glLightfv'
trace:wgl:wglGetProcAddress func: 'glLighti'
trace:wgl:wglGetProcAddress func: 'glLightiv'
trace:wgl:wglGetProcAddress func: 'glLineStipple'
trace:wgl:wglGetProcAddress func: 'glLineWidth'
trace:wgl:wglGetProcAddress func: 'glListBase'
trace:wgl:wglGetProcAddress func: 'glLoadIdentity'
trace:wgl:wglGetProcAddress func: 'glLoadMatrixd'
trace:wgl:wglGetProcAddress func: 'glLoadMatrixf'
trace:wgl:wglGetProcAddress func: 'glLoadName'
trace:wgl:wglGetProcAddress func: 'glLogicOp'
trace:wgl:wglGetProcAddress func: 'glMap1d'
trace:wgl:wglGetProcAddress func: 'glMap1f'
trace:wgl:wglGetProcAddress func: 'glMap2d'
trace:wgl:wglGetProcAddress func: 'glMap2f'
trace:wgl:wglGetProcAddress func: 'glMapGrid1d'
trace:wgl:wglGetProcAddress func: 'glMapGrid1f'
trace:wgl:wglGetProcAddress func: 'glMapGrid2d'
trace:wgl:wglGetProcAddress func: 'glMapGrid2f'
trace:wgl:wglGetProcAddress func: 'glMaterialf'
trace:wgl:wglGetProcAddress func: 'glMaterialfv'
trace:wgl:wglGetProcAddress func: 'glMateriali'
trace:wgl:wglGetProcAddress func: 'glMaterialiv'
trace:wgl:wglGetProcAddress func: 'glMatrixMode'
trace:wgl:wglGetProcAddress func: 'glMultMatrixd'
trace:wgl:wglGetProcAddress func: 'glMultMatrixf'
trace:wgl:wglGetProcAddress func: 'glNewList'
trace:wgl:wglGetProcAddress func: 'glNormal3b'
trace:wgl:wglGetProcAddress func: 'glNormal3bv'
trace:wgl:wglGetProcAddress func: 'glNormal3d'
trace:wgl:wglGetProcAddress func: 'glNormal3dv'
trace:wgl:wglGetProcAddress func: 'glNormal3f'
trace:wgl:wglGetProcAddress func: 'glNormal3fv'
trace:wgl:wglGetProcAddress func: 'glNormal3i'
trace:wgl:wglGetProcAddress func: 'glNormal3iv'
trace:wgl:wglGetProcAddress func: 'glNormal3s'
trace:wgl:wglGetProcAddress func: 'glNormal3sv'
trace:wgl:wglGetProcAddress func: 'glNormalPointer'
trace:wgl:wglGetProcAddress func: 'glOrtho'
trace:wgl:wglGetProcAddress func: 'glPassThrough'
trace:wgl:wglGetProcAddress func: 'glPixelMapfv'
trace:wgl:wglGetProcAddress func: 'glPixelMapuiv'
trace:wgl:wglGetProcAddress func: 'glPixelMapusv'
trace:wgl:wglGetProcAddress func: 'glPixelStoref'
trace:wgl:wglGetProcAddress func: 'glPixelStorei'
trace:wgl:wglGetProcAddress func: 'glPixelTransferf'
trace:wgl:wglGetProcAddress func: 'glPixelTransferi'
trace:wgl:wglGetProcAddress func: 'glPixelZoom'
trace:wgl:wglGetProcAddress func: 'glPointSize'
trace:wgl:wglGetProcAddress func: 'glPolygonMode'
trace:wgl:wglGetProcAddress func: 'glPolygonOffset'
trace:wgl:wglGetProcAddress func: 'glPolygonStipple'
trace:wgl:wglGetProcAddress func: 'glPopAttrib'
trace:wgl:wglGetProcAddress func: 'glPopClientAttrib'
trace:wgl:wglGetProcAddress func: 'glPopMatrix'
trace:wgl:wglGetProcAddress func: 'glPopName'
trace:wgl:wglGetProcAddress func: 'glPrioritizeTextures'
trace:wgl:wglGetProcAddress func: 'glPushAttrib'
trace:wgl:wglGetProcAddress func: 'glPushClientAttrib'
trace:wgl:wglGetProcAddress func: 'glPushMatrix'
trace:wgl:wglGetProcAddress func: 'glPushName'
trace:wgl:wglGetProcAddress func: 'glRasterPos2d'
trace:wgl:wglGetProcAddress func: 'glRasterPos2dv'
trace:wgl:wglGetProcAddress func: 'glRasterPos2f'
trace:wgl:wglGetProcAddress func: 'glRasterPos2fv'
trace:wgl:wglGetProcAddress func: 'glRasterPos2i'
trace:wgl:wglGetProcAddress func: 'glRasterPos2iv'
trace:wgl:wglGetProcAddress func: 'glRasterPos2s'
trace:wgl:wglGetProcAddress func: 'glRasterPos2sv'
trace:wgl:wglGetProcAddress func: 'glRasterPos3d'
trace:wgl:wglGetProcAddress func: 'glRasterPos3dv'
trace:wgl:wglGetProcAddress func: 'glRasterPos3f'
trace:wgl:wglGetProcAddress func: 'glRasterPos3fv'
trace:wgl:wglGetProcAddress func: 'glRasterPos3i'
trace:wgl:wglGetProcAddress func: 'glRasterPos3iv'
trace:wgl:wglGetProcAddress func: 'glRasterPos3s'
trace:wgl:wglGetProcAddress func: 'glRasterPos3sv'
trace:wgl:wglGetProcAddress func: 'glRasterPos4d'
trace:wgl:wglGetProcAddress func: 'glRasterPos4dv'
trace:wgl:wglGetProcAddress func: 'glRasterPos4f'
trace:wgl:wglGetProcAddress func: 'glRasterPos4fv'
trace:wgl:wglGetProcAddress func: 'glRasterPos4i'
trace:wgl:wglGetProcAddress func: 'glRasterPos4iv'
trace:wgl:wglGetProcAddress func: 'glRasterPos4s'
trace:wgl:wglGetProcAddress func: 'glRasterPos4sv'
trace:wgl:wglGetProcAddress func: 'glReadBuffer'
trace:wgl:wglGetProcAddress func: 'glReadPixels'
trace:wgl:wglGetProcAddress func: 'glRectd'
trace:wgl:wglGetProcAddress func: 'glRectdv'
trace:wgl:wglGetProcAddress func: 'glRectf'
trace:wgl:wglGetProcAddress func: 'glRectfv'
trace:wgl:wglGetProcAddress func: 'glRecti'
trace:wgl:wglGetProcAddress func: 'glRectiv'
trace:wgl:wglGetProcAddress func: 'glRects'
trace:wgl:wglGetProcAddress func: 'glRectsv'
trace:wgl:wglGetProcAddress func: 'glRenderMode'
trace:wgl:wglGetProcAddress func: 'glRotated'
trace:wgl:wglGetProcAddress func: 'glRotatef'
trace:wgl:wglGetProcAddress func: 'glScaled'
trace:wgl:wglGetProcAddress func: 'glScalef'
trace:wgl:wglGetProcAddress func: 'glScissor'
trace:wgl:wglGetProcAddress func: 'glSelectBuffer'
trace:wgl:wglGetProcAddress func: 'glShadeModel'
trace:wgl:wglGetProcAddress func: 'glStencilFunc'
trace:wgl:wglGetProcAddress func: 'glStencilMask'
trace:wgl:wglGetProcAddress func: 'glStencilOp'
trace:wgl:wglGetProcAddress func: 'glTexCoord1d'
trace:wgl:wglGetProcAddress func: 'glTexCoord1dv'
trace:wgl:wglGetProcAddress func: 'glTexCoord1f'
trace:wgl:wglGetProcAddress func: 'glTexCoord1fv'
trace:wgl:wglGetProcAddress func: 'glTexCoord1i'
trace:wgl:wglGetProcAddress func: 'glTexCoord1iv'
trace:wgl:wglGetProcAddress func: 'glTexCoord1s'
trace:wgl:wglGetProcAddress func: 'glTexCoord1sv'
trace:wgl:wglGetProcAddress func: 'glTexCoord2d'
trace:wgl:wglGetProcAddress func: 'glTexCoord2dv'
trace:wgl:wglGetProcAddress func: 'glTexCoord2f'
trace:wgl:wglGetProcAddress func: 'glTexCoord2fv'
trace:wgl:wglGetProcAddress func: 'glTexCoord2i'
trace:wgl:wglGetProcAddress func: 'glTexCoord2iv'
trace:wgl:wglGetProcAddress func: 'glTexCoord2s'
trace:wgl:wglGetProcAddress func: 'glTexCoord2sv'
trace:wgl:wglGetProcAddress func: 'glTexCoord3d'
trace:wgl:wglGetProcAddress func: 'glTexCoord3dv'
trace:wgl:wglGetProcAddress func: 'glTexCoord3f'
trace:wgl:wglGetProcAddress func: 'glTexCoord3fv'
trace:wgl:wglGetProcAddress func: 'glTexCoord3i'
trace:wgl:wglGetProcAddress func: 'glTexCoord3iv'
trace:wgl:wglGetProcAddress func: 'glTexCoord3s'
trace:wgl:wglGetProcAddress func: 'glTexCoord3sv'
trace:wgl:wglGetProcAddress func: 'glTexCoord4d'
trace:wgl:wglGetProcAddress func: 'glTexCoord4dv'
trace:wgl:wglGetProcAddress func: 'glTexCoord4f'
trace:wgl:wglGetProcAddress func: 'glTexCoord4fv'
trace:wgl:wglGetProcAddress func: 'glTexCoord4i'
trace:wgl:wglGetProcAddress func: 'glTexCoord4iv'
trace:wgl:wglGetProcAddress func: 'glTexCoord4s'
trace:wgl:wglGetProcAddress func: 'glTexCoord4sv'
trace:wgl:wglGetProcAddress func: 'glTexCoordPointer'
trace:wgl:wglGetProcAddress func: 'glTexEnvf'
trace:wgl:wglGetProcAddress func: 'glTexEnvfv'
trace:wgl:wglGetProcAddress func: 'glTexEnvi'
trace:wgl:wglGetProcAddress func: 'glTexEnviv'
trace:wgl:wglGetProcAddress func: 'glTexGend'
trace:wgl:wglGetProcAddress func: 'glTexGendv'
trace:wgl:wglGetProcAddress func: 'glTexGenf'
trace:wgl:wglGetProcAddress func: 'glTexGenfv'
trace:wgl:wglGetProcAddress func: 'glTexGeni'
trace:wgl:wglGetProcAddress func: 'glTexGeniv'
trace:wgl:wglGetProcAddress func: 'glTexImage1D'
trace:wgl:wglGetProcAddress func: 'glTexImage2D'
trace:wgl:wglGetProcAddress func: 'glTexParameterf'
trace:wgl:wglGetProcAddress func: 'glTexParameterfv'
trace:wgl:wglGetProcAddress func: 'glTexParameteri'
trace:wgl:wglGetProcAddress func: 'glTexParameteriv'
trace:wgl:wglGetProcAddress func: 'glTexSubImage1D'
trace:wgl:wglGetProcAddress func: 'glTexSubImage2D'
trace:wgl:wglGetProcAddress func: 'glTranslated'
trace:wgl:wglGetProcAddress func: 'glTranslatef'
trace:wgl:wglGetProcAddress func: 'glVertex2d'
trace:wgl:wglGetProcAddress func: 'glVertex2dv'
trace:wgl:wglGetProcAddress func: 'glVertex2f'
trace:wgl:wglGetProcAddress func: 'glVertex2fv'
trace:wgl:wglGetProcAddress func: 'glVertex2i'
trace:wgl:wglGetProcAddress func: 'glVertex2iv'
trace:wgl:wglGetProcAddress func: 'glVertex2s'
trace:wgl:wglGetProcAddress func: 'glVertex2sv'
trace:wgl:wglGetProcAddress func: 'glVertex3d'
trace:wgl:wglGetProcAddress func: 'glVertex3dv'
trace:wgl:wglGetProcAddress func: 'glVertex3f'
trace:wgl:wglGetProcAddress func: 'glVertex3fv'
trace:wgl:wglGetProcAddress func: 'glVertex3i'
trace:wgl:wglGetProcAddress func: 'glVertex3iv'
trace:wgl:wglGetProcAddress func: 'glVertex3s'
trace:wgl:wglGetProcAddress func: 'glVertex3sv'
trace:wgl:wglGetProcAddress func: 'glVertex4d'
trace:wgl:wglGetProcAddress func: 'glVertex4dv'
trace:wgl:wglGetProcAddress func: 'glVertex4f'
trace:wgl:wglGetProcAddress func: 'glVertex4fv'
trace:wgl:wglGetProcAddress func: 'glVertex4i'
trace:wgl:wglGetProcAddress func: 'glVertex4iv'
trace:wgl:wglGetProcAddress func: 'glVertex4s'
trace:wgl:wglGetProcAddress func: 'glVertex4sv'
trace:wgl:wglGetProcAddress func: 'glVertexPointer'
trace:wgl:wglGetProcAddress func: 'glViewport'
trace:wgl:wglGetProcAddress func: 'glPointParameterfv'
trace:wgl:wglGetProcAddress func: 'glPointParameteri'
trace:wgl:wglGetProcAddress func: 'wglFinish'
trace:wgl:X11DRV_wglGetProcAddress ('wglFinish'):                       (0x7dfc9900) - WineGL
trace:wgl:wglGetProcAddress func: 'wglFlush'
trace:wgl:X11DRV_wglGetProcAddress ('wglFlush'):                        (0x7dfc9800) - WineGL
trace:wgl:wglGetCurrentContext  returning (nil)
trace:wgl:wglGetCurrentDC  found context: (nil)
trace:wgl:wglGetCurrentContext  returning (nil)
trace:wgl:X11DRV_ChoosePixelFormat (0x1351f8,0xe3c6a4)
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - size / version : 40 / 1
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - dwFlags : PFD_DOUBLEBUFFER PFD_DRAW_TO_WINDOW PFD_SUPPORT_OPENGL 
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - iPixelType : PFD_TYPE_RGBA
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Color   : 32
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Red     : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Green   : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Blue    : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Alpha   : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Accum   : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Depth   : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Stencil : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Aux     : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - iLayerType : PFD_MAIN_PLANE
trace:wgl:get_formats Found 18 bitmap capable fbconfigs
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x75 corresponding to iPixelFormat 1 at GLX index 0
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x76 corresponding to iPixelFormat 2 at GLX index 1
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x77 corresponding to iPixelFormat 3 at GLX index 2
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x78 corresponding to iPixelFormat 4 at GLX index 3
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x79 corresponding to iPixelFormat 5 at GLX index 4
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x79 corresponding to iPixelFormat 6 at GLX index 4
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x7a corresponding to iPixelFormat 7 at GLX index 5
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x7a corresponding to iPixelFormat 8 at GLX index 5
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x7b corresponding to iPixelFormat 9 at GLX index 6
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x7b corresponding to iPixelFormat 10 at GLX index 6
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x7c corresponding to iPixelFormat 11 at GLX index 7
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x7c corresponding to iPixelFormat 12 at GLX index 7
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x7d corresponding to iPixelFormat 13 at GLX index 8
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x7e corresponding to iPixelFormat 14 at GLX index 9
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x7f corresponding to iPixelFormat 15 at GLX index 10
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x80 corresponding to iPixelFormat 16 at GLX index 11
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x81 corresponding to iPixelFormat 17 at GLX index 12
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x81 corresponding to iPixelFormat 18 at GLX index 12
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x82 corresponding to iPixelFormat 19 at GLX index 13
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x82 corresponding to iPixelFormat 20 at GLX index 13
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x83 corresponding to iPixelFormat 21 at GLX index 14
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x83 corresponding to iPixelFormat 22 at GLX index 14
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x84 corresponding to iPixelFormat 23 at GLX index 15
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x84 corresponding to iPixelFormat 24 at GLX index 15
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x85 corresponding to iPixelFormat 25 at GLX index 16
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x86 corresponding to iPixelFormat 26 at GLX index 17
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x87 corresponding to iPixelFormat 27 at GLX index 18
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x88 corresponding to iPixelFormat 28 at GLX index 19
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x89 corresponding to iPixelFormat 29 at GLX index 20
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x89 corresponding to iPixelFormat 30 at GLX index 20
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x8a corresponding to iPixelFormat 31 at GLX index 21
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x8a corresponding to iPixelFormat 32 at GLX index 21
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x8b corresponding to iPixelFormat 33 at GLX index 22
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x8b corresponding to iPixelFormat 34 at GLX index 22
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x8c corresponding to iPixelFormat 35 at GLX index 23
trace:wgl:get_formats Found bitmap capable format FBCONFIG_ID 0x8c corresponding to iPixelFormat 36 at GLX index 23
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x8d corresponding to iPixelFormat 37 at GLX index 24
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x8e corresponding to iPixelFormat 38 at GLX index 25
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x8f corresponding to iPixelFormat 39 at GLX index 26
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x90 corresponding to iPixelFormat 40 at GLX index 27
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x91 corresponding to iPixelFormat 41 at GLX index 28
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x92 corresponding to iPixelFormat 42 at GLX index 29
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x93 corresponding to iPixelFormat 43 at GLX index 30
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x94 corresponding to iPixelFormat 44 at GLX index 31
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x95 corresponding to iPixelFormat 45 at GLX index 32
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x96 corresponding to iPixelFormat 46 at GLX index 33
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x97 corresponding to iPixelFormat 47 at GLX index 34
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x98 corresponding to iPixelFormat 48 at GLX index 35
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x99 corresponding to iPixelFormat 49 at GLX index 36
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x9a corresponding to iPixelFormat 50 at GLX index 37
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x9b corresponding to iPixelFormat 51 at GLX index 38
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x9c corresponding to iPixelFormat 52 at GLX index 39
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x9d corresponding to iPixelFormat 53 at GLX index 40
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x9e corresponding to iPixelFormat 54 at GLX index 41
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0x9f corresponding to iPixelFormat 55 at GLX index 42
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa0 corresponding to iPixelFormat 56 at GLX index 43
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa1 corresponding to iPixelFormat 57 at GLX index 44
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa2 corresponding to iPixelFormat 58 at GLX index 45
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa3 corresponding to iPixelFormat 59 at GLX index 46
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa4 corresponding to iPixelFormat 60 at GLX index 47
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa5 corresponding to iPixelFormat 61 at GLX index 48
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa6 corresponding to iPixelFormat 62 at GLX index 49
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa7 corresponding to iPixelFormat 63 at GLX index 50
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa8 corresponding to iPixelFormat 64 at GLX index 51
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xa9 corresponding to iPixelFormat 65 at GLX index 52
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xaa corresponding to iPixelFormat 66 at GLX index 53
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xab corresponding to iPixelFormat 67 at GLX index 54
trace:wgl:get_formats Found onscreen format FBCONFIG_ID 0xac corresponding to iPixelFormat 68 at GLX index 55
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xc9 corresponding to iPixelFormat 69 at GLX index 84
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xca corresponding to iPixelFormat 70 at GLX index 85
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xcb corresponding to iPixelFormat 71 at GLX index 86
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xcc corresponding to iPixelFormat 72 at GLX index 87
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xcd corresponding to iPixelFormat 73 at GLX index 88
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xce corresponding to iPixelFormat 74 at GLX index 89
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xcf corresponding to iPixelFormat 75 at GLX index 90
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd0 corresponding to iPixelFormat 76 at GLX index 91
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd1 corresponding to iPixelFormat 77 at GLX index 92
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd2 corresponding to iPixelFormat 78 at GLX index 93
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd3 corresponding to iPixelFormat 79 at GLX index 94
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd4 corresponding to iPixelFormat 80 at GLX index 95
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd5 corresponding to iPixelFormat 81 at GLX index 96
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd6 corresponding to iPixelFormat 82 at GLX index 97
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd7 corresponding to iPixelFormat 83 at GLX index 98
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd8 corresponding to iPixelFormat 84 at GLX index 99
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xd9 corresponding to iPixelFormat 85 at GLX index 100
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xda corresponding to iPixelFormat 86 at GLX index 101
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xdb corresponding to iPixelFormat 87 at GLX index 102
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xdc corresponding to iPixelFormat 88 at GLX index 103
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xdd corresponding to iPixelFormat 89 at GLX index 104
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xde corresponding to iPixelFormat 90 at GLX index 105
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xdf corresponding to iPixelFormat 91 at GLX index 106
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe0 corresponding to iPixelFormat 92 at GLX index 107
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe1 corresponding to iPixelFormat 93 at GLX index 108
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe2 corresponding to iPixelFormat 94 at GLX index 109
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe3 corresponding to iPixelFormat 95 at GLX index 110
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe4 corresponding to iPixelFormat 96 at GLX index 111
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe5 corresponding to iPixelFormat 97 at GLX index 112
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe6 corresponding to iPixelFormat 98 at GLX index 113
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe7 corresponding to iPixelFormat 99 at GLX index 114
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe8 corresponding to iPixelFormat 100 at GLX index 115
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xe9 corresponding to iPixelFormat 101 at GLX index 116
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xea corresponding to iPixelFormat 102 at GLX index 117
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xeb corresponding to iPixelFormat 103 at GLX index 118
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xec corresponding to iPixelFormat 104 at GLX index 119
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xed corresponding to iPixelFormat 105 at GLX index 120
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xee corresponding to iPixelFormat 106 at GLX index 121
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xef corresponding to iPixelFormat 107 at GLX index 122
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf0 corresponding to iPixelFormat 108 at GLX index 123
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf1 corresponding to iPixelFormat 109 at GLX index 124
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf2 corresponding to iPixelFormat 110 at GLX index 125
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf3 corresponding to iPixelFormat 111 at GLX index 126
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf4 corresponding to iPixelFormat 112 at GLX index 127
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf5 corresponding to iPixelFormat 113 at GLX index 128
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf6 corresponding to iPixelFormat 114 at GLX index 129
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf7 corresponding to iPixelFormat 115 at GLX index 130
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf8 corresponding to iPixelFormat 116 at GLX index 131
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xf9 corresponding to iPixelFormat 117 at GLX index 132
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xfa corresponding to iPixelFormat 118 at GLX index 133
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xfb corresponding to iPixelFormat 119 at GLX index 134
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xfc corresponding to iPixelFormat 120 at GLX index 135
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xfd corresponding to iPixelFormat 121 at GLX index 136
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xfe corresponding to iPixelFormat 122 at GLX index 137
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0xff corresponding to iPixelFormat 123 at GLX index 138
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x100 corresponding to iPixelFormat 124 at GLX index 139
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x101 corresponding to iPixelFormat 125 at GLX index 140
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x102 corresponding to iPixelFormat 126 at GLX index 141
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x103 corresponding to iPixelFormat 127 at GLX index 142
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x104 corresponding to iPixelFormat 128 at GLX index 143
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x105 corresponding to iPixelFormat 129 at GLX index 144
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x106 corresponding to iPixelFormat 130 at GLX index 145
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x107 corresponding to iPixelFormat 131 at GLX index 146
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x108 corresponding to iPixelFormat 132 at GLX index 147
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x109 corresponding to iPixelFormat 133 at GLX index 148
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x10a corresponding to iPixelFormat 134 at GLX index 149
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x10b corresponding to iPixelFormat 135 at GLX index 150
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x10c corresponding to iPixelFormat 136 at GLX index 151
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x10d corresponding to iPixelFormat 137 at GLX index 152
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x10e corresponding to iPixelFormat 138 at GLX index 153
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x10f corresponding to iPixelFormat 139 at GLX index 154
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x110 corresponding to iPixelFormat 140 at GLX index 155
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x111 corresponding to iPixelFormat 141 at GLX index 156
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x112 corresponding to iPixelFormat 142 at GLX index 157
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x113 corresponding to iPixelFormat 143 at GLX index 158
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x114 corresponding to iPixelFormat 144 at GLX index 159
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x115 corresponding to iPixelFormat 145 at GLX index 160
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x116 corresponding to iPixelFormat 146 at GLX index 161
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x117 corresponding to iPixelFormat 147 at GLX index 162
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x118 corresponding to iPixelFormat 148 at GLX index 163
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x119 corresponding to iPixelFormat 149 at GLX index 164
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x11a corresponding to iPixelFormat 150 at GLX index 165
trace:wgl:get_formats Found offscreen format FBCONFIG_ID 0x11b corresponding to iPixelFormat 151 at GLX index 166
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=6
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=8
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=10
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=12
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=18
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=20
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=22
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=24
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=30
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=32
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=34
trace:wgl:X11DRV_ChoosePixelFormat PFD_DRAW_TO_BITMAP mismatch for iPixelFormat=36
trace:wgl:X11DRV_ChoosePixelFormat Successfully found a matching mode, returning index: 1 75
trace:wgl:X11DRV_DescribePixelFormat (0x1351f8,1,40,0xe3c6a4)
trace:wgl:ConvertPixelFormatWGLtoGLX Returning fmt_id=0x75 for iPixelFormat=1
trace:wgl:ConvertPixelFormatWGLtoGLX Number of returned pixelformats=68
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - size / version : 40 / 1
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - dwFlags : PFD_DOUBLEBUFFER PFD_DRAW_TO_WINDOW PFD_SUPPORT_OPENGL 
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - iPixelType : PFD_TYPE_RGBA
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Color   : 32
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Red     : 8
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Green   : 8
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Blue    : 8
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Alpha   : 0
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Accum   : 64
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Depth   : 24
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Stencil : 8
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - Aux     : 4
trace:wgl:dump_PIXELFORMATDESCRIPTOR   - iLayerType : PFD_MAIN_PLANE
trace:wgl:X11DRV_SetPixelFormat (0x1351f8,1,0xe3c6a4)
trace:wgl:ConvertPixelFormatWGLtoGLX Returning fmt_id=0x75 for iPixelFormat=1
trace:wgl:ConvertPixelFormatWGLtoGLX Number of returned pixelformats=68
fixme:process:GetLogicalProcessorInformation ((nil),0x103c5c0): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x103c5ac): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation ((nil),0x113e9b8): stub
trace:wgl:ConvertPixelFormatGLXtoWGL Returning iPixelFormat 1 for fmt_id 0x75
trace:wgl:internal_SetPixelFormat  FBConfig have :
trace:wgl:internal_SetPixelFormat  - FBCONFIG_ID   0x75
trace:wgl:internal_SetPixelFormat  - VISUAL_ID     0x21
trace:wgl:internal_SetPixelFormat  - DRAWABLE_TYPE 0x7
trace:wgl:wglCreateContext (0x628)
trace:wgl:ConvertPixelFormatGLXtoWGL Returning iPixelFormat 1 for fmt_id 0x75
trace:wgl:X11DRV_wglCreateContext (0x628)->(PF:1)
trace:wgl:ConvertPixelFormatWGLtoGLX Returning fmt_id=0x75 for iPixelFormat=1
trace:wgl:ConvertPixelFormatWGLtoGLX Number of returned pixelformats=151
trace:wgl:X11DRV_wglCreateContext  creating context 0x13b318 (GL context creation delayed)
trace:wgl:wglMakeCurrent hdc: (0x628), hglrc: (0x13b318)
trace:wgl:X11DRV_wglMakeCurrent (0x628,0x13b318)
trace:wgl:ConvertPixelFormatWGLtoGLX Returning fmt_id=0x75 for iPixelFormat=1
trace:wgl:ConvertPixelFormatWGLtoGLX Number of returned pixelformats=151
trace:wgl:describeDrawable  HDC 0x628 has:
trace:wgl:describeDrawable  - iPixelFormat 1
trace:wgl:describeDrawable  - Drawable 0x6600002
trace:wgl:describeDrawable  - FBCONFIG_ID 0x75
trace:wgl:describeDrawable  - VISUAL_ID 0x21
trace:wgl:describeContext  Context 0x13b318 have (vis:0x7c913e48):
trace:wgl:describeContext  - FBCONFIG_ID 0x75
trace:wgl:describeContext  - VISUAL_ID 0x21
trace:wgl:X11DRV_wglMakeCurrent  make current for dis 0x7c8c3170, drawable 0x6600002, ctx 0x7c924c70
trace:wgl:X11DRV_wglMakeCurrent  returning True
trace:wgl:wglGetProcAddress func: 'glClampColorARB'
trace:wgl:wglGetProcAddress func: 'glDrawBuffersARB'
trace:wgl:wglGetProcAddress func: 'glIsRenderbuffer'
trace:wgl:wglGetProcAddress func: 'glBindRenderbuffer'
trace:wgl:wglGetProcAddress func: 'glDeleteRenderbuffers'
trace:wgl:wglGetProcAddress func: 'glGenRenderbuffers'
trace:wgl:wglGetProcAddress func: 'glRenderbufferStorage'
trace:wgl:wglGetProcAddress func: 'glRenderbufferStorageMultisample'
trace:wgl:wglGetProcAddress func: 'glGetRenderbufferParameteriv'
trace:wgl:wglGetProcAddress func: 'glIsFramebuffer'
trace:wgl:wglGetProcAddress func: 'glBindFramebuffer'
trace:wgl:wglGetProcAddress func: 'glDeleteFramebuffers'
trace:wgl:wglGetProcAddress func: 'glGenFramebuffers'
trace:wgl:wglGetProcAddress func: 'glCheckFramebufferStatus'
trace:wgl:wglGetProcAddress func: 'glFramebufferTexture1D'
trace:wgl:wglGetProcAddress func: 'glFramebufferTexture2D'
trace:wgl:wglGetProcAddress func: 'glFramebufferTexture3D'
trace:wgl:wglGetProcAddress func: 'glFramebufferTextureLayer'
trace:wgl:wglGetProcAddress func: 'glFramebufferRenderbuffer'
trace:wgl:wglGetProcAddress func: 'glGetFramebufferAttachmentParameteriv'
trace:wgl:wglGetProcAddress func: 'glBlitFramebuffer'
trace:wgl:wglGetProcAddress func: 'glGenerateMipmap'
trace:wgl:wglGetProcAddress func: 'glProgramParameteriARB'
trace:wgl:wglGetProcAddress func: 'glFramebufferTextureARB'
trace:wgl:wglGetProcAddress func: 'glFramebufferTextureLayerARB'
trace:wgl:wglGetProcAddress func: 'glFramebufferTextureFaceARB'
trace:wgl:wglGetProcAddress func: 'glSampleCoverageARB'
trace:wgl:wglGetProcAddress func: 'glActiveTextureARB'
trace:wgl:wglGetProcAddress func: 'glClientActiveTextureARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord1fARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord1fvARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord2fARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord2fvARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord3fARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord3fvARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord4fARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord4fvARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord2svARB'
trace:wgl:wglGetProcAddress func: 'glMultiTexCoord4svARB'
trace:wgl:wglGetProcAddress func: 'glGenQueriesARB'
trace:wgl:wglGetProcAddress func: 'glDeleteQueriesARB'
trace:wgl:wglGetProcAddress func: 'glBeginQueryARB'
trace:wgl:wglGetProcAddress func: 'glEndQueryARB'
trace:wgl:wglGetProcAddress func: 'glGetQueryObjectivARB'
trace:wgl:wglGetProcAddress func: 'glGetQueryObjectuivARB'
trace:wgl:wglGetProcAddress func: 'glPointParameterfARB'
trace:wgl:wglGetProcAddress func: 'glPointParameterfvARB'
trace:wgl:wglGetProcAddress func: 'glProvokingVertex'
trace:wgl:wglGetProcAddress func: 'glGetObjectParameterivARB'
trace:wgl:wglGetProcAddress func: 'glGetObjectParameterfvARB'
trace:wgl:wglGetProcAddress func: 'glGetUniformLocationARB'
trace:wgl:wglGetProcAddress func: 'glGetActiveUniformARB'
trace:wgl:wglGetProcAddress func: 'glUniform1iARB'
trace:wgl:wglGetProcAddress func: 'glUniform2iARB'
trace:wgl:wglGetProcAddress func: 'glUniform3iARB'
trace:wgl:wglGetProcAddress func: 'glUniform4iARB'
trace:wgl:wglGetProcAddress func: 'glUniform1fARB'
trace:wgl:wglGetProcAddress func: 'glUniform2fARB'
trace:wgl:wglGetProcAddress func: 'glUniform3fARB'
trace:wgl:wglGetProcAddress func: 'glUniform4fARB'
trace:wgl:wglGetProcAddress func: 'glUniform1fvARB'
trace:wgl:wglGetProcAddress func: 'glUniform2fvARB'
trace:wgl:wglGetProcAddress func: 'glUniform3fvARB'
trace:wgl:wglGetProcAddress func: 'glUniform4fvARB'
trace:wgl:wglGetProcAddress func: 'glUniform1ivARB'
trace:wgl:wglGetProcAddress func: 'glUniform2ivARB'
trace:wgl:wglGetProcAddress func: 'glUniform3ivARB'
trace:wgl:wglGetProcAddress func: 'glUniform4ivARB'
trace:wgl:wglGetProcAddress func: 'glUniformMatrix2fvARB'
trace:wgl:wglGetProcAddress func: 'glUniformMatrix3fvARB'
trace:wgl:wglGetProcAddress func: 'glUniformMatrix4fvARB'
trace:wgl:wglGetProcAddress func: 'glGetUniformfvARB'
trace:wgl:wglGetProcAddress func: 'glGetUniformivARB'
trace:wgl:wglGetProcAddress func: 'glGetInfoLogARB'
trace:wgl:wglGetProcAddress func: 'glUseProgramObjectARB'
trace:wgl:wglGetProcAddress func: 'glCreateShaderObjectARB'
trace:wgl:wglGetProcAddress func: 'glShaderSourceARB'
trace:wgl:wglGetProcAddress func: 'glCompileShaderARB'
trace:wgl:wglGetProcAddress func: 'glCreateProgramObjectARB'
trace:wgl:wglGetProcAddress func: 'glAttachObjectARB'
trace:wgl:wglGetProcAddress func: 'glLinkProgramARB'
trace:wgl:wglGetProcAddress func: 'glDetachObjectARB'
trace:wgl:wglGetProcAddress func: 'glDeleteObjectARB'
trace:wgl:wglGetProcAddress func: 'glValidateProgramARB'
trace:wgl:wglGetProcAddress func: 'glGetAttachedObjectsARB'
trace:wgl:wglGetProcAddress func: 'glGetHandleARB'
trace:wgl:wglGetProcAddress func: 'glGetShaderSourceARB'
trace:wgl:wglGetProcAddress func: 'glBindAttribLocationARB'
trace:wgl:wglGetProcAddress func: 'glGetAttribLocationARB'
trace:wgl:wglGetProcAddress func: 'glCompressedTexImage2DARB'
trace:wgl:wglGetProcAddress func: 'glCompressedTexImage3DARB'
trace:wgl:wglGetProcAddress func: 'glCompressedTexSubImage2DARB'
trace:wgl:wglGetProcAddress func: 'glCompressedTexSubImage3DARB'
trace:wgl:wglGetProcAddress func: 'glGetCompressedTexImageARB'
trace:wgl:wglGetProcAddress func: 'glBindBufferARB'
trace:wgl:wglGetProcAddress func: 'glDeleteBuffersARB'
trace:wgl:wglGetProcAddress func: 'glGenBuffersARB'
trace:wgl:wglGetProcAddress func: 'glIsBufferARB'
trace:wgl:wglGetProcAddress func: 'glBufferDataARB'
trace:wgl:wglGetProcAddress func: 'glBufferSubDataARB'
trace:wgl:wglGetProcAddress func: 'glGetBufferSubDataARB'
trace:wgl:wglGetProcAddress func: 'glMapBufferARB'
trace:wgl:wglGetProcAddress func: 'glUnmapBufferARB'
trace:wgl:wglGetProcAddress func: 'glGetBufferParameterivARB'
trace:wgl:wglGetProcAddress func: 'glGetBufferPointervARB'
trace:wgl:wglGetProcAddress func: 'glGenProgramsARB'
trace:wgl:wglGetProcAddress func: 'glBindProgramARB'
trace:wgl:wglGetProcAddress func: 'glProgramStringARB'
trace:wgl:wglGetProcAddress func: 'glDeleteProgramsARB'
trace:wgl:wglGetProcAddress func: 'glProgramEnvParameter4fvARB'
trace:wgl:wglGetProcAddress func: 'glProgramLocalParameter4fvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttribPointerARB'
trace:wgl:wglGetProcAddress func: 'glEnableVertexAttribArrayARB'
trace:wgl:wglGetProcAddress func: 'glDisableVertexAttribArrayARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib1dARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib1dvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib1fARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib1fvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib1sARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib1svARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib2dARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib2dvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib2fARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib2fvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib2sARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib2svARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib3dARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib3dvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib3fARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib3fvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib3sARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib3svARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NbvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NivARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NsvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NubARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NubvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NuivARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4NusvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4bvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4dARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4dvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4fARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4fvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4ivARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4sARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4svARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4ubvARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4uivARB'
trace:wgl:wglGetProcAddress func: 'glVertexAttrib4usvARB'
trace:wgl:wglGetProcAddress func: 'glGetProgramivARB'
trace:wgl:wglGetProcAddress func: 'glBlendColorEXT'
trace:wgl:wglGetProcAddress func: 'glBlendFuncSeparateEXT'
trace:wgl:wglGetProcAddress func: 'glBlendEquationEXT'
trace:wgl:wglGetProcAddress func: 'glFogCoordfEXT'
trace:wgl:wglGetProcAddress func: 'glFogCoordfvEXT'
trace:wgl:wglGetProcAddress func: 'glFogCoorddEXT'
trace:wgl:wglGetProcAddress func: 'glFogCoorddvEXT'
trace:wgl:wglGetProcAddress func: 'glFogCoordPointerEXT'
trace:wgl:wglGetProcAddress func: 'glBlitFramebufferEXT'
trace:wgl:wglGetProcAddress func: 'glRenderbufferStorageMultisampleEXT'
trace:wgl:wglGetProcAddress func: 'glIsRenderbufferEXT'
trace:wgl:wglGetProcAddress func: 'glBindRenderbufferEXT'
trace:wgl:wglGetProcAddress func: 'glDeleteRenderbuffersEXT'
trace:wgl:wglGetProcAddress func: 'glGenRenderbuffersEXT'
trace:wgl:wglGetProcAddress func: 'glRenderbufferStorageEXT'
trace:wgl:wglGetProcAddress func: 'glIsFramebufferEXT'
trace:wgl:wglGetProcAddress func: 'glBindFramebufferEXT'
trace:wgl:wglGetProcAddress func: 'glDeleteFramebuffersEXT'
trace:wgl:wglGetProcAddress func: 'glGenFramebuffersEXT'
trace:wgl:wglGetProcAddress func: 'glCheckFramebufferStatusEXT'
trace:wgl:wglGetProcAddress func: 'glFramebufferTexture1DEXT'
trace:wgl:wglGetProcAddress func: 'glFramebufferTexture2DEXT'
trace:wgl:wglGetProcAddress func: 'glFramebufferTexture3DEXT'
trace:wgl:wglGetProcAddress func: 'glFramebufferRenderbufferEXT'
trace:wgl:wglGetProcAddress func: 'glGenerateMipmapEXT'
trace:wgl:wglGetProcAddress func: 'glGetRenderbufferParameterivEXT'
trace:wgl:wglGetProcAddress func: 'glGetFramebufferAttachmentParameterivEXT'
trace:wgl:wglGetProcAddress func: 'glProgramEnvParameters4fvEXT'
trace:wgl:wglGetProcAddress func: 'glProgramLocalParameters4fvEXT'
trace:wgl:wglGetProcAddress func: 'glPointParameterfEXT'
trace:wgl:wglGetProcAddress func: 'glPointParameterfvEXT'
trace:wgl:wglGetProcAddress func: 'glProvokingVertexEXT'
trace:wgl:wglGetProcAddress func: 'glSecondaryColor3ubEXT'
trace:wgl:wglGetProcAddress func: 'glSecondaryColor3ubvEXT'
trace:wgl:wglGetProcAddress func: 'glSecondaryColor3fEXT'
trace:wgl:wglGetProcAddress func: 'glSecondaryColor3fvEXT'
trace:wgl:wglGetProcAddress func: 'glSecondaryColorPointerEXT'
trace:wgl:wglGetProcAddress func: 'glActiveStencilFaceEXT'
trace:wgl:wglGetProcAddress func: 'glTexImage3DEXT'
trace:wgl:wglGetProcAddress func: 'glTexSubImage3DEXT'
trace:wgl:wglGetProcAddress func: 'glPointParameterivNV'
trace:wgl:wglGetProcAddress func: 'glPointParameteriNV'
trace:wgl:wglGetProcAddress func: 'glCombinerInputNV'
trace:wgl:wglGetProcAddress func: 'glCombinerOutputNV'
trace:wgl:wglGetProcAddress func: 'glCombinerParameterfNV'
trace:wgl:wglGetProcAddress func: 'glCombinerParameterfvNV'
trace:wgl:wglGetProcAddress func: 'glCombinerParameteriNV'
trace:wgl:wglGetProcAddress func: 'glCombinerParameterivNV'
trace:wgl:wglGetProcAddress func: 'glFinalCombinerInputNV'
trace:wgl:wglGetProcAddress func: 'wglGetExtensionsStringARB'
trace:wgl:X11DRV_wglGetProcAddress ('wglGetExtensionsStringARB'):       (0x7dfc3880) - WineGL
trace:wgl:wglGetProcAddress func: 'wglGetPixelFormatAttribivARB'
trace:wgl:X11DRV_wglGetProcAddress ('wglGetPixelFormatAttribivARB'):    (0x7dfc4cf0) - WineGL
trace:wgl:wglGetProcAddress func: 'wglGetPixelFormatAttribfvARB'
trace:wgl:X11DRV_wglGetProcAddress ('wglGetPixelFormatAttribfvARB'):    (0x7dfc5960) - WineGL
trace:wgl:wglGetProcAddress func: 'wglChoosePixelFormatARB'
trace:wgl:X11DRV_wglGetProcAddress ('wglChoosePixelFormatARB'):         (0x7dfc83a0) - WineGL
trace:wgl:wglGetProcAddress func: 'wglSetPixelFormatWINE'
trace:wgl:X11DRV_wglGetProcAddress ('wglSetPixelFormatWINE'):           (0x7dfcc060) - WineGL
trace:wgl:wglGetProcAddress func: 'wglSwapIntervalEXT'
trace:wgl:X11DRV_wglGetProcAddress ('wglSwapIntervalEXT'):              (0x7dfc2b90) - WineGL
```

---

### Post by unbrained on 2011-10-07
I had the same problem, with ATI. Since it's a 64 bit distro, I had to install lib32 driver from ATI (Archlinux)
Hope it helps ;)

---

### Post by atentik on 2011-10-18
I am having similar issue but I using 32bit. My ```
glxinfo
``` produces
[PHP]glxinfo | grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
[/PHP]
but my ```
sudo lshw -c video
``` produces 
[PHP] description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f8000000-f80fffff memory:e0000000-efffffff iopor[/PHP]
Any help will be great. Thanks.

---

### Post by atentik on 2011-10-19
Any help?

---

