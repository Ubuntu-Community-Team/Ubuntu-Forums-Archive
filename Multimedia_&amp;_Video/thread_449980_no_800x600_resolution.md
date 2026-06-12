---
title: "no 800x600 resolution?"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by eilu on 2007-05-20
I checked my screen resolution prefs and there's no 800x600 option, just 1280x800 and 1024x768. Is there a way I can get 800x600? I recall I might have had it before, but it 'disappeared' after I installed 915resolution (not 100% sure on this; although AFAIK I overwrote 600x400 to 1280x800 on setting up 915resolution)

$ lspci outputs video card info as:
```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated 
Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated 
Graphics Controller (rev 03)

```
on $ lspci -v -s 00:02.0 I get:
```
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated 
Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1252
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at feb40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

```
while $ lspci -v -s 00.02.1 returns:
```
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated 
Graphics Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1252
        Flags: bus master, fast devsel, latency 0
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

```

So, is there any way to get 800x600 or is it just not supported?

---

### Post by taurus on 2007-05-20
You can edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and add that resolution in there if you wish.  Save it and then reboot.

---

### Post by eilu on 2007-05-22
The "screen" subsection looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
```

Do I just add "800x600" under Modes? SO it would, for example, be like this:
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "800x600"
	EndSubSection

---

### Post by Ek0nomik on 2007-05-22
> **eilu said:**
> The "screen" subsection looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
```

Do I just add "800x600" under Modes? SO it would, for example, be like this:
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "800x600"
	EndSubSection


Correct.

---

### Post by eilu on 2007-05-22
I tried, but no dice.

The reason I'm looking for 800x600 is I can't play Diablo 2 fullscreen. I load it up, it redraws to 800x600 but something else redraws again to my default so diablo 2 ends up in a small 800x600 windown on the corner of my screen. So now I play windowed, because at least I can move the window to the middle of the screen. I figure if I could manually set 800x600 I could play fullscreen.

---

