---
title: "Help with Dell Monitor"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by linuxunil on 2006-06-14
I have a dell E173FP that when I set the resolution at 1280x1024 and the refresh rate at 75 there are lines through the screen. I have tried a few things but none work.  The monitor works fine at 1024x768 @ 75.  Please help.

Here is the xorg.conf

```
Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by deadgobby on 2006-06-14
[QUOTE=linuxunil]I have a dell E173FP that when I set the resolution at 1280x1024 and the refresh rate at 75 there are lines through the screen. I have tried a few things but none work.  The monitor works fine at 1024x768 @ 75.  Please help.[/QUOTE]
 Did you run the dell monitor at that res 1280x1024 if you ran breezy version? What vid care do you have? If it is on on board vid, it may be that it cannot not handle that type of res or the monitor cannot. I have a dell montor and just let xorg default to the settings for that monitor. 
Gobby

---

### Post by linuxunil on 2006-06-14
I have run it at 1280x1024 on windows and on openSuSE, it has integraged intel graphics. The computer is a Dell Optiplex GX150.

---

### Post by vigleik on 2006-06-15
[QUOTE=linuxunil]I have run it at 1280x1024 on windows and on openSuSE, it has integraged intel graphics. The computer is a Dell Optiplex GX150.[/QUOTE]

Ubuntu has trouble autoconfiguring these Dell flatpanels. Dapper can't get my E172FP right either. One possible fix is to boot from another distro's live CD (I've had good luck with simplymepis, maybe try their latest beta) or install another distro which can handle your monitor and just copy over the xorg.conf file.

I solved my problem a different way. Because I have a nvidia graphics card instead of integrated graphics, I installed the nvidia driver (easyubuntu) and then did "dpkg-reconfigure xserver-xorg", making sure to choose the nvidia driver and the correct resolution.

You could try "dpkg-reconfigure xserver-xorg" and experiment with different drivers, if you don't feel like trying another distro.

Vigleik

---

