---
title: "setting up primary display, HOW??"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by joraco on 2006-08-14
Hi, first of all thankyou everyone for reading this

Well, I've succesfully configured the dual-head of my video card (NV6800XT) but now I've an issue that I can't resolve, I want to set up one monitor as a primary, but I don't know how can I do.
My current screen configuration is an Acer AL732 (17") and a TV Samsung LE26 (26") now the primary screen is the Samsung, I tried a lot of possibilites in the xorg.conf but is useless, I can't establish the Samsung as the primary screen, this is my xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Derecha" 0 0
    Screen      1  "Izquierda" LeftOf "Derecha"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "MonitorS"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
    ModeLine "1360x768" 85.800 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
EndSection

Section "Monitor"
	Identifier	"MonitorA"
	HorizSync	30.0 - 80.0
	VertRefresh	56.0 - 75.0
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "nvidia"
    Option      "RenderAccel" "true"
    BusID       "PCI:1:0:0"
    Screen       0
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "nvidia"
    Option      "RenderAccel" "true"
    BusID       "PCI:1:0:0"
    Screen       1
EndSection

Section "Screen"
    Identifier     "Derecha"
    Device         "Device0"
    Monitor        "MonitorS"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
	Identifier	"Izquierda"
	Device		"Device1"
	Monitor		"MonitorA"
	DefaultDepth	24
        SubSection     "Display"
        	Depth       24
	        Modes      "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

MonitorS is the samgung and MonitorA is the Acer

Well, thanks for all

---

### Post by Ziox on 2006-08-14
> **joraco said:**
> Hi, first of all thankyou everyone for reading this

Well, I've succesfully configured the dual-head of my video card (NV6800XT) but now I've an issue that I can't resolve, I want to set up one monitor as a primary, but I don't know how can I do.
My current screen configuration is an Acer AL732 (17") and a TV Samsung LE26 (26") now the primary screen is the Samsung, I tried a lot of possibilites in the xorg.conf but is useless, I can't establish the Samsung as the primary screen, this is my xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Derecha" 0 0
    Screen      1  "Izquierda" LeftOf "Derecha"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "MonitorS"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
    ModeLine "1360x768" 85.800 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
EndSection

Section "Monitor"
	Identifier	"MonitorA"
	HorizSync	30.0 - 80.0
	VertRefresh	56.0 - 75.0
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "nvidia"
    Option      "RenderAccel" "true"
    BusID       "PCI:1:0:0"
    Screen       0
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "nvidia"
    Option      "RenderAccel" "true"
    BusID       "PCI:1:0:0"
    Screen       1
EndSection

Section "Screen"
    Identifier     "Derecha"
    Device         "Device0"
    Monitor        "MonitorS"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
	Identifier	"Izquierda"
	Device		"Device1"
	Monitor		"MonitorA"
	DefaultDepth	24
        SubSection     "Display"
        	Depth       24
	        Modes      "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

MonitorS is the samgung and MonitorA is the Acer

Well, thanks for all

Try flipping "Screen 1" and "Screen 0" in your Device Section.




And then change these lines:

```
Screen      0  "Derecha" 0 0
    Screen      1  "Izquierda" LeftOf "Derecha"
```

to 

```
Screen      0  "Izquierda" 0 0
    Screen      1  "Derecha" RightOf "Izquierda"
```

then Reboot.

hopefully this helps.

---

### Post by joraco on 2006-08-14
This is the first that I do, but is useless, al is desconfigurated, but, I FOUND THE SOLUTION!!!:D :D 

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Izquierda" 0 0
    Screen      1  "Derecha" RightOf "Izquierda"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "MonitorS"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
    ModeLine "1360x768" 85.800 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
EndSection

Section "Monitor"
	Identifier	"MonitorA"
	HorizSync	30.0 - 80.0
	VertRefresh	56.0 - 75.0
EndSection

Section "Device"
#EL ACER
    Identifier  "Device0"
    Driver      "nvidia"
    Option      "RenderAccel" "true"
    BusID       "PCI:1:0:0"
    Screen       0
#here is the trick!!
    Option "UseDisplayDevice" "DFP"
EndSection

Section "Device"
#LA TELE
    Identifier  "Device1"
    Driver      "nvidia"
    Option      "RenderAccel" "true"
    BusID       "PCI:1:0:0"
    Screen       1
#here is the trick!!   
 Option "UseDisplayDevice" "CRT"
EndSection

Section "Screen"
	Identifier	"Izquierda"
	Device		"Device0"
	Monitor		"MonitorA"
	DefaultDepth	24
        SubSection     "Display"
        	Depth       24
		Modes      "1280x1024" "1024x768" "800x600" "640x480"       
	EndSubSection
EndSection


Section "Screen"
    Identifier     "Derecha"
    Device         "Device1"
    Monitor        "MonitorS"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



```

thnks for all

---

### Post by daou on 2006-08-16
Where did you find the solution, if I may ask?

---

### Post by joraco on 2006-08-17
In the nvidia forums, sorry I don't have the exactly post

---

### Post by daou on 2006-08-17
Ok. I was just thinking because I had the same problem and figured out a way to solve it. I then posted a solution on the nvidia forums. And if there was nothing on the Ubuntu forums about it, perhaps I could make a howto about the topic here.

Was it [this post]("http://www.nvnews.net/vbulletin/showpost.php?p=931167&postcount=100") that solved it for you?

---

### Post by joraco on 2006-08-17
No, it isn't

---

### Post by tomriddle on 2007-10-09
Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "MonitorS"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
    ModeLine "1360x768" 85.800 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
EndSection

---

