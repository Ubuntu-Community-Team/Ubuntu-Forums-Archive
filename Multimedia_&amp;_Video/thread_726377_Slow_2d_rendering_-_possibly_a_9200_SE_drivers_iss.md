---
title: "Slow 2d rendering - possibly a 9200 SE drivers issue"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by entwoska on 2008-03-16
Hi, I know that there's a lot of threads about older Radeon cards like mine (9200 SE) but after reading tons of those, I'm still stuck with a couple of questions.


First, my problem is that the 2d rendering seem to be handled greatly by my cpu and not by my ati card like it should. Nothing dramatic mind you, the problem appear on web pages with lots of animations for example. The web page becomes jerky. The Xorg process is eating up all of my process power (up to 90%).


I'm using the "ati" wrapper since the proprietary drivers are not compatible with the Radeon 9200 SE anymore.

So I'd like to know if there are some options in the xorg.conf file that would optimize my performances, or if the proprietary drivers (the 8.28.8 version) is an option on Gutsy Gibbon 7.10 (and if these would possibly help).

Also I just noticed that the output for :

```
glxinfo | grep rendering
```
is 
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

Anything I can do about this?

My specs:
Ubuntu 7.10
Asus video card with Radeon 9200 SE (RV280 chipset)
Pentium 4 3Ghz
2G of RAM

And here is the device section from my xorg.conf file :

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver		"ati"
	Busid		"PCI:1:0:0"
	Option		"AGPMode"	"8"
	Option		"BusType"	"AGP"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod"	"XAA"
	Option		"AccelDFS"	"false"
	Option		"DRI"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
        Option          "DMAForXv"       "true"


Thanks and looking forward to your answers!

---

### Post by xc3RnbFO8P on 2008-03-16
I found this:

[http://forum.compiz-fusion.org/showthread.php?t=5953]("http://forum.compiz-fusion.org/showthread.php?t=5953")

---

### Post by entwoska on 2008-03-16
Ok so I got to make the direct rendering work by removing any old ati drivers I had left.

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 TCL

```

The problem persists though. I always have a little lag when I switch from window to window. Any video refresh is a whole lot of work and makes the Xorg process scream.

Seems to me that my video card is not working hard, letting the hard work for my cpu.

Any ideas, suggestions ? Thanks.

---

### Post by xc3RnbFO8P on 2008-03-16
Just this:

[http://ubuntuforums.org/showthread.php?t=550082&page=6]("http://ubuntuforums.org/showthread.php?t=550082&page=6")

---

### Post by entwoska on 2008-03-17
So I cleared all the options in my xorg.conf file except for the "DRI" "true" option.

Now xorg is a lot more responsive and glxgears runs on an average of 1220 fps.
(Pretty normal I guess?) 



Still the Xorg process jumps to 40-50 % cpu usage when having heavy animations (flash or javascript) in firefox. Guess it's normal...

Flickr slideshows were a nightmare, but now it's back to normal.



Thanks Ringi for your help, much appreciated!

---

