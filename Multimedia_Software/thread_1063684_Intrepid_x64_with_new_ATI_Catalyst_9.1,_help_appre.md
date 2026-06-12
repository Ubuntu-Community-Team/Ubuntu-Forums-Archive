---
title: "Intrepid x64 with new ATI Catalyst 9.1, help appreciated!"
date: 2009-02-08
forum: Multimedia Software
---

### Post by niallporter on 2009-02-08
Hi all,

I've been holding off upgrading to Intrepid until the issues between the new X version and ATI drivers were resolved.  I saw the other day that ATI had released Catalyst 9.1 so I put a fresh Intrepid x64 install onto a free partition, patched it fully and had a go with the Catalyst drivers according to the instructions given here:  [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Having followed that lot to the letter, I get the "Ubuntu is running in Low Graphics mode" message once it's finished booting up and the tail end of my Xorg.0.log file looks like this:
```

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 8/8
(EE) fglrx(0): Given depth (8) is not supported by fglrx driver
(EE) fglrx(0): PreInitVisual failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
SetVBEMode failed
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

My xorg.conf looked like this after I'd finished the instructions in the above link:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection
```

Thinking maybe it was defaulting to an unsupported colour depth/resolution I changed the Screen section to this:

```
Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1920x1200"
	EndSubSection
EndSection
```

But that didn't help at all either.  BTW, the graphics hardware is a Radeon X800XL, AGP version.

Anyone got any ideas?

TIA
Niall

---

### Post by johnjohn2 on 2009-02-08
> **niallporter said:**
> Hi all,

I've been holding off upgrading to Intrepid until the issues between the new X version and ATI drivers were resolved.  I saw the other day that ATI had released Catalyst 9.1 so I put a fresh Intrepid x64 install onto a free partition, patched it fully and had a go with the Catalyst drivers according to the instructions given here:  [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Having followed that lot to the letter, I get the "Ubuntu is running in Low Graphics mode" message once it's finished booting up and the tail end of my Xorg.0.log file looks like this:
```

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 8/8
(EE) fglrx(0): Given depth (8) is not supported by fglrx driver
(EE) fglrx(0): PreInitVisual failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
SetVBEMode failed
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

My xorg.conf looked like this after I'd finished the instructions in the above link:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection
```

Thinking maybe it was defaulting to an unsupported colour depth/resolution I changed the Screen section to this:

```
Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1920x1200"
	EndSubSection
EndSection
```

But that didn't help at all either.  BTW, the graphics hardware is a Radeon X800XL, AGP version.

Anyone got any ideas?

TIA
Niall

9.1 has too many flaws to be useable.i would sugget uninstall and go with the ubuntu FGLRX driver supplied!

---

### Post by niallporter on 2009-02-08
> **johnjohn2 said:**
> 9.1 has too many flaws to be useable.i would sugget uninstall and go with the ubuntu FGLRX driver supplied!

I tried that originally on a previous install but the supplied driver available from the restricted drivers settings doesn't work right for me, I get major corruption when using compiz or any OpenGL apps.

I'd have thought ATI's drivers might be getting better over time, each new one just seems to be worse than the last for me. :(

---

