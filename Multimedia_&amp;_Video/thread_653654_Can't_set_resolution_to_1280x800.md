---
title: "Can't set resolution to 1280x800"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by trifold on 2007-12-30
Hardware:
HP Pavilion tx1120us laptop
Nvidia GeForce Go 6150
Software:
Ubuntu Gutsy x64 amd
nvidia driver installed:
NVIDIA-Linux-x86_64-169.07-pkg2.run

Files xorg.conf and Xorg.0.log attached.

In Xorg.0.log file first is says:
```

(II) NVIDIA(0):   Validating Mode "1280x800R":
(II) NVIDIA(0):     1280 x 800 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Configuration file ModeLine
(II) NVIDIA(0):       Pixel Clock      : 71.000 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1440
(II) NVIDIA(0):       VRes, VSyncStart :  800,  803
(II) NVIDIA(0):       VSyncEnd, VTotal :  809,  823
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1280x800R": 1280x800
(II) NVIDIA(0):     Mode is valid.

```

then:

```

(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1600x1200R"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(WW) NVIDIA(0): No valid modes for "1600x1200R"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1152x768":

```

also:
```

(II) NVIDIA(0): --- Modes in ModePool for Nvidia Default Flat Panel (DFP-0) ---
(II) NVIDIA(0): "nvidia-auto-select" : 1280 x  800 @  60.1 Hz  (from: EDID)
(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.1 Hz  (from: EDID)
(II) NVIDIA(0): "1280x800R"          : 1280 x  800 @  59.9 Hz  (from: X Configuration file ModeLine)
(II) NVIDIA(0): "1280x800_60"        : 1280 x  800 @  60.1 Hz  (from: EDID)
(II) NVIDIA(0): "1280x800_60_0"      : 1280 x  800 @  59.9 Hz  (from: X Configuration file ModeLine)
(II) NVIDIA(0): "1152x768"           : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1152x768_55"        : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)

```

So, why it doesn't start 1280x800 mode? (i.e. why it fist say it is valid and then no valid modes?)

Best regards,

Luka

---

### Post by pbcartwright on 2007-12-30
did you look at the NVIDIA X server settings tab ?? instead of just right-clicking the desktop look for the NVIDIA settings, I think under System ??

---

### Post by trifold on 2007-12-31
Thanks, I didn't see it! Now it works. It's located Application->System Tools->NVIDiA X Server Settings. But still I don't understand why configuration that I posted doesn't work.

---

