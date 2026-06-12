---
title: "[fglrx:firegl_init] *ERROR* Device not found!"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by abovett on 2005-10-17
Hi

I have an old Radeon card (7200 I believe). 3D used to work OK in Hoary, but I just did a dist-upgrade from Hoary to Warty and 3D stopped working. Got it going again with the Xorg "ati" driver (which I _think_ was what I was using before), but performance is awful.

So I tried installing the fglrx driver, but it refuses to install the kernel module - says "Device not found", but I'm not sure why. Does it mean it can't find the card, and if so what can I do about it?

Here's the relevant output (I think) of lspci and dmesg:
```
[andrew@jupiter-ubuntu ~]$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]
[andrew@jupiter-ubuntu ~]$ dmesg | grep fglrx
[4294694.484000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294694.509000] [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
[4294694.509000] [fglrx:firegl_init] *ERROR* Device not found!

```

If I try to enable the fglrx driver in xorg.conf, it fails (obviously).

Anyone any ideas? And why is the regular "ati" driver so much slower than it was before? If I could get reasonable performance out of that I'd be happy - I'm only looking to use it for simple things like crack-attack and nice screen savers.

Thanks

Andy B


Thanks

---

### Post by Golgoth on 2005-10-17
try the "radeon" driver instead of "ati" or "fglrx"

some info [here]("http://ubuntuforums.org/showpost.php?p=413031&postcount=10")

---

### Post by abovett on 2005-10-17
[QUOTE=Golgoth]try the "radeon" driver instead of "ati" or "fglrx"[/QUOTE]

Thanks. My bad - should have spotted that - so many posts on ATI I missed it.

However - no improvement :( graphics still dead slow.

Here's my xorg.conf file - can anyone spot any problems?

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
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7200 (R100 QD)"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option 		"AGPMode" "4"
	Option 		"AGPSize" "64" # default: 8
	Option 		"RingSize" "8"
	Option 		"BufferSize" "2"
	Option 		"EnablePageFlip" "true"
	Option 		"EnableDepthMoves" "true"
	Option 		"RenderAccel" "true"
	#Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"CMC 17 AD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7200 (R100 QD)"
	Monitor		"CMC 17 AD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "RENDER" "Enable" 
EndSection


```

TIA

Andy B

---

### Post by abovett on 2005-10-17
Progress!

Turns out I've been on the wrong track. I've been seeing one of two symptoms as I've messed around with my radeon drivers and xorg.cong settings - either 3D is _extremely_ slow, or I get an "illegal instruction" error trying to run 3D apps. The second is the clue - it's [bug 15036]("https://bugzilla.ubuntu.com/show_bug.cgi?id=15036").

Just one problem (at the moment) - the fix Daniel Stone offers (libgl1-mesa-dri_6.3.2-0ubuntu7_i386.deb) has a dependancy problem - it wants libgl1-mesa_6.3.2-0ubuntu7_i386 but only libgl1-mesa_6.3.2-0ubuntu6_i386 is installed. I got it to install using --force-depends, but apt is now upset (of course). Anyone know if libgl1-mesa_6.3.2-0ubuntu7_i386 actually exists (yet)?

Regards

Andy B

---

### Post by Golgoth on 2005-10-18
have you removed the "fglrx" stuff with synaptic: xorg-driver-fglrx et fglrx-control?

same question for your /etc/modules file...

---

### Post by abovett on 2005-10-18
[QUOTE=Golgoth]have you removed the "fglrx" stuff with synaptic: xorg-driver-fglrx et fglrx-control?

same question for your /etc/modules file...[/QUOTE]

Yes did all that. Even tested the new fix on a clean Breezy install on another hard disk.

As I say - the new libgl1-mesa-dri_6.3.2-0ubuntu7_i386.deb from the bugzilla post is the fix - everything works fine once it's installed. It's just that it's not yet been uploaded to the apt repository, and has a dependency on another package which isn't yet available. The dependency isn't that important, obviously, because if I override it with --force-depends then all my 3D stuff is fine. I've gone back to libgl1-mesa-dri_6.3.2-0ubuntu6_i386 (and no working 3D) at the moment to avoid problems with apt-get - I'm just waitinfg for this package and its dependencies to appear in the repositories.

Regards

Andy B

---

