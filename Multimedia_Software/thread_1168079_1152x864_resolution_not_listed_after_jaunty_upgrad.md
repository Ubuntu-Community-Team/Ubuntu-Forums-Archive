---
title: "1152x864 resolution not listed after jaunty upgrade"
date: 2009-05-23
forum: Multimedia Software
---

### Post by josephdaniel on 2009-05-23
Hearing all the news about how fast jaunty is, I finally decided to upgrade from Intrepid.

My update went smooth except for one thing. My preferred resolution of 1152x864 is no longer listed in System > Preferences > Display

I tried resetting xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

but it didn't fix the problem. So I tried altering the xorg.conf as follows:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    8
    SubSection "Display"
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

but still I don't get the 1152x864 option in display settings.

My xrandr output is:
```
   1280x1024      60.0 +
   1024x768       85.0*+   85.0*    75.0     70.1     60.0  
   800x600        85.1     75.0     60.3  
   640x480        85.0     75.0     66.7     59.9  
   720x400        70.1
```

I was using the resolution 1152x864 @ 75Hz in intrepid before the upgrade. How can I get it back?

Any help is appreciated,
Thanks,
Joseph

---

### Post by josephdaniel on 2009-05-23
Problem Solved :)

I used the instructions in this page,
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

I applied the following changes to xorg.conf and now I am successfully working on 1152x864 once more.
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
	Option 		"PreferredMode"		"1152x864_75.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"intel"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
EndSection
```

---

