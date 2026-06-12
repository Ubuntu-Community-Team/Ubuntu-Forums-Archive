---
title: "Direct Rendering on other display than :0 problem"
date: 2008-06-21
forum: Multimedia Software
---

### Post by galli on 2008-06-21
Hello everybody.

I've been using ubuntu since 1 year so far. IMHO it is the best operating system I've ever used but this time I need some help :D.

I have an ATI Radeon 9250 running with the free drivers.

My problem is the following:
When the default X session (which runs on display 0 screen 0) starts I have direct rendering enabled and it works like a charm. I can play 3D Games, work with gimp and such. But when I start a new X session on another display, for example display 1, the display starts ok BUT direct rendering is not enabled.

This is the script I am using to start a new X session:
```

X :1 -ac &
cd "/usr/bin/"
sleep 2
DISPLAY=:1
exec "/usr/bin/xfce4-terminal"

```

After the session is started I run a terminal to test if direct rendering is enabled by using "glxinfo | grep direct"

I tried many many things with xorg.conf. I've read the x.org documentation and the dri documentation but I still have no idea how to make this work.

I think it is very funny the fact that I have direct rendering on the first display (:0) and that doesn't work on others. Is there any config file for the displays or something that I am missing? Maybe some driver configuration?

Oh, my xorg.conf is the default one right now. I post it just in case:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
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
EndSection

```

What I tried until now is to set another screen with the same driver and monitor and add it to the default layout by using Screen "new Screen" and that didn't work also I created a new server layout and tried to run the X session with that serverlayout and didn't work either


Any ideas are highly appreciated and sorry for my english I know it is not perfect :).



Thanks in advance!
Galli.

---

