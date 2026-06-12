---
title: "graphic perfomance is shitty, although glxgears works fine"
date: 2009-02-09
forum: Multimedia Software
---

### Post by nlz on 2009-02-09
My output of glxgears is pretty high;

```
7904 frames in 5.0 seconds = 1580.463 FPS
15692 frames in 5.0 seconds = 3138.371 FPS
19331 frames in 5.0 seconds = 3865.646 FPS
17988 frames in 5.0 seconds = 3597.530 FPS
17020 frames in 5.0 seconds = 3403.915 FPS
15938 frames in 5.0 seconds = 3186.832 FPS
18467 frames in 5.0 seconds = 3693.385 FPS
19835 frames in 5.0 seconds = 3966.897 FPS
17180 frames in 5.0 seconds = 3435.893 FPS
19676 frames in 5.0 seconds = 3935.085 FPS
```

but it seems that my PC uses mainly the CPU for this, and not my graphic card (in top I can see that Glxgears uses 98% of CPU power)

If I watch a youtube movie, it's really shitty on my 28" screen, it won't cope with the framerate, but Urban Terror runs perfectly.

I have a 3 GHZ dual core processor and a GeForce FX5700LE.

Is this:
a) a flash problem
b) graphic card config problem
c) typical for an old soundcard

flashversion:
```
kropotkin@gamma:/usr/lib/adobe-flashplugin$ strings libflashplayer.so |grep "LNX"
LNX 10,0,15,3
```
 

Thanks

---

### Post by binbash on 2009-02-09
glxgears is not a benchmark tool.Are you using compiz?If so did you check compiz forums(official compiz forums > tutorials, howtos ?, there are some cool xorg settings to get better performance (not for flash but general)

---

### Post by johnjohn2 on 2009-02-09
> 36184 frames in 5.0 seconds = 7236.701 FPS
40743 frames in 5.0 seconds = 8148.549 FPS
41472 frames in 5.0 seconds = 8294.349 FPS
42177 frames in 5.0 seconds = 8435.265 FPS
40016 frames in 5.0 seconds = 8003.160 FPS
32057 frames in 5.0 seconds = 6401.465 FPS
31524 frames in 5.0 seconds = 6297.709 FPS
33058 frames in 5.0 seconds = 6611.509 FPS
40396 frames in 5.0 seconds = 8079.100 FPS
40128 frames in 5.0 seconds = 8025.499 FPS


ATI 3870 512

using hardly any cpu 
on 64 bit 8.10 and flash is pants

That was also while watching BBC 1 (Streaming)
With Compiz very on

---

### Post by johnjohn2 on 2009-02-09
> 13002 frames in 5.0 seconds = 2599.187 FPS
13006 frames in 5.0 seconds = 2601.155 FPS
13026 frames in 5.0 seconds = 2605.184 FPS
13478 frames in 5.0 seconds = 2695.555 FPS
13105 frames in 5.0 seconds = 2620.966 FPS
13043 frames in 5.0 seconds = 2608.564 FPS
13132 frames in 5.0 seconds = 2626.390 FPS
13024 frames in 5.0 seconds = 2604.795 FPS


was with compiz off

---

### Post by nlz on 2009-02-09
thanks, but i couldn't find a tutorial chapter there, and the howto's only show compiz related stuff ([http://forum.compiz-fusion.org/forumdisplay.php?f=87](http://forum.compiz-fusion.org/forumdisplay.php?f=87)). I wonder if i want more performance if i should rely on compiz. My xorg eats a lot of resources, i would like to see that lessen.

here my xorg.conf:
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

### Post by johnjohn2 on 2009-02-09
turn compiz on and post glxgears results

---

### Post by nlz on 2009-02-09
glxgears with compiz on:

```
9416 frames in 5.0 seconds = 1883.165 FPS
9658 frames in 5.0 seconds = 1931.594 FPS
9450 frames in 5.0 seconds = 1889.956 FPS
7931 frames in 5.0 seconds = 1585.851 FPS
7574 frames in 5.0 seconds = 1512.888 FPS
7440 frames in 5.0 seconds = 1487.958 FPS
8433 frames in 5.0 seconds = 1686.476 FPS
8735 frames in 5.0 seconds = 1746.907 FPS
9650 frames in 5.0 seconds = 1929.961 FPS
9031 frames in 5.0 seconds = 1806.178 FPS
9530 frames in 5.0 seconds = 1905.904 FPS
8589 frames in 5.0 seconds = 1717.376 FPS
8133 frames in 5.0 seconds = 1626.399 FPS
7450 frames in 5.0 seconds = 1489.936 FPS
7617 frames in 5.0 seconds = 1522.564 FPS
5638 frames in 5.0 seconds = 1127.523 FPS
5131 frames in 5.0 seconds = 1025.851 FPS
9233 frames in 5.0 seconds = 1846.535 FPS
```

---

### Post by nlz on 2009-02-11
** bumptiedum **

---

