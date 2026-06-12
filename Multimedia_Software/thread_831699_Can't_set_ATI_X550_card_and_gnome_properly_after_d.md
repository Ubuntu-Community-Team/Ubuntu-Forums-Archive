---
title: "Can't set ATI X550 card and gnome properly after disk failure"
date: 2008-06-17
forum: Multimedia Software
---

### Post by g0nzo on 2008-06-17
Hi,

I had Ubuntu 7.10 working with compiz. After updating Ubuntu to 8.04 I lost compiz, but at least Ubuntu worked quite well.

Unfortunately, recently I had small problem with disk (it complained that it's in read-only mode), but fsck managed to fix everything. The problem is that now I get different (and broken) Gnome look and I can't manage to fix it - here's the pic: 

[IMG]http://img178.imageshack.us/img178/2179/brokengnomeog9.png[/IMG]

I get no close/minimize/maximize buttons, I can't even set a wallpaper - all I get is uniform color instead of a picture.

I got ATI X550: "01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]".

I tried installing proprietary drivers, but I got white screen only. So I tried to install ATI drivers using envyng, but I also got white screen. I fixed it by booting into recovery mode, selecting "Fix X server", then booting into console and running "aticonfig --inital -f".

Now my xorg.conf looks like this:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "pl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

fglrxinfo gives me:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

When I tried to run 'compiz --replace' I got this:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b63 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't egistered

```
I've just updated to kernel 2.6.24-19, but it doesn't make any difference.

If there's no easy way to get 3D support on my card - how can I at least bring Gnome back to its default look with working buttons/wallpaper?

Thanks in advance

---

### Post by g0nzo on 2008-06-18
I mananeged to fix missing button by reinstalling metacity and metacity-common, but I still can't i.e. a wallpaper.

Also this bluish Gnome look not only looks worse than the default one, but I also can't create tabs in terminal...

Any tips?

---

