---
title: "TwinView question/problem"
date: 2005-11-27
forum: Multimedia &amp; Video
---

### Post by warped096 on 2005-11-27
I have enabled twinview using a 17 inch CRT and a 15 inch LCD. I wish to use the CRT as my main monitor with the desktop and my LCD as the auxillary with the blank screen, however, it uses the LCD as the main monitor by default, and I cant figure out how to switch to use the CRT as the main monitor. How would I go about doing this? Thanks :cool: Here is my xorg.conf file

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "TwinView"
        Option          "MetaModes"                "1024x768, 1024x768"
        Option          "SecondMonitorHorizSync"   "UseEdidFreqs"
        Option          "SecondMonitorVertRefresh" "UseEdidFreqs"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	    # 1024x768 @ 90.00 Hz (GTF) hsync: 72.81 kHz; pclk: 100.19 MHz
  Modeline "1024x768_90.00"  100.19  1024 1088 1200 1376  768 769 772 809  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

---

### Post by mo_x on 2005-11-27
You might want to take a look at the nvidia linux forum:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
Maybe you can use the ConnectedMonitor option (see the nvidia readme) but I think it is not possible with the currecnt driver.

---

