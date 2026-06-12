---
title: "video problems... restricted drivers."
date: 2008-08-27
forum: Multimedia Software
---

### Post by zx6r1033 on 2008-08-27
While watching movies, either from DVD or streaming, I get this really odd video. It looks the same as before you load drivers for the video card in windows. It is like this scrolling bar that changes the frames. 

Anyway... I was going on the assumption that it a bad refresh rate, since I have the newest driver version installed.  I cannot change the res or refresh rate at the moment. I am hoping someone can tell me what is going on or how to fix it.


This is my xorg file:

```

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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

