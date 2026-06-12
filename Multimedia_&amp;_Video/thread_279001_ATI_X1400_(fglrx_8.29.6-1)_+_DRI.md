---
title: "ATI X1400 (fglrx 8.29.6-1) + DRI"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by acidix on 2006-10-17
Hi,
I just installed the fglrx driver from the ati website on my new notebook.
I followed the howto saying i need to install xorg-driver-fglrx, fglrx-kernel-source and fglrx-control.
I successfully loaded the fglrx module in the kernel and the driver itself is working pretty slick.

But fglrxinfo says that OpenGL is still powered by the Mesa driver:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

The xorg log says the following:
```

grep -i dri /var/log/Xorg.0.log |grep -vE "driver|drmOpenDevice"

        X.Org Video Driver: 1.0
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading extension XFree86-DRI
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
        Module class: X.Org XInput Driver
        Module class: X.Org XInput Driver
        Module class: X.Org XInput Driver
        Module class: XFree86 XInput Driver
(II) ATI Proprietary Linux Driver Version Identifier:8.29.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.29g1                
(II) ATI Proprietary Linux Driver Build Date: Sep 19 2006 16:28:13
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
(EE) AIGLX error: dlopen of /usr/lib/dri/fglrx_dri.so failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __glXFindDRIScreen)

```

Suggestion, anyone?

Thanks
Thomas Uhde

---

### Post by cnbiz850 on 2006-10-17
I am at the same problem with you now.  I am guessing that when installing fglrx one needs to force it otherwise mesa would not let it.  Check post "HOWTO: ATI drivers".  I am going to try that tomorrow.  Please post what you find.

---

### Post by Melcar on 2006-10-17
Did you remember to disable the default fglrx driver in the linux restricted modules?  Also, you can try tying from the terminal:

sudo aticonfig --force --initial

and rebooting.

---

### Post by acidix on 2006-10-18
i disabled the fglrx module in /etc/default/linux-restricted-modules and also did an aticonfig --force --initial. nothing has changed.

i also tried symlinking /usr/X11R6/lib/libGL.so.1 to /usr/lib/libGL.so.1.2 which had absolutely no affect on my current config.

maybe it is helpful to post the output of dmesg | grep fglrx:
```

[17179608.304000] fglrx: module license 'Proprietary. (C) 2002 - ATI Tec      s, Starnberg, GERMANY' taints kernel.
[17179608.308000] [fglrx] Maximum main memory to use for locked dma buff       MBytes.
[17179608.308000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on
[17179609.916000] [fglrx] total      GART = 134217728
[17179609.916000] [fglrx] free       GART = 118226944
[17179609.916000] [fglrx] max single GART = 118226944
[17179609.916000] [fglrx] total      LFB  = 126038016
[17179609.916000] [fglrx] free       LFB  = 114143232
[17179609.916000] [fglrx] max single LFB  = 114143232
[17179609.916000] [fglrx] total      Inv  = 0
[17179609.916000] [fglrx] free       Inv  = 0
[17179609.916000] [fglrx] max single Inv  = 0
[17179609.916000] [fglrx] total      TIM  = 0

```

looks pretty nice, doesn't it? but fglrxinfo shows that i am using mesa opengl ...

---

### Post by prince_niceguy on 2007-01-15
it is searching for aiglx. try disabling it... it should work. i had the same issue. i do not have the entry to be made in the xorg.conf. trying googling and you should find it out.
best of luck...

---

