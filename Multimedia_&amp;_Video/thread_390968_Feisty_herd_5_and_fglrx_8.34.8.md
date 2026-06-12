---
title: "Feisty herd 5 and fglrx 8.34.8"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by BadPenny on 2007-03-22
I'm attempting to set my system with Beryl from the svn repository on tuxfamily.org, but cannot get the driver to load. I recently switched over to Kubuntu/Feisty from Debian/sid because I thought this would work. I had it running on the opensource ati driver, but that is (as far as I know) unaccellerated, and I had artifacts when I would move windows etc. I installed both to the xserver-fglrx and xserver-xgl:

```

ii  xserver-xgl                                7.2.0.git.20070224-0ubuntu3            GL-based X serverii  xorg-driver-fglrx                         7.1.0-8.34.8+2.6.20.3-12.11            Video driver for ATI graphics accelerators
ii  xorg-driver-fglrx-dev                     7.1.0-8.34.8+2.6.20.3-12.11            Video driver for ATI graphics accelerators

```

xorg.conf shows I am running the right driver and that the module is getting loaded: 
```

Section "Device"
        Identifier  "ATI Technologies Inc M22 [Radeon Mobility M300]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

```

```

fglrx                 540004  0
agpgart                33480  2 fglrx,intel_agp

```

DRI is getting loaded according to /var/log/Xorg.0.log:

```

(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI

```

and

```

(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.34.8
        ABI class: X.Org Server Extension, version 0.3

```

However...Further down in the log, 

```

WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* * 

```

The beryl wiki says to first insure that glxinfo | grep direct should say direct rendering is yes. My system says:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

What am I missing under Ubuntu to get the fglrx driver working with DRI so I can proceed ? 

Thanks,
--BP

---

### Post by tseliot on 2007-03-22
How did you install the driver?

---

### Post by BadPenny on 2007-03-22
> **tseliot said:**
> How did you install the driver?

Using the Ubuntu restricted repositories.

I got past the original problems, by disabling compositing and turning AIGLX off (included for the benefit of future searchers):

```

Section "Extensions"
     Option    "Composite" "Disable"
EndSection

Section "ServerFlags"
     Option "AIGLX" "Off"
EndSection

```

Now I'm getting the following when trying to start xgl (as configured from the beryl-wiki) from kdm

```

AUDIT: Thu Mar 22 20:56:51 2007: 7066 X: client 2 rejected from local host (uid 1000)

```

I also noted that in /var/log/syslog:

```

 kdm_greet[6369]: Can't open default user face

```

Not sure if its directly related, but I see a ton of errors in ~/.xsession-errors:

```

Xsession: X session started for balexander at Fri Mar 23 22:25:30 EDT 2007
Traceback (most recent call last):
  File "/usr/bin/displayconfig-restore", line 20, in ?
    import ixf86misc
ImportError: No module named ixf86misc
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
kdesktop: WARNING: Pixmap not found for mimetype application/x-x509-ca-cert
*** attempt to put segment in horiz list twice
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.
so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue

```

What is causing this? I moved my .Xauthority to .Xauthority.old, but I don't think this is the problem.
Suggestions?

Thanks,
--BP

---

