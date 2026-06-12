---
title: "Dual monitor with dual graphics card"
date: 2009-02-13
forum: Multimedia Software
---

### Post by janwari on 2009-02-13
I have spent 2 whole days before asking for help here. I am trying to setup Dual monitor with dual graphics card on Ubuntu 7.10 (Gutsy Gibbon). I have read a lot of tutorial on the forums and majority of them are for Dual-Output Graphics card. Does this mean that Ubuntu will only work with Dual-Output graphics card? 

I have attached the output of lspci and my xorg.conf. 
As one can see from the files Ubuntu is detecting my ATI graphic card and the on board Intel one.
```

00:02.0 Display controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
04:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)

```

Additionally when I go to System->Administration->Screens and Graphics  it displays three Screen but doesnt allow me to extend anyone of those(see attached images).

I would like to know whether there is even a remote possibility of me getting dual monitor with dual graphics card to work?? If yes, then I dont mind spending more time along this route as this is my last hurdle to get off Windows. If not, then I will have to look at some other alternatives.

Any suggestion/help is welcomed.

Thanks.

---

### Post by janwari on 2009-02-13
After spending another 2 hrs having another crack at fixing this issue, I achieved some success. I was able to successfully create seperate xorg.conf files for the Intel and ATI controllers. And both the graphics card work in a single monitor setup. But when I try to configure dual monitor setup by adding multiple Device, Monitor and Screen section X windows throws the following error "(EE) Screen 1 deleted because of no matching config section." 

This is the xorg.conf file when I try to configure it to work with dual monitor. 

```


####
# Start
# Dell Monitor / Intel graphics card
#
###

Section "Device"
	Identifier	"Intel"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Screen      	0 
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "CRT,CRT"
EndSection

Section "Monitor"
	Identifier	"Dell Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Dell Screen"
	Device		"Intel"
	Monitor		"Dell Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

####
# 
# Dell Monitor / Intel graphics card
# End
###


####
# Start
# Sony Monitor / ATI graphics card
#
###

Section "Device"
	Identifier	"ATI"
	Driver		"ati"
	BusID		"PCI:4:0:0"
	Screen      	1 
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "CRT,CRT"
EndSection


Section "Monitor"
	Identifier	"Sony Monitor"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	48-120
EndSection


Section "Screen"
	Identifier	"Sony Screen"
	Device		"ATI"
	Monitor		"Sony Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

####
# 
# Sony Monitor / ATI graphics card
# End
###


Section "ServerLayout"
    Identifier    "Default Layout"
    Screen         0   "Dell Screen"
    Screen         1   "Sony Screen" RightOf "Dell Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option 	   "Xinerama" "on"
    Option         "Clone" "on"
EndSection


```

Am I missing some configuration here??

---

### Post by janwari on 2009-02-20
Ok, after spending another week trying to figure out what the heck is wrong with my xorg.conf file(*have ~50 xorg.conf test files now*) and after getting some valuable suggestions in #ubuntu and #linux on Freenode I was finally able to get Ubuntu 7.10 to work with dual monitor. 

The thing that actually did it for me was running $**X -configure** in recovery mode. This command auto created a multihead xorg.conf file. There are still some issues like I cant drag a Window between the two screen and I cannot run "Screen Resolution" or "Screens and Graphics". But the fact that Dual monitor works is itself an achievenment and I am satisfied with it for now :)

I have attached my xorg.conf that finally worked for my Dual monitor setup, incase anyone is faced with similar issue ;-)

---

