---
title: "xorg.conf for DIY vga to scart adapter (nvidia)?"
date: 2008-05-30
forum: Mythbuntu
---

### Post by sonium on 2008-05-30
Hi, I built myself an vga to scart adapter by following [this howto]("http://www.myhtpc.de/showtopic.php?threadid=5482").

They say that nvidia-settings would provide a suitable mode for this adapter
720x576@50Hz/i but it doesn't.

So could someone gratefully provide me a working xorg.conf for this mode?

If I only insert the modeline:
720x576=720,42,72,134,576,3,28,18,15125,41

xorg switches to failsave mode:/

---

### Post by laga on 2008-05-30
I didn't know you could specify modelines in that format.

This site used a have some modelines, but it seems to be offline right now: [http://www.nexusuk.org/projects/vga2scart/](http://www.nexusuk.org/projects/vga2scart/)

I use a DIY VGA->Scart cable, too, but with an ATI card which can provide the composite sync signal. I'm not sure if my modelines would work for you... have you tried searching the mythtv-users mailing list at [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)?

*edit:* I've just noticed that you can read the source of the nexusuk.org web site to find the modelines :)

---

### Post by sonium on 2008-06-01
Hi, thank you for you reply.

I tried to use a modeline given by your link.

I entered the modeline as follows:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "INL LE-1708"
    Modeline       "768x576pali" 14.76  768 789 858 944  576 580 583 625 -hsync -vsync interlace
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
	Modes       "768x576pali"
        Depth       24
    EndSubSection
EndSection
```


this leads the xorg behave like this:

```
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7050 PV / NVIDIA nForce
(--) NVIDIA(0):     630a at PCI:0:18:0:
(--) NVIDIA(0):     INL LE-1708 (CRT-0)
(--) NVIDIA(0): INL LE-1708 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "768x576pali"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
```

---

