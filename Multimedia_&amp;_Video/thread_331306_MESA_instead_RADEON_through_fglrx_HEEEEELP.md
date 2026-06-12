---
title: "MESA instead RADEON through fglrx HEEEEELP"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by aDOT on 2007-01-04
Please I need help,
I read a lot of topics about HOWTO install fglrx, but result is the same => :evil: MESA:evil: 
Please tell me what do I do wrong?

I installed ubuntu 6,10, and I am trying to install fglrx for Radeon Mobility  9700.
I made link to /usr/lib/dri as  /usr/lib/xorg/modules/dri, so why:

[PHP](II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *[/PHP]

I attached X.log for more details.

](*,)

---

### Post by Dekunuts on 2007-01-04
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

that one worked for me

---

### Post by aDOT on 2007-01-05
Thank you for help,
I used [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) guide , that looks the same as "wiki's". So, now I have another problem:
```
andrew@andrew-laptop:~$ LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.32.5 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.32.5 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

More, I have not /etc/X11/Xsession.d/10fglrx to remove it :( as link above advises
I think that just creating link to /usr/lib/xorg/modules/dri (there is  fglrx_dri.so lies ) is not good idea. So, what do I must to do????

---

