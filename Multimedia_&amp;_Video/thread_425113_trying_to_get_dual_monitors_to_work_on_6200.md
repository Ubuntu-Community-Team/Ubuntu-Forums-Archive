---
title: "trying to get dual monitors to work on 6200"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by gado_gad on 2007-04-27
Hi
Im trying to get my two monitors to work on my computer
I have 2 monitors both crt a 17" and a 15"
the 17" on the left and the 15" on the right of my desk
the 17" is the main monitor
I was able to get them both to work at the same time but with the 15" as the "left" monitor and the screen resolution for both was really low

So what im trying to get is the 17" on the left to be the main monitor at 1280x1024 and the 15" on the right to be secondary at 1024x768

This is what I currently have (17" working at 1280x1024, 15" Blank)

Section "Device"
	Identifier	"nVidia Corporation NV44A [GeForce 6200]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option 		"TwinView" "True"
	Option		"TwinViewOrientation" "RightOf"
	Option		"ConnectedMonitor" "crt, crt"
	Option		"Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
	Option		"UseDisplayDevice" "CRT"
EndSection

---

