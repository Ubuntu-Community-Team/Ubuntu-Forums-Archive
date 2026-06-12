---
title: "GMA 3150 problems"
date: 2010-05-16
forum: Multimedia Software
---

### Post by bedgen on 2010-05-16
hi! i use netbook asus eeepc 1001p with UNR 10.04
it works on gma 3150 video card
```
$ uname -a
Linux revx 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```i try to run fallout 2 with wine
```
$ wine fallout2.exe 
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef00,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1bdbb8,0x1bdff8): stub

```glxgears works properly.

how can i fix it?

P.S. i got jolicloud like 2d OS. and fallout works there. and there no any errors.

---

### Post by bedgen on 2010-05-17
up

---

