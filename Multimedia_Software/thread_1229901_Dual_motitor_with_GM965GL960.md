---
title: "Dual motitor with GM965/GL960"
date: 2009-08-02
forum: Multimedia Software
---

### Post by 2LSS on 2009-08-02
I am trying to configure a second monitor in hardy on my vaio fz140e laptop. It clones the screen no problem but I can't configure the second screen as an additional workspace. The monitor I am using at the moment is a xenarc 7" vga touchscreen. I have also tried a hp vs19b monitor and my 32" olevia lcd tv with similar results. 
I go to System> Preferences> Screen Resolution and set to this:
[IMG]http://i300.photobucket.com/albums/nn34/2lss/dm1.jpg[/IMG]  

then Apply> Keep Settings> Close. When I click Apply the second monitor pretends to switch but when it turns back on its still cloning the laptop screen. Then if I go back to Screen Resolution it is reset:
[IMG]http://i300.photobucket.com/albums/nn34/2lss/dm2.jpg[/IMG]
I have tried changing the resolution and refresh rate. What am I missing? Is there something I have to change in xorg.conf file?

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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

And here is my lspci 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by 2LSS on 2009-08-05
Bump, Anyone?

---

### Post by eldragon on 2009-08-05
are both displays 1280x800?

2 things could be happening:

1- your virtual desktop size is smaller than 2560, need to set that up in xorg.conf

2- gm965 does not support virtual desktops bigger than 2048x2048. im not sure this is the case with your chipset, it is with mine (gma950)


to test things out, try an place one screen below the other one in the display properties. this will give a virtual desktop of 1280x1600 which should fix issue number 2, if you are still having problems, google the solution for issue number 1.

---

### Post by 2LSS on 2009-08-06
Both displays are theoretically 1280 x 800. The second monitor is a 7" vga that auto detects the resolution. I tried stacking the displays with same results. Then I changed the resolution of the second monitor to 800 x 600 and it worked as one workspace.
[URL="http://jbopensrc.wordpress.com/2008/04/29/quickfix-ubuntu-hardy-dual-monitor-with-intel-945gm-troubles-cant-escape-clone-mode/"]So I googled and came across this: 
[/URL]
```

frank@frank-laptop:~$ xrandr --output LVDS --left-of VGA
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x800)
```

so then I added this to my xorg.conf
```
SubSection “Display”
Virtual 2048 2048
EndSubSection
```
after x restarted I got a message telling me I was in low graphics mode and my display was about 50% smaller. I reverted to my backup and all is good but I don't understand why it didn't work :confused:
Can someone please explain this in easy noob terms?

---

### Post by eldragon on 2009-08-06
> **2LSS said:**
> Both displays are theoretically 1280 x 800. The second monitor is a 7" vga that auto detects the resolution. I tried stacking the displays with same results. Then I changed the resolution of the second monitor to 800 x 600 and it worked as one workspace.
[URL="http://jbopensrc.wordpress.com/2008/04/29/quickfix-ubuntu-hardy-dual-monitor-with-intel-945gm-troubles-cant-escape-clone-mode/"]So I googled and came across this: 
[/URL]
```

frank@frank-laptop:~$ xrandr --output LVDS --left-of VGA
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x800)
```

so then I added this to my xorg.conf
```
SubSection “Display”
Virtual 2048 2048
EndSubSection
```
after x restarted I got a message telling me I was in low graphics mode and my display was about 50% smaller. I reverted to my backup and all is good but I don't understand why it didn't work :confused:
Can someone please explain this in easy noob terms?

hmmm, mine is like this:
```

	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	2048 2048
	EndSubSection

```

anyway, that should work stacking the displays, you need a bigger fb if you want them side by side.

so, modify the virtual line to fill your needs. to know how to tweak it, check
```

man xorg.conf

```

---

### Post by 2LSS on 2009-08-07
Success! I added your 
```
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	2048 2048
	EndSubSection
```
And it works!

Only one problem, when I set up the second monitor it automatically becomes the main screen and my taskbars are moved to it. Is there any way to keep my laptop screen as the main and the second as the empty desktop space?

---

### Post by eldragon on 2009-08-08
> **2LSS said:**
> Success! I added your 
```
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	2048 2048
	EndSubSection
```
And it works!

Only one problem, when I set up the second monitor it automatically becomes the main screen and my taskbars are moved to it. Is there any way to keep my laptop screen as the main and the second as the empty desktop space?

you need to use xrandr for that... i think the command is --primary, read the man pages to learn how to use it


EDIT: when i said it does not support a bigger than 2048x2048 framebuffer, i was wrong, what it does not support is textures bigger than 2048x2048, so if you are not using compiz, you should be able to set them side by side.

---

