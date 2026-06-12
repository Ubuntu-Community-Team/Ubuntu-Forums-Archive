---
title: "Open GL Visual / Stereo Rendering Problem"
date: 2011-09-02
forum: Multimedia Software
---

### Post by Kat of Zion on 2011-09-02
Im running Maya 2009 on Xfce.  It runs just fine (and has for quite some time).  However of recent, I get the following error when Maya tries to test render prims with an image mapped onto it.  

**Warning: Unable to get OpenGL visual with a stereo buffer, trying without //.**

I know this could be a Maya issue but the following link suggests it could have to do with Xorg.conf's setup:

[http://baltazaar.wordpress.com/2009/03/30/stereo-rendering-with-maya-on-linux-opengl/](http://baltazaar.wordpress.com/2009/03/30/stereo-rendering-with-maya-on-linux-opengl/)

I did try the method described here and it caused issue with Xorg so I couldnt start up my computer again. I have since revereted my xorg back to the way it was, with no other solution in sight.  Running GLX gears does not show any issues with GLX itself so I know it must be some new thing I need to put into Xorg.

Solutions?

---

### Post by Kat of Zion on 2011-09-15
Here is my current Xorg file:


```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "AllowDFPStereo" "true"
	Option "Stereo" "3"
EndSection
```

I thought the 	Option "AllowDFPStereo" "true" would be the ticket but Maya still claims it cant use the stereo buffer

---

