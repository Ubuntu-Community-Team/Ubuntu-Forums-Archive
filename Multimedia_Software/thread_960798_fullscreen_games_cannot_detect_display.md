---
title: "fullscreen games cannot detect display"
date: 2008-10-27
forum: Multimedia Software
---

### Post by ghostandmachine on 2008-10-27
I've been unable to play any 3d games at all using ubuntu. The two I've been trying to play was AA and Enemy Territories. Both games I tried to play from the command line go to my monitor saying "cannot display resolution" 1680 x 1050 60Hz.

I have no idea of how to fix this. every where I look on the forums no one has an answer. I don't even know what refresh rates my monitor can do.

Here's my x.org config if that helps.

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

thanks in advance

---

### Post by xnerdx on 2008-10-27
Well first of all lets go ahead and check on your video card, run this command in terminal:
```
lspci | grep VGA
```
Copy the results here! Also can you report the specs of your computer here? Did the game run in windows?

---

### Post by ghostandmachine on 2008-10-27
```
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
```

I used EnvyNG to install my driver.

Specs are as follows:

Dell Dimension E521
AMD Dual
1 gb RAM


AA worked while I used windows (amazing game) but never tried ET.

---

### Post by xnerdx on 2008-10-27
Hmm this has me stuck :(.
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
        BusID           "00:05:00"
EndSection

```
Try changing that then saving it, after you do that press CTRL+ALT+BACKSPACE
I hope this works :(

---

### Post by ghostandmachine on 2008-10-27
no fix.

what is the busid?

---

### Post by ghostandmachine on 2008-10-28
bump

---

### Post by ghostandmachine on 2008-10-30
so just an update if anyone is even seeing this thread anymore.

I've installed fusion-icon to disable compiz to see if that's why I wasn't getting any screen detection. Now I still get cannot display screen with compiz turned off but now I get sound.

Hope this helps anyone who's having the same problems.

---

### Post by ghostandmachine on 2009-01-26
I know this thread is old but I still can't play any games in full screen.

Any help would be great.

---

