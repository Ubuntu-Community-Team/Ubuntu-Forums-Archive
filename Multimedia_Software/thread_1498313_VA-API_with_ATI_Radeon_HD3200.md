---
title: "VA-API with ATI Radeon HD3200"
date: 2010-05-31
forum: Multimedia Software
---

### Post by Solsiden on 2010-05-31
[FONT=Arial][SIZE=3]I have an ASUS motherboard with a build-in ATI Radeon HD3200 graphic card. I am trying to use the HW MPEG4 decoder. [FONT=Arial]However, using MPlayer with the “–vo = VA-API“ option gives an error message and no video is shown.[/FONT][/SIZE][/FONT]

[FONT=Arial][SIZE=3]vainfo:[/SIZE][/FONT]
```

per@music:~$ vainfo
libva: libva version 0.31.0-sds6
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva error: dlopen of /usr/lib/va/drivers/fglrx_drv_video.so failed: libva-0.31.0.5.so.1: cannot open shared object file: No such file or directory
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```
 
[SIZE=3][FONT=Arial][FONT=Arial][SIZE=3]The “fglrx_drv_video.so” links to “xvba_drv_video.so” in the same directory.[/SIZE][/FONT]
 
[/FONT][/SIZE][FONT=Arial][SIZE=3]fglrxinfo:[/SIZE][/FONT]
```

per@music:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 3.2.9756 Compatibility Profile Context

```
 
 
[FONT=Arial][SIZE=3]Any ideas are appreciated, as I am still new to Linux.[/SIZE][/FONT]

---

