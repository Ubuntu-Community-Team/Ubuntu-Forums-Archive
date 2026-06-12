---
title: "XRANDR Dual Head, single desktop on RADEON 9600"
date: 2009-03-08
forum: Multimedia Software
---

### Post by markofealing on 2009-03-08
I'm running Ubuntu 8.10 with a ATI Radeon 9600 in a dual head configuration as follows:

Hitachi 17MVXPro2 CRT (would like to run 1024x768@75Hz) on the left on VGA-0
HP F70 TFT (Would like to run 1280x1024) on the right on DVI-0

Using XRANDR 1.2 I can configure my desired desktop (XRANDR is absolutely brilliant) for example setting my HP F70 is just **xrandr --output DVI-0 --mode 1280x1024**from terminal! However, on reboot the settings revert back to the detected defaults which are wrong. Therefore, I need to put the settings in xorg.conf.

Below is my xorg.conf, supposedly modified to configure my displays automatically on the start of X. However, all that works is setting the definition of 1024x768_75.00 for VGA-0.

[I]Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	BoardName   "RV350 AQ [Radeon 9600]"
	BusID       "PCI:1:0:0"
	Option	"Monitor-VGA-0" "Hitachi"
	Option	"Monitor-DVI-0" "HP F70"
EndSection

Section "Monitor"
    Identifier      "Hitachi"
    Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
    Option "PreferredMode" "1024x768_75.00"
    Option "LeftOf" "HP F70"
EndSection

Section "Monitor"
    Identifier      "HP F70"
    Option "PreferredMode" "1280x1024"
EndSection

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Card0"
	Monitor "Hitachi"
	DefaultDepth 24
	SubSection "Display"
		Modes "1280x1024" "1024x768"
		Virtual	2304 1024
	EndSubSection
EndSection[/I]

When I enter XRANDR -q, this is what I get, the text in red is what setting should be if the xorg.conf file was to work properly.

[I]Screen 0: minimum 320 x 200, current 2048 x 768, maximum 2304 x 1024
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
[COLOR="Red"]   1024x768_75.00   75.0 +[/COLOR]
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0*    59.9  
   800x600        60.3  
   640x480        59.9  
DVI-0 connected 1024x768+1024+0 (normal left inverted right x axis y axis) 359mm x 287mm
[COLOR="Red"]   1280x1024      60.0 +   60.0     60.0 [/COLOR] 
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  [/I]

I've spend two days looking at various sample xorg.conf files and web pages and still can't see where I'm going wrong.:(

Thanks in advance for your help

---

### Post by cubeist on 2009-03-08
I think the easiest way would be to use the ati proprietary driver, then use the ati catalyst control center (which will be in your accessories menu after instaling).

This program will allow you to graphically position the two screens just as you want...and have one big desktop spread across two screens

---

### Post by markofealing on 2009-05-20
Found a solution.

Once you have set your resolution, go into Preferences > Screen Resolution and select the desired resolution for your screens from there. The settings get saved and are restored after a reboot.

Resolved!

---

