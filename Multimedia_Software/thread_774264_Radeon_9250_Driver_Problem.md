---
title: "Radeon 9250 Driver Problem"
date: 2008-04-29
forum: Multimedia Software
---

### Post by zivziv on 2008-04-29
HI 

I've Installed Ubuntu 8.04 on my pc.
I have some problems with the video card.
The computer is connected to 32' LCD TV (Metz). when I've tried to install Ubuntu I could only use the VGA connector and not the DVI (Because from some reason the screen become black and doesn't response).

After the installation I still can't use the DVI connector - When booting in DVI mode , everything is good until the stage of the username / password  , then the screen become black and nothing happens.

I've installed Envy but when I try to run it I get the following message:
"Your  graphic card has been detected as ATI Mobility / Radeon 9200
Your graphic card is supported by te legacy Driver 
EnvyNG ERROR : ATI's legacy driver does not support your operating system"

I've also tried to download and install the drivers directly from ATI/AMD site.
However I get slimier error.

I've also tried to reinstall fglrx-control , xorg-driver-fglrx.
When I try to run "ATI Catalyst COntrol Center" I get an error that no ATI graphic installer was installed .

I don't know what to do any more - Plz Help .
I can't use the VGA connector  I need to use my DVI and my graphic card as I should and did in 6.06 ver.


Here is my vga lspci output (I have radeon 9250 - AGP):

 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)

Here is the xorg.conf:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,il"
        Option          "XkbVariant"    ","
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


Thanks In Advance

---

