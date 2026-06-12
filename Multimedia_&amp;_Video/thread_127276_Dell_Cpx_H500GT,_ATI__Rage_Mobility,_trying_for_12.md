---
title: "Dell Cpx H500GT, ATI  Rage Mobility, trying for 1280x1024"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by bekamyn on 2006-02-08
Ok I've been reading everything I can trying every option I can think of but I just can't get this laptop to do 1280x1024. I can only get a maximum of 1024x768. I don't need 3D acceleration or anything like that just a higher resolution. 

Maybe you can tell me what I'm doing wrong. Here is my xorg.conf. I've tried using the ati and vesa driver.
My order of operation
1. Exit Fluxbox
2. Ctrl+alt+F3
3. /etc/init.d/gdm stop
4. dpkg-reconfigure xserver-xorg
5. /etc/init.d/gdm start
6. Login
7. Run Gnome Control Center and check what resolutions are available

My understanding is the fglrx driver will not work for this card and since I don't care about 3D that's fine with me.

Xorg.conf
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"type1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Rage Mobiltiy M1"
	Driver		"vesa" #tried ati also
	BusID		"PCI:1:0:0"
	VideoRam	8192
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	31.5-48.5
	VertRefresh	50-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Rage Mobiltiy M1"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

lspci output
```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)


```

lspci -n output
```

0000:00:00.0 0600: 8086:7190 (rev 03)
0000:00:01.0 0604: 8086:7191 (rev 03)
0000:00:03.0 0607: 104c:ac1c (rev 01)
0000:00:03.1 0607: 104c:ac1c (rev 01)
0000:00:07.0 0680: 8086:7110 (rev 02)
0000:00:07.1 0101: 8086:7111 (rev 01)
0000:00:07.2 0c03: 8086:7112 (rev 01)
0000:00:07.3 0680: 8086:7113 (rev 03)
0000:00:08.0 0401: 125d:1978 (rev 10)
0000:01:00.0 0300: 1002:4c4d (rev 64)

```

So, what exactly am I doing wrong?

---

### Post by kch_86 on 2006-02-09
I believe the highest resolution that the monitor on that laptop supports is 1024x768.

---

### Post by bekamyn on 2006-02-10
You are right, I failed to see that when I was in Win2000 it was changing the external video resolution (1280x1024 max) not the internal which apparently only supports 1024x768.

---

### Post by kch_86 on 2006-02-10
Yeah it kinda sucks. I have the j version and I'm used to 1280 resolution. I miss the extra screen space. But for a 240 dollar laptop I can't complain.

---

