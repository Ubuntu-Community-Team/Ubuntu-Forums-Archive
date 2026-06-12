---
title: "Need help problem with screen please"
date: 2008-12-13
forum: Multimedia Software
---

### Post by -Root- on 2008-12-13
I need help i am a newib on Ubuntu i been on for 6 hours trying to fix one error resizing the screen now i read [http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution) this already but i tryed everything like 40 times and noting worked here is my xorg file right now can someone tell me what to add my screen can go upto to 1200/1000 or 1600/1400 at 50-60 Hz :) i got nivdia Geforce 5500 FX 256 MB ram

Here is the file right now

Section "Screen"
	Identifier	"Configured Screen Device"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

---

### Post by eternalnewbee on 2008-12-13
Did you try to enable your graphic card?
To check, go to: **Main Menu > System > Administration > Hardware Drivers**.
Did you try to adjust screen resolution from: **Main Menu > System > Preferences > Screen Resolution**?

---

### Post by -Root- on 2008-12-13
Yes i did both the video card is activated and the resolution thing only shows to 680/480

---

### Post by overdrank on 2008-12-13
> **-Root- said:**
> Yes i did both the video card is activated and the resolution thing only shows to 680/480

Hi have you tried using the nvidia-settings to adjust ```
gksu nvidia-settings
```
What version of ubuntu?

---

### Post by -Root- on 2008-12-14
Yes i already tryed the video card setting noting there not to mention the setting keeps fliping and going away from me. It shows only the 680/480 again noting i can do. :(

---

### Post by -Root- on 2008-12-15
anyone please?

---

