---
title: "screen resolution"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by z987k on 2007-08-24
I have a monitor that supports 1280x1024 but ubuntu is only letting me choose 1024x768 and weird refresh rates like 50, 51 and 53 hz.

I don't know what's up.  If I put "1280x1024" into the modes section of my xorg.conf it does nothing.

Screen is a Samgung SyncMaster 712N and video card is a 6600GT running the nvidia drivers (i think).  The nvidia splash screen doesn't come up so I don't really know if the nvidia drivers are loaded and being used.

xorg.conf screen section:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

---

### Post by heimo on 2007-08-24
Try:
```

    Horizsync    30-81
    Vertrefresh  56-75

```

---

### Post by z987k on 2007-08-24
worked great as for as getting the higher resolution to work, but the refresh rate options are still 50hz and 54hz.  Works and looks fine, so I can live with that I guess.

Question though, why did changing the horizontal sync and vertical refresh allow me to change the resolution to a higher value?

---

### Post by DanPT on 2007-08-24
Go to your monitor website and get the real  Horizsync Vertrefresh

On my old NEC 19" I bought second hand is like H:31-96 V:55-160 **don't use those** number.
Get the right spec for your monitor from either the monitor website or if you still have the owner manual somewhere

Altho 50hz and 54hz is a weird refresh rate so something else might be happening.

---

### Post by heimo on 2007-08-24
> **z987k said:**
> worked great as for as getting the higher resolution to work, but the refresh rate options are still 50hz and 54hz.  Works and looks fine, so I can live with that I guess.
   
You could run xrandr on terminal to see if it also reports just those 50,54Hz options.

> **z987k said:**
> Question though, why did changing the horizontal sync and vertical refresh allow me to change the resolution to a higher value?
Higher resolution probably required higher HorizSync. You could run xvidtune to see what's your current Pixel Clock, Horizontal Sync and VertRefresh. On 1280x1024 mine are: 135MHz, 79.98KHz, 75.02Hz.

---

### Post by z987k on 2007-08-25
I went ahead and looked up some numbers on the monitor and here's what I found in the manual.

Synchronization
Horizontal      30 ~ 81 kHz
Vertical        56 ~ 75 Hz

Resolution
Optimum resolution 1280 x 1024@60 Hz
Maximum resolution 1280 x 1024@75 Hz

Maximum Pixel Clock
140 MHz

to the sync is right on, but it still shows 50,54hz.  Works at 1280x1024 though.

---

### Post by Usbman on 2007-09-05
Any luck with this problem?

Because I have same graphics card as you and I too am only getting 54hz refresh rate. In Edgy it was 75hz.

---

### Post by lask on 2007-09-08
I have the same problem...

---

### Post by lask on 2007-09-08
In Gnome Screen Resolution manager  shows 51Hz but in xorg.conf i set up to 75Hz vsync monitor.
Anybody can explain why is that and maybe haw to fix this?

---

### Post by gummygod on 2007-09-09
im in the same boat. 7.04 and 1280x1024 with only 50 and 54Hz refresh rates available.  my monitor and gfxcard can handle 60Hz for sure and im fairly certain 75Hz too. 
anyone know how to get 60Hz?

---

### Post by wingnux on 2007-12-30
Same here =/

---

### Post by ringmaster on 2008-06-08
The same here, Hardy 8.04 and I am stuck at 50 hz with my M228WD. My card (nvidia 6100 nforce 430 rev. 2) supports 1680x1050 at 60 Hz for sure.

---

### Post by ubuntu-freak on 2008-06-08
It may be lying about the refresh rate. Regarding your res, enter this command in the terminal:
 
**sudo xrandr -q** 
 
Then set the highest resolution supported with:
 
**sudo xrandr -s widthxheight**                         

If that wasn't the resolution you wanted to set, use the "xrandr -q" command again, as it may now list the true maximum resolution.

---

### Post by ringmaster on 2008-06-10
> **reassuringlyoffensive said:**
> It may be lying about the refresh rate. 

Thank you. Yes, it was lying. I installed nvidia-settings from the repositories (I was tempted to install nvidia drivers manually, but if I make this way I loose updates) and there it says 59,99 Hz.

It is useful to activate monitor Vsync and avoid tearing on films.

Sorry for my english.

---

### Post by Unix_Slayer on 2008-06-10
The refresh rate depends on the monitor, and the contrast level. My monitor is an LG 19 inch lcd, with a contrast ratio of 3000:1. So my hz is 50 to 51. It's not un-usual to run at 50 to 55 hz. Depending on the contrast ratio.

Also.... I'm running the lastest drivers from NVida. I installed them manually. It took all of 5 minutes to do. I'm also running multiGPU, and in SLI.

[IMG]http://mysite.verizon.net/mgm_mgm/realnv.jpg[/IMG]
[IMG]http://mysite.verizon.net/mgm_mgm/nv1.jpg[/IMG]

---

