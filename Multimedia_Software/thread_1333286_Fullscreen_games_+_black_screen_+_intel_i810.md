---
title: "Fullscreen games + black screen + intel i810"
date: 2009-11-21
forum: Multimedia Software
---

### Post by Nahuel_ on 2009-11-21
Hello everyone, I'm currently running Linux Mint 7 on a HP Pavilion dv1014la laptop. I'm posting here since I believe the solution for both Ubuntu and Mint should be similar. If not, please excuse me and mods can lock/delete the thread.
Everytime I run a game in fullscreen mode, the screen just goes black. However, it doesn't crash since I can hear the music from the game and I can control it. I just don't see anything. I can exit by just pressing ESC. 

Here's some information:

PC: HP pavilion dv1014la 

lspci -v | grep Graphics
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

current xorg.conf
```
Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	#  InputDevice	"SynapticsTouchpad" "SendCoreEvents"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "intel"
	VendorName  "Intel Corporation"
	BoardName   "82852/855GM Integrated Graphics Device"
	Option         "Legacy3D" "false"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection
```

That's what my current xorg.conf looks like. It has some options that I added in order to test if it could solve anything with some stuff I found researching, but with no results. Usually, my xorg.conf looks just like this:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

Another thing. When I tried to change the resolution of the screen, it crashed completely. There's another game I use (neverball) which doesn't run in fullscreen. It works fine, but when I drag the window, the graphics are still painted where the window was before... hope that's clear.

I made some research here and in other places, but none of the solutions helped. I *guess* the closest one was following this guide:
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)
By adding **Option &#8220;AccelMethod&#8221; &#8220;UXA&#8221;** to xorg.conf, neverball doesn't do what I described above.
Thanks! Any help highly appreciated.

---

### Post by Nahuel_ on 2009-11-21
Well, I fixed it. If someone's interested, I followed the **Safe Configuration** instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Thanks.

---

