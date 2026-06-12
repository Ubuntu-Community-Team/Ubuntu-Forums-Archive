---
title: "nVidia AND ATI together"
date: 2008-06-19
forum: Multimedia Software
---

### Post by billomer on 2008-06-19
I have a dual head nvidia agp card, and a dual head ati pci card.  I'm trying to get them working together, but not having much luck.

I wrote my own xorg.conf file and got dual head from the nvidia cards, but I can not get a single head (or both) from the ati card to work.

Here's an lspci output:

```
01:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)
04:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
04:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
```


And here is the relevant stuff from my xorg.conf:

```
Section "ServerLayout"

    Identifier     "Default Layout"
	Screen	0	"Main Screen"
	Screen	1	"Second Screen" RightOf "Main Screen"
	Screen	2	"Third Screen" LeftOf "Second Screen"
	Screen	3	"Fourth Screen" LeftOf "Third Screen"
	Option	"Xinerama"	"true"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor2"
	Option	"DPMS"
EndSection

Section "Monitor"
        Identifier      "Monitor3"
        Option  "DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor4"
	Option	"DPMS"
EndSection



Section "Device"
    Identifier     "nvidia0"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Screen	0
EndSection

Section "Device"
	Identifier	"nvidia1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen	1
EndSection

Section "Device"
	Identifier	"ati0"
	Driver		"ati"
	BusID		"PCI:4:0:0"
	Screen	2
EndSection

Section "Device"
	Identifier	"ati1"
	Driver		"ati"
	BusID		"PCI:4:0:0"
	Screen	3
EndSection

Section "Screen"
    Identifier     "Main Screen"
    Device         "nvidia0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Second Screen"
    Device         "nvidia1"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Third Screen"
    Device         "ati0"
    Monitor        "Monitor3"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
   Identifier	"Fourth Screen"
   Device	"ati1"
   Monitor	"Monitor4"
   DefaultDepth	24
   SubSection	"Display"
	Depth	24
	Modes	"1280x1024"
   EndSubSection
EndSection
```




X does start but I see this in my Xorg.0.log:

```

(WW) RADEON: No matching Device section for instance (BusID PCI:4:0:0) found
(WW) RADEON: No matching Device section for instance (BusID PCI:4:0:1) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found

<SNIP>

(EE) Screen 2 deleted because of no matching config section.
(II) UnloadModule: "radeon"
(EE) Screen 2 deleted because of no matching config section.
(II) UnloadModule: "radeon"

```




I have searched online but haven't found any help with this kind of setup.  I find it hard to believe I'm the first person trying to mix nvidia and ati cards together. 

Does anyone have any idea what I could be missing?

---

### Post by billomer on 2008-06-20
Am I really the only one not sane enough to attempt using an nVidia AGP and ATI PCI card?

---

### Post by NateMan on 2008-06-20
yes

---

### Post by sim-value on 2008-06-20
> **billomer said:**
> Am I really the only one not sane enough to attempt using an nVidia AGP and ATI PCI card?

Way to much freenes in your brain ...

---

### Post by Tarmael on 2008-06-27
This is madness!! How can you get them to work together when they've been at each others throats for years!!!

You're proding a bee's nest here...

On a serious note: I don't think you can get your desired effect with this setup...


Just... Because.

Bas.

---

### Post by fastae on 2008-09-18
Just same problem here...

You can make it work by fixing XORG on your own, setting either one of as its own driver and another one as just regular VGA or something else which fits the best.  But I still have all kinds of issue...

Thinking of getting new one...

---

