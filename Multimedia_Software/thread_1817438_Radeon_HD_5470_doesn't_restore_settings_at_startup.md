---
title: "Radeon HD 5470 doesn't restore settings at startup - I'M GOING CRAZY!"
date: 2011-08-03
forum: Multimedia Software
---

### Post by dawbomb on 2011-08-03
Hi,

I've got an Acer Aspire 5741G laptop, which has an ATI Mobility Radeon HD 5470 graphics card.  The laptop has a 15.6" LCD, and I have a Dell 24" LCD connected through HDMI.

I've set up split screens, and it works perfectly.  If I shutdown and restart, the settings stay.

If I unplug the HDMI cable, when I start up my laptop I then need to struggle to reconfigure graphics settings, as the screen setup is all over the place-  I seem to have two screens squashed into one.

Once I've sorted out my graphics settings, used my computer, and get home again, once I have started up my computer again I am back to the same image on both monitors, and have to open up Catalyst CC, change settings all over again, restart, all to get my split screen back again.  Until I go into university the following day.

Is anyone aware of any fixes?  Perhaps a script to force CCC to check if there is an external screen connected and load the correct settings?  Unfortunately, when I boot Windows 7 it "just works".  I can plug and unplug screens all I like WHILE THE COMPUTER IS ON, and it works fine.  I've been using Ubuntu for about 4 years now, but this is really irritating me!

Thanks in advance for any help received!

xorg.conf:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1366x768"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "50"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1920x1080"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3286 1920
		Depth     24
	EndSubSection
EndSection

```

---

### Post by ~!geek!~ on 2011-08-03
You may give it a try:

After all the desired settings done, you may try this command:

> aticonfig

Running this command will suggest you steps you need to follow. You may be prompted to run other command too, if its first time u r using this command. I don't remember  the exact name, but follow whatever it asks.

---

