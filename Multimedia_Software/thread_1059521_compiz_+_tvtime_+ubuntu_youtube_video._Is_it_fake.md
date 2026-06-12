---
title: "compiz + tvtime +ubuntu youtube video. Is it fake?"
date: 2009-02-03
forum: Multimedia Software
---

### Post by Blackie_Chan on 2009-02-03
I have been trying to get compiz + tvtime working on my ubuntu 8.10 box for a long time, and still no luck. 

Today, I found this video: [http://www.youtube.com/watch?v=8wGg0ZyIs8M](http://www.youtube.com/watch?v=8wGg0ZyIs8M) Is the video fake? I've spent a lot of time googling and no one else has been able to get it to work together. 

I've also email the video poster, asking how he did it, and haven't gotten a response. 

Here's my current xorg.conf:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Configured Mouse"
	InputDevice    "Remote"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Remote"
	Driver      "mouse"
	Option	    "Device" "/dev/lircm"
	Option	    "Protocol" "IntelliMouse"
	Option	    "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Radeon 9600"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "TexturedVideo" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "off"
	Option	    "TexturedXrender" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon 9600"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by cariboo on 2009-02-03
I didn't bother with the video, but tvtime has nothing to do with compiz, you just have to have the proper video driver installed. check the screenshots.

I do have compiz turned on but I only have floppy windows and transparent terminals setup.

Jim

---

### Post by Blackie_Chan on 2009-02-04
> **cariboo907 said:**
> I didn't bother with the video, but tvtime has nothing to do with compiz, you just have to have the proper video driver installed. check the screenshots.

I do have compiz turned on but I only have floppy windows and transparent terminals setup.

Jim

What video driver do you have installed? I'm guessing you are not using an ATI card.

---

