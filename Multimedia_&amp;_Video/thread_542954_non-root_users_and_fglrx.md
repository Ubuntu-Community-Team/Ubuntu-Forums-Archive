---
title: "non-root users and fglrx"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Saulnier on 2007-09-04
Hi,
I'm quite not to GNU/Linux, have been toying with Ubuntu v7.04 recently. I used apt-get install kdebase kde-core kde kubuntu-desktop to install KDE 3.5.6.
I then upgraded the kernel to v2.6.22-10-generic and installed fglrx v8.40.4 drivers from AMD's homepage.

I've got DRI initializing, 2D and 3D acceleration working for my primary user (The one created by the Ubuntu installer,) however my secondary user (Which I created using Gnome's Users and Groups program,) cannot, according to the /var/log/Xorg.0.log it fails to initialize the UMM driver.

I looked in the /var/log/kdm.log as well, which gave a more detailed description:
firegl_InitUMM failed.

I've searched google a bit without being able to find anything about a "UMM" driver or why it wouldn't be initializing. Any thoughts would be most appreciated!

Here's some additional information about my system:

P4 Prescott (2.8E, 32-bit)
SAPPHIRE X1600 (AGP 8x, GDDR2)

/etc/X11/xorg.conf
```

Section "ServerLayout"
	Identifier     "Layout[0]"
	Screen         "Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier  "ViewSonic"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Radeon R530"
	Driver      "fglrx"
        Option      "UseFastTLS" "2"
        Option      "VideoOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "Radeon R530[Secondary]"
        Driver      "fglrx"
        BusID       "PCI:1:0:1"
EndSection

Section "Screen"
	Identifier  "Screen[0]"
	Device      "Radeon R530"
	Monitor     "ViewSonic"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
        Identifier  "Screen[1]"
        Device      "Radeon R530[Secondary]"
        Monitor     "ViewSonic"
        DefaultDepth     24
        SubSection "Display"
               Viewport   0 0
               Depth      24
        EndSubSection
EndSection

Section "ServerFlags"
      Option   "AIGLX" "no"
EndSection

Section "Extensions"
      Option   "XVideo" "yes"
      Option   "Composite" "no"
EndSection

Section "DRI"
	Mode   0666
EndSection

```

/var/log/Xorg.0.log && /var/log/kdm.log
```

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
firegl_InitUMM failed
(EE) fglrx(0): Failed to initialize UMM driver.
(WW) fglrx(0): Failed to set up write-combining range (0xcf000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xce000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcc000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc8000000,0x7fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0xffe0000)
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!

```

---

### Post by wolfen69 on 2007-09-04
```
sudo apt-get install kubuntu-desktop
```
would have sufficed.

---

### Post by thelocust on 2007-09-04
I would use envy to uninstall and reinstall. My guess is that would fix it.

---

