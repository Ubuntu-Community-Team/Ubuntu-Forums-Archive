---
title: "I can't set resolution"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by omoikane on 2007-02-16
I used 1280x1024 resolution recently before ubuntu updates some libraries, but after updating and rebooting my system, resolution falls to 800x 600 and cannot change any more.

I tried to reinstall my graphic card driver, and many howtos in this forum, but failed.

I checked Xorg.0.log file in /var/log and that says..

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.25.53
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     @@@ (CRT-0)
(--) NVIDIA(0): @@@ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "832x624"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(WW) NVIDIA(0): No valid modes for "640x480"; removing.
(WW) NVIDIA(0): No valid modes for "256x256"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

```

and this is my xorg.conf file

```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ed-j on 2007-02-16
Hi!

What version of Ubuntu are you using, and what kind of monitor?

---

### Post by omoikane on 2007-02-16
I'm running 6.10 edgy and my monitor is CRT 17''

---

### Post by ed-j on 2007-02-16
> **omoikane said:**
> I'm running 6.10 edgy and my monitor is CRT 17''

I have tried Edgy on A 17"CRT, all it will give me is 1024x768@85Hz or 1280x1024@60Hz. At th emoment I am trying Ubuntu 5.1 on a 19" CRT, that only gives me 1280x1024@85Hz. I have found all of the setting for 5.1 and 6.1 in:  sudo dpkg-reconfigure xserver-xorg   and then done a restart to complete the changes.

It may be that your monitor is not poweful enough for your graphics card. Hope this helps!

---

### Post by omoikane on 2007-02-16
It cannot helped, I still can't change my resolution, and still gets same warning on log file.

---

### Post by ed-j on 2007-02-16
When configuring the xserver, try setting the choice of graphics card to "vesa" instead of nVidia.

---

### Post by omoikane on 2007-02-16
> **ed-j said:**
> When configuring the xserver, try setting the choice of graphics card to "vesa" instead of nVidia.

ok, i tried "vesa" and get resolution 1280x1024 on login page, but i tried to logging in and enter desktop, it views black display and returned to login page.

---

### Post by ed-j on 2007-02-16
After vesa, set display to 1024x768@75Hz. If this makes no difference, set it to 1280x1024@60Hz. I still think your graphics card may be too much for your monitor and it will only allow you to set 1024x768. Keep trying!.

---

### Post by omoikane on 2007-02-16
> **ed-j said:**
> After vesa, set display to 1024x768@75Hz. If this makes no difference, set it to 1280x1024@60Hz. I still think your graphics card may be too much for your monitor and it will only allow you to set 1024x768. Keep trying!.

Thanks for your help, but how can I change my resolution to 1024x768@75Hz? I can't enter GNOME desktop environment when set it to vesa, and on nvidia, I cannot change my resolution through system -> settings -> screen resolution.

any help will be appriciated

---

### Post by ed-j on 2007-02-16
When the computer is booting up, press "esc" when it says the grub is loading. This will allow you to choose "recovery mode" which is where I thought you set it to vesa?

There are different choices you can make here: Keep pressing esc until you reach a list of resolutions that you can choose. Choose whichever you wish by pressing the "space bar", then enter your choices. You will then be given a choice to set the horizontal and vertical frequencies of your monitor. If you know these, choose "advanced", if you do not know these choose easy. Once you have entered the changes, restart. Good luck!

---

### Post by omoikane on 2007-02-16
Ok, I tried them(1024x768@75Hz and 1280x1024@60Hz), but it also displays login screen though, but when logging in, it fails to start GNOME environment.

---

### Post by ed-j on 2007-02-16
Hi again!

If it were my decision, I would be checking all my cables and connections and thinking of wiping and doing a reinstall if you have no important data. I still think the problem is the monitor.

If I can think of anything else, I will let you know straight away. Best I can do. Goodluck!

---

### Post by Koppie on 2007-03-12
Actually I found this works better:
```
Option "UseEDID" "FALSE"
```
I know it seems like the same, but "IgnoreEDID" "True" didn't work for me and "UseEDID" "FALSE" did.  Go figure.

---

