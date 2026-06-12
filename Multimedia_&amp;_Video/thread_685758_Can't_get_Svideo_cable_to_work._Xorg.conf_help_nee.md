---
title: "Can't get Svideo cable to work. Xorg.conf help needed."
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by Siph0n on 2008-02-02
Hi. I have a GeForce 5900XT video card and a 42inch LG plasma TV. I just bought a s-video cable and wanted to watch movies from my computer on my TV... I followed the 2 X Screens instructions at [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) , but still can't get it to work.

Here are the relevant parts to my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0	   "Screen0"
    Screen 1	   "Screen1" rightof "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Monitor"
    Identifier     "Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier	   "Television"
    HorizSync	    30-50
    VertRefresh	    60
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Screen	    0
    BusID	    "PCI:02:09:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    Screen	    1
    BusID	    "PCI:02:09:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor"
    DefaultDepth    24
    Option	   "ConnectedMonitor" "CRT"
    SubSection	   "Display"
        Depth	    24
	Modes	   "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier	   "Screen1"
    Device	   "Device1"
    Monitor	   "Television"
    DefaultDepth    24
    Option	   "TVOutFormat" "SVIDEO"
    Option	   "TVStandard" "NTSC-M"
    Option	   "ConnectedMonitor" "TV"
    SubSection	   "Display"
        Depth	    24
        Modes	   "1280x1024"
    EndSubSection
EndSection

```

I got the BusID from lspci
```
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

I saw this in the /var/log/Xorg.0.log file after rebooting
```
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb  2 14:19:51 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
```

Also when I reboot my resolution goes really low and it says my nvidia driver isn't being used... Any help would be appreciated. Thanks.

---

### Post by gsmanners on 2008-02-02
I think that video card probably doesn't support 1280x1024 to the TV. Try using something smaller like 1024x768.

---

### Post by Siph0n on 2008-02-02
I tried the 1024x768 resolution and I still get the error:

"Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself."

Still, would the resolution of my TV I have set in xorg.conf make my LCD monitor a lower resolution? Also, once I do get it working is there a way to make the Svideo cable work and than not work? so I don't have the image on the TV the whole time my computer is up. Thanks in advance.

---

### Post by perixx on 2008-02-02
Hi!

I don't know if this also applies to Nvidia cards, but ATI's currently don't support video-playback on the second screen. 
I've already seen some such issue while displaying the desktop both on a notebook's panel & on TV via S-video; the desktop was shown on TV, but the windowed film remained black. 

Does your TV have a real S-Video input or a S-Video conforming Scart connector? Because if it's got no 2 Scart-connectors, it very likely to only supporting 'RGB' input. In this case, using a cheap 'S-video to Scart' adapter, will result in having a b/w picture, because only the luminance signal ('brightness') is being used. 

To circumvent that, you'd have to bridge the luminance and chrominance (color) signal pins inside the connector with a 470pF condenser, to 'add' color signal to the chrominance signal, thus gaining a slightly quality-reduced 'FBAS' signal, which the TV can process. This only applies, if you're in the 'PAL' area, of course :) See also this info: [http://en.wikipedia.org/wiki/S-Video]("http://en.wikipedia.org/wiki/S-Video")

Do you want to just want to display your desktop or playback videos on your TV? 
You should run '**nvidia-settings**' (sudo in front, to save settings to /etc/X11/xorg.conf), there you should be able to set up your dual-screen configuration to your needs. Btw., depending on where you live, your TV's 'resolution' should be sth. like e.g.:
> PAL Square-Pixel	768 x 576	944 x 625	4:3 = 1:075
PAL CCIR-601	720 x 576	864 x 625	5:4 = 1:0,8

ADD: Forgot to mention - perhaps there's a wrong screen refresh rate set for the TV (should be 60Hz at NTSC and 50Hz at PAL devices)... 

perixx

---

### Post by gsmanners on 2008-02-03
That looks like a tricky problem. Sorry I can't help more, but I normally use:

nvidia-xconfig --twinview --twinview-orientation clone

I suppose what you want is something along the lines of:

nvidia-xconfig --twinview --twinview-orientation RightOf

---

### Post by Siph0n on 2008-02-05
What is the difference between Twin View and 2 Screens? Also, what is it called when you have two monitors (or one monitor and a tv), and can drag a window from one to the other? 

Also the xorg.conf I posted above has this:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0	   "Screen0"
    Screen 1	   "Screen1" rightof "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection
```

Can someone explain to me why there is a space between "Screen" and "0", and also "Screen1" and "1"? The identifiers dont have a space.... Also, does "Screen1" rightof "Screen0" mean that if i move my window on my monitor to the far right it will go over into my tv? Thanks for all the help!!! :)

---

### Post by gsmanners on 2008-02-05
I'm not really aware of what the difference is between TwinView and what you've been trying to do.

That's just the syntax for the ServerLayout section of xorg.conf.

Screen  screen-num "screen-id" position-information

I'm not sure how position works. I seem to recall that you can move the mouse from one screen to the other. The other screen should also have its own desktop, as well.

---

### Post by Siph0n on 2008-02-06
I tried using [http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT) . The tutorial said that this would make one screen (LCD or TV) on at a time. When I hit Ctrl Alt F8 ubuntu closes x windows and says Running Local Scripts, along with some other thing like checking the battery.... However, my tv doesn't show my computer desktop like it said it would. When I hit Ctrl Alt F7 xwindows starts again. Any ideas??? My tv still says No Signal. I know that the ports and svideo cable works because i plugged my dvd player in through Svideo, and my windows laptop and they both work. 

1) I was thinking it could be the resolution?

2) I have seen some places where 
Option		"ConnectedMonitor" "TV"
is sometimes
Option		"ConnectedMonitor" "CRT,TV"
Should I have that in my Device section for my TV?


3) Or perhaps its the Horizontal or Vertical refresh rates for my tv?

4) Am I missing anything from my monitor Screen, Device, or Monitor?

5) Should I have two ServerLayouts?

Thanks if anyone can help! :)

xorg.conf:
```
Section "Device"
	Identifier	"nVidia Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"Card_tv"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TVOutFormat" "SVIDEO"
	Option		"TVStandard" "NTSC-M"
	Option		"ConnectedMonitor" "TV"
EndSection

Section "Monitor"
	Identifier	"tv"
	Horizsync	30-50
	Vertrefresh	60
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"Screen_tv"
	Device		"Card_tv"
	Monitor		"tv"
	Defaultdepth	24
	Subsection	"Display"
		Depth	24
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"tv"
	Screen		0 "Screen_tv" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
```

---

### Post by theacoustician on 2008-02-06
Two points to note

1. S-video can't handle higher than NTSC resolution (640x480).  The problem may simply be that you have the resolution set too high.

2. If you have a computer and a new plasma, why not hook it up via VGA or DVI?  It'll look a helva lot better than the s-video could ever hope to give you.

---

### Post by Siph0n on 2008-02-07
Thanks everyone for the help! One of the main problems was that my S-video cable was plugged into my TV Tuner instead of my graphics card. My graphics card, a 5900XT, I thought had an Svideo out port, but it is not... I tried to use a VGA cable with my laptop, and it worked with just an Fn and F4 keystroke... super simple... It also looks like better quality than the svideo cable from my windows laptop! Thanks for that suggestion!!! Anyone with an MSI GeForce 5900XT graphics card know what ports are on it? I know DVI and VGA, but the one inbetween has too many pin holes to be an Svideo port.... Thanks :)

---

### Post by perixx on 2008-02-08
I suppose you mean the 'Mini-DIN' or 'Hosiden' connector - there's info on wikipedia (and also computerbase, I guess) about it...

perixx

---

