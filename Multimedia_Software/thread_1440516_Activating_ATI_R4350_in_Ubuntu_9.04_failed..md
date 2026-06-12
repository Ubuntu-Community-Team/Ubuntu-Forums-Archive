---
title: "Activating ATI R4350 in Ubuntu 9.04 failed."
date: 2010-03-27
forum: Multimedia Software
---

### Post by _nikolaos on 2010-03-27
Everything started after upgrading from 8.10 upto 9.04. At first, I had no graphics, after downloading the right driver for my ATI R4350 card things seemed to go well.

Though, that's the situation right now:

(1) In the GNOME,

**System -> Preferences -> ATI Catalyst Control Center (Administrative)**

pops up this window

```
**Initialization error**
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

```

(2) From **System -> Administration -> Hardware drivers**, it shows a window:
```

ATI/AMD proprietary FGLRX graphics driver
...
This driver is not activated.

```

and the "Activate" button does not activate anything.

(3) From a terminal window, I tried:

```

$ cat /var/log/Xorg.0.log|grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed
(EE) GLX error: Can not get required symbols.

```

(4) **glxinfo** goes *Segmentation fault*.

(5) If I run VLC media player, its window title shows **(x11 output)**.

(6) On a terminal,
```

$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

```

So, my video graphics card is not working properly. Is there something that I can do to fix the situation?

Should I download some different driver?

My kernel's 2.6.28-18-server.

Thanks in advance.

----

Eventually, I installed Ubuntu 10.04 which recognized the card and works fine.

---

