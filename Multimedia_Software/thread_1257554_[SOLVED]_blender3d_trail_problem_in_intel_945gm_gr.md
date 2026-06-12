---
title: "[SOLVED] blender3d trail problem in intel 945gm graphic card"
date: 2009-09-03
forum: Multimedia Software
---

### Post by ryecomp on 2009-09-03
I have many issues around graphic problem in intel 945gm on-board graphic card.
Current system configuration is ubuntu 9.04, intel graphic card driver 2.4 (reverted)
blender3d 2.48a, 

Glxgears reported as high as 800 FPS when UXA acceleration is turned on.

But blender3d leaves lot of trails and almost all icons image is missing... making it
impossible to use. 

I slowed down system to use blender3d. (/etc/X11/xorg.conf). With following 
configuration glxgears report 180 FPS!!

Section "Device"
	Identifier	"Configured Video Device"
	Option		"NoAccell"	"1"
#	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" # i8xx users: see note in guide
EndSection

But blender3d did not leave any trail. And all icons image turns back to 
original shape.

---

### Post by ryecomp on 2009-09-04
NO... NOT solved yet. 

This looks the problem was partially solved, but the true is that 
xorg.conf is not related to solving the problem. 

Real picture is like this ... 
"Restarting x repetitively (tty7 to tty1 to ...) reduces frame rate (glxgears)
from 800 FPS to 360 FPS to 180 FPS... when it reached 180 FPS, 
blender start to operate normally. "

xorg.conf parameter whether acceleration is turned on or not,
whether it is uxa or not... is not related to solution...

---

