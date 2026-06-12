---
title: "Lines in Video especially when Panning"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Jaffarkelshac on 2008-05-03
I have been having this issue a while, and I have not been able to describe it adequate enough so, I filmed a video with my camera and below are the screencaptures from it. The lines appear in all my videos, by vlc, flash, mplayer so its not app related I think. Makes watching action film with fast camera movement on a big screen rather distracting. I hope this helps get me a fix. 

[http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot-2.png](http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot-2.png)

[http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot-3.png](http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot-3.png)

[http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot-5.png](http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot-5.png)

[http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot.png](http://i217.photobucket.com/albums/cc24/jaffarkelshac/Screenshot.png)

My system
Hardy Heron (8.04 LTS) with  2.6.24-17-generic (gnome)
nvidia 7300gt card, using compiz 
screen is 1024x768 50hz

---

### Post by |{urse on 2008-05-03
if you disable desktop effects does the problem persist?

---

### Post by |{urse on 2008-05-03
if so try finding the correct refresh rates for your monitor on the web or the manufacturers site and adjusting your xorg.conf as necessary.

sudo gedit /etc/X11/xorg.conf

look for the monitor section, the appropriate section should look like this

```
Section "Monitor"
    Identifier    "CM752ET"
    HorizSync     31-101
    VertRefresh    60-160
EndSection
``` 

this is just an example, your mileage may vary.

---

### Post by Jaffarkelshac on 2008-05-03
I did not expect a response this quick, yeah, disabling the desktop effects fixes the problem.

---

### Post by |{urse on 2008-05-03
Yeah thats a very common proble. the solution lies in correctly configuring x. if you could post your xorg.conf i might be able to help so you dont have to disable desktop effects every time you want to watch a movie ^^

---

### Post by Jaffarkelshac on 2008-05-03
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:6:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:6:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

My Xorg.conf

---

### Post by |{urse on 2008-05-03
sorry should have asked before but what is your monitors make and model>?

---

### Post by Jaffarkelshac on 2008-05-03
its a tv/monitor best comparison is this [http://www.tribaluk.com/alba-alcd15dvd1pnk-lcd-television-01028024.htm](http://www.tribaluk.com/alba-alcd15dvd1pnk-lcd-television-01028024.htm) except i have the alcd2 and this is the 2, only cosmetic difference.

---

### Post by |{urse on 2008-05-06
sorry its taken so long. try this.

> gstreamer-properties

select the video tab and change video to XWindow system (no XV)

---

### Post by Jaffarkelshac on 2008-05-06
Unfortunately there is no change.

---

### Post by terry_gardener on 2009-02-22
i have also had this problem when the desktop effects where on, videos had lines/tearing effect when panning. 

when i disabled desktop effects it works ok. just like yourself. 

i have found that if you tick sync to vblank in compizsetting-manager--general options--display settings. it works ok again or it did for me.

---

