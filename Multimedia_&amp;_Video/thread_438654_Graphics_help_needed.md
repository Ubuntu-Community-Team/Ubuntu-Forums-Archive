---
title: "Graphics help needed"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by Aneirin on 2007-05-09
Ok, before I get into the details, I'll just say I'm rather mixed in my linux experience.  Learned how to code and compile C, learned (and forgot the next week) how to write bash scripts, know almost nothing about gui's in linux.  Anyway, I'm having a problem getting a decent graphics resolution.

I'm running Ubuntu 7.04 with a GeForce 5200 card in the PCI slot and a generic (Envision) monitor.  When I try to configure this (according to help guides available online) I'm getting some odd messages in the log

My xorg.conf for the display section looks like:

> Section "Device"
	Identifier	"GeForce"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	262144
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"EN-710"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	60, 75, 85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GeForce"
	Monitor		"EN-710"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

and the message in the log reads:
> (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     @X@ ENVISION ?N?? (CRT-0)
(--) NVIDIA(0): @X@ ENVISION ?N?? (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(WW) NVIDIA(0): @X@ ENVISION ?N?? (CRT-0)'s EDID does not contain a maximum
(WW) NVIDIA(0):     image size; cannot compute DPI from @X@ ENVISION ?N??
(WW) NVIDIA(0):     (CRT-0)'s EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp

Now since I'm stronger on Micro$haft and fairly weak here, can anyone please tell me what I'm doing wrong?  I'd love to be able to use Ubuntu, but I need something better than 800x600 on a 17 inch monitor.  Thanks.

---

### Post by dfreer on 2007-05-09
sounds like it didn't detect your monitor correctly, I would look into adding the mode line for your monitor, this *may* help. 
[http://julipedia.blogspot.com/2007/03/x11-mode-line-generator.html](http://julipedia.blogspot.com/2007/03/x11-mode-line-generator.html)
my two cents, good luck!

---

### Post by Aneirin on 2007-05-10
Unfortunately, that didn't work.   I got the lines:
```
# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
```
in the xorg.conf under the monitor section (is that the correct place?) and it came back wit the same log information as before.  Thanks for the try though, and do you have any more thoughts?

---

