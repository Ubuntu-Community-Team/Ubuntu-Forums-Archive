---
title: "Wrong screen resolution using vga switch"
date: 2009-04-25
forum: Multimedia Software
---

### Post by jmpmjmpm on 2009-04-25
Hi 

I'm using a vga switch that supports resolutions of 1600 x 1280 but my display keeps changing to a resolution lower than it's native 1440 x 900. I have looked in my xorg.conf file and it is sparse, 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1152 864
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

I have tried changing the above to 1440 x 900 but it goes into low graphics mode and offers to change the configuration back to default. 

How can I re-enable and then lock in the resolution of 1440 x 900? the other device which sahres the switch is an xbox360 and it runs at 1440x900 ok. But Ubuntu (and previously windows 7) keeps switching

thanks

---

### Post by Zimmer on 2009-04-25
My only suggestion is that you will need two config files and swap/rename them as and when you want to switch, and you will still need to restart the x server...

 You will need to construct the bespoke xorg.conf  files with a valid modeline for each monitor and use the option
Option "UseEdid" "False"

in the screen section to avoid auto detection and the use of failsafe xorg.conf 

see Appendix B

[http://us.download.nvidia.com/XFree8...DME/index.html](http://us.download.nvidia.com/XFree8...DME/index.html)

---

### Post by jmpmjmpm on 2009-04-27
i'm not sure it is even using the xorg.conf file as there aren't any settings in it...

---

### Post by Zimmer on 2009-04-29
Check the log to see what is happening ...

System>Administration>System Log

xorg.0.log

if you read the headings it will tell you how to interpret the symbols...

Markers:
 (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

---

### Post by jmpmjmpm on 2009-04-30
thanks Zimmer, I will check the log and post back

---

