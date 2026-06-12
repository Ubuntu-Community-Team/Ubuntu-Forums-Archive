---
title: "ATi drivers plus CRT"
date: 2009-04-23
forum: Multimedia Software
---

### Post by DoktorSeven on 2009-04-23
I've had an issue installing any version of Ubuntu on this computer which has an ATi Radeon HD 3200 integrated graphics card on it.  Drivers will install correctly and the screen will come up huge (1600x1200) but any attempt to resize the screen has issues.  3d is working correctly, however, as reported by both glxinfo and fglrxinfo.

The Display application will frequently freeze whenever I try to change resolutions, a lot of horizontal lines will streak up and down for a while, and worse, I cannot select anything over 60Hz for my monitor.  It seems to be attempting to automatically get information from my monitor which apparently it does not provide or Xorg (or something related) doesn't properly recognize:

```
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000001, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(EE) fglrx(0): Unknown EDID version 0
(II) fglrx(0):  Display1: Failed to get EDID information. 
(II) fglrx(0): Output DFP2 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1600x1200

```
(from Xorg.0.log)

It also ignores any manual attempt to specify sync/refresh rates for my monitor which have been added into xorg.conf (that have worked perfectly in the past).

It's gotten to me that lately Linux distros have apparently tried to bypass perfectly rational manual configuration for this strange sort of automation that never seems to work.  Is there a real solution for this, or am I stuck until I waste money buying new hardware that appeases this strange new process?

Edit: ATI CCC does the same, no ability to change from 60Hz and shows vertical lines while starting.

Edit 2: I know it's something to do with the DFP2 output being default and xorg using information from the existing xorg.conf section when it doesn't exist, but I find no reasonable way to tell it to do otherwise.  aticonfig has a --force-monitor option but nothing I do can tell it to disregard anything but the CRT.

Frustrating.

---

### Post by DoktorSeven on 2009-04-24
Probably futile bump.  I'm sure that's the issue now; xorg/fglrx/something is looking at the DFP2 output as being default (which apparently is my HDMI output, which isn't being used at all) and applying any monitor information to only it and only falling back on my CRT after it fails to detect it.

No amount of telling fglrx that I want to only use crt1 or any xorg.conf configuration hackery will allow it to work, and there is no way to turn off that output port any other way (no BIOS option).

Any method I'm missing, or is this just a bug/problem with xorg/fglrx?

---

### Post by Saint_ on 2009-04-26
Hey bro, christ knows im not the one to help you, but i'm running the same video card and im having some issues with it too, so im curious as to whether or not you get them. My video playback is real sketchy, like the videos appear "glitchy" and flash black spiratically, the flahses last fractions of a second, but they're real noticeable. Also, when minimizing/maximizing dialogs, the entire window will have a checkered pattern to it for roughly a second before rendering the entire window, etc. So i'm just wondering if you're having these problems as well.

---

