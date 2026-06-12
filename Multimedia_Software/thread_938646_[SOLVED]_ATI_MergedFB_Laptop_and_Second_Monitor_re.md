---
title: "[SOLVED] ATI MergedFB Laptop and Second Monitor res not correct"
date: 2008-10-05
forum: Multimedia Software
---

### Post by AmbiguousOutlier on 2008-10-05
Hello I've used the following thread to get my Dual monitors up and running;

[http://ubuntuforums.org/showthread.php?p=1773710](http://ubuntuforums.org/showthread.php?p=1773710)

However I can't get the resolution correct.

```

Section "Device"
	Identifier	"Configured Video Device"
	Option "MergedFB" "true" #Enable MergedFB function
	  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
	  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	  Option "CRT2VRefresh" "60-60" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	  Option "OverlayOnCRTC2" "true"
	  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
	  Option "MetaModes" "1440x900-1680x1050" #Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"Horizsync    28-64 #You may wish to change the values to fit your specific monitor
    Vertrefresh    43-60
	
EndSection

```

The first monitor (1440x900) is my laptop and the other is my LCD display. Which I want to function as the primary screen, and have an extended desktop on to the laptop.

Can anyone see what I have done wrong as the resolution on the laptop is perfect but the LCD is not.

I'm still new at this.
Thanks

---

### Post by AmbiguousOutlier on 2008-10-05
Ok a bit of googling later and I now have both monitors with the correct resolution, however the tool bars at the top and bottom of the screen are set to the smaller resolution which means on the larger screen they are not the correct width and not positioned correctly in the screen. Is there a way to make them disappear altogether off on screen.

Also the screens are cloned to a certain degree, I want to have separate images on each.

This is what I changed.

```

Section "Device"
	Identifier	"Configured Video Device"
	Option "MergedFB" "true" #Enable MergedFB function
	  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
	  Option "CRT2Hsync" "30-82" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	  Option "CRT2VRefresh" "60-60" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	  Option "OverlayOnCRTC2" "true"
	  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
	  Option "MetaModes" "1680x1050-1440x900" #Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"Horizsync    28-82 #You may wish to change the values to fit your specific monitor
    Vertrefresh    43-75
	
EndSection

```

---

