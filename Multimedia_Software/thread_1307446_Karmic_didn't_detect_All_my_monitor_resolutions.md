---
title: "Karmic didn't detect All my monitor resolutions"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Sensiva on 2009-10-31
As I described here[ https://answers.launchpad.net/ubuntu/+question/87388]("https://answers.launchpad.net/ubuntu/+question/87388")

Is there a way to get 1600x1200 resolution on my 21 inch **hp p 1230** monitor?

Thank you

---

### Post by tipul07 on 2009-11-03
Same problem here... I have a 20" LG Flatron L2010B, Nvidia 7300 GT.

First I tried "easy" way using nvidia-settings and nvidia-xconfig. It was an improvement as resolution defaulted to 800x600 or 1024x768 and I got to 1152x864... well max resultion is 1360x768, but that's for widescreens...

So got stuck with 1152x864...

Then tried "manual" part...

Tried [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) to get some 1600x1200 Modelines in monitor section, edited xorg.conf and added:

```

    #ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    Modeline "1600x1200@60" 176.70 1600 1632 2296 2328 1200 1224 1236 1261
    #ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

```

With combinations of:

```

Option "metamodes" "1600x1200"

```

```

Option "metamodes" "1600x1200 +0+0"

```

```

Option "metamodes" "1600x1200@60;1280x1024@60"

```


Usually I get in /var/log/Xorg.0.log something like: "No valid modes for "X"; removing." Where X is one of metamodes like in example below:

```

(**) NVIDIA(0): Option "MetaModes" "1600x1200 +0+0"
(**) Nov 03 13:38:47 NVIDIA(0): Enabling RENDER acceleration
(II) Nov 03 13:38:47 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Nov 03 13:38:47 NVIDIA(0):     enabled.
(WW) Nov 03 13:38:47 NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(II) Nov 03 13:38:47 NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:4:0:0 (GPU-0)
(--) Nov 03 13:38:47 NVIDIA(0): Memory: 524288 kBytes
(--) Nov 03 13:38:47 NVIDIA(0): VideoBIOS: 05.73.22.51.60
(II) Nov 03 13:38:47 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Nov 03 13:38:47 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Nov 03 13:38:47 NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:4:0:0:
(--) Nov 03 13:38:47 NVIDIA(0):     CRT-1
(--) Nov 03 13:38:47 NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(II) Nov 03 13:38:47 NVIDIA(0): Assigned Display Device: CRT-1
(WW) Nov 03 13:38:47 NVIDIA(0): No valid modes for "1600x1200+0+0"; removing.
(WW) Nov 03 13:38:47 NVIDIA(0):
(WW) Nov 03 13:38:47 NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) Nov 03 13:38:47 NVIDIA(0):     "nvidia-auto-select".
(WW) Nov 03 13:38:47 NVIDIA(0):
(II) Nov 03 13:38:47 NVIDIA(0): Validated modes:
(II) Nov 03 13:38:47 NVIDIA(0):     "nvidia-auto-select"
(II) Nov 03 13:38:47 NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) Nov 03 13:38:47 NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) Nov 03 13:38:47 NVIDIA(0):     from CRT-1's EDID.
(==) Nov 03 13:38:47 NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) Nov 03 13:38:47 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

```

I know I had problems with same video card/monitor with 9.04, but after some googles/digging found a solution and got to 1600x1200.

Anything got into this situation too and found a solution please share.

Thnx,
Andy

---

### Post by Sensiva on 2009-11-07
The weird thing is... I can't find the bloody xorg.conf file :mad:

---

