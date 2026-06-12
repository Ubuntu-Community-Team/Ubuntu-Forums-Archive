---
title: "Radeon 7000 VE  driver on Dapper"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by _axiom_ on 2007-01-03
I am getting confused by the things I read about this.

I understand that what I need to get better performance I need to enable “Direct Rendering”, which is curently not working.

```
axiom@axiom:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

I tried to follow the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=221672"), which seemed promising, but I really haven't gotten anywhere with it.

I did get dri snapshot installed and compile with my kernal headers with that nifty script.

And then I edit my xorg.conf

```
Section "Device"
  identifier "ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
  boardname "ATI Radeon (fglrx)"
  busid "PCI:1:0:0"
  driver "radeon"
  screen 0
  vendorname "ATI"
	option "MergedFB" "off"
	option		"AGPMode" "4"
	option		"AGPFastWrite" "true"
	option	        "EnablePageFlip" "True"
	option	        "UseInternalAGPGART" "no"
	option	        "backingstore" "true"
	option	        "AllowGLXWithComposite" "true"
	option          "RenderAccel" "true"
EndSection
```
(The problem could be in there, the first time I just copied what he showed, and X wouldn't come up at all.)

After restarting,  I ran driconf, but it didn't have any of the options that he talked about.  I don't think it could find any devices. I tried adding one, but even then the only thing I could change was it's name, and there was nothing about TCL mode or HyperZ.

What am I missing here?

---

