---
title: "Nvidia drivers not working."
date: 2009-12-13
forum: Mythbuntu
---

### Post by tonycollinet on 2009-12-13
Just set up a front end with nvidia 6200 based graphics card. I need to use the tv out to a standard old/crt analogue tv.

It works fine (except can't sort out overscan) on the standard ubuntu drivers. However, I can't get ANY of the nvidia driver versions to work. If I try them, the graphics card gets messed up - there is no output to the display. and I get the following at the end of xorg.0.log:

After this, I need to power off (not just reset) before I can go reliably again. If I don't power off, I get weird vertical matrix style text on the screen - even during post boot!

```
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) Loading extension NV-GLX


```

---

### Post by Caysho on 2009-12-14
I saw the wierd artifacts in text mode earlier this year when I had a video card dying on me.  I eventually got consistent hangs when GLX was enabled.
Try a different card.

---

### Post by tonycollinet on 2009-12-15
Hmmm

Think I'll try reseating the card. May also look in bios settings.

---

### Post by geekyhawkes on 2009-12-15
SOrry if you have already thought of this, but the most reliable way i found to get nvidia drivers working is to install them in the following way;

Hit Esc during GRUB startup, select recovery mode for the kernal you are running.  Drop to a console (with or without networking).  Select TTY2 (Ctrl and F2), then log in and install the nvidia drivers.  Restart and hopefully it will work for you.

---

