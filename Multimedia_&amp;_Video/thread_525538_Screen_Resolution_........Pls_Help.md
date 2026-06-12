---
title: "Screen Resolution ........Pls Help"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by Enspade on 2007-08-14
Hi.......
I got a Asus PV VM MOtherboard with integrated GEforce 6150.......I cannot get my kubuntu 7.04 to get resolutions greater than 800x600.........But i am able to get on Windows Xp....... I am giving here what is written in the screen section of xorg,,,,,,,,
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51PV [GeForce 6150]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


There i find it os being supported ....But iam unable to get it.....
I tried using xrandr .....I got
SZ: Pixels Physical Refresh
*0 800 x 600 ( 271mm x 203mm ) *60 56
1 640 x 480 ( 271mm x 203mm ) 60
2 400 x 300 ( 271mm x 203mm ) 60 56
3 320 x 240 ( 271mm x 203mm ) 60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

i tried xrandr -s 1024x768
but says Size 1024x768 not found in available modes


Pls help me here ............
Thanks in Advance...........

---

### Post by overdrank on 2007-08-15
HI if you have not found a solution to your problem then this thread may help
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck! :)

---

