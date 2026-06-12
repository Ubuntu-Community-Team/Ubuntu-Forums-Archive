---
title: "nVidia dual monitor setup"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by MrSam on 2006-06-14
Let me first say thanks to everyone who responded to my questions the past couple of days. I finally got both monitors up and happy. I got the GLX kernel patch and drivers off one of the repos and some info from nVidia's knowledge base about commands and syntax for the video section of xorg.conf. I thought I'd post my final working xorg.conf here in case it might save anybody two days wroth of time getting things going.

xorg.conf (only the video section)
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	BusID		"PCI:4:0:0"
EndSection

# Dell 2001FP
Section "Monitor"	
	Identifier	"CRT"
#	Option		"DPMS"
	Option		"HorizSync"	"31-80"
	Option		"VertRefresh"	"60-60"
EndSection

# Scepter NagaIII
Section	"Monitor"	
	Identifier	"DFP"
#	Option		"DPMS"
	Option		"HorizSync"	"24-91"
	Option		"VertRefresh"	"60-60"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"CRT"
	Option		"Twinview" "True"
	Option		"TwinviewOrientation" "DFP RightOf CRT"
	Option		"SecondMonitorHorizSync"    "24-91"
	Option		"SecondMonitorVertRefresh"  "60-60"
	Option		"MetaModes"		    "1600x1200,1680x1050"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x720" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x720" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x720" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x720" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x720" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1280x720" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

```

Here are the URLs for the nVidia knoledge base:
Configuring Twinview
[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=175&p_created=1101836633&p_sid=U4AYg_9i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPTImcF9jYXRzPTU4JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU4OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD10d2ludmlldw**&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=175&p_created=1101836633&p_sid=U4AYg_9i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPTImcF9jYXRzPTU4JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU4OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD10d2ludmlldw**&p_li=&p_topview=1)

X configuration options

[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=174&p_created=1101836147&p_sid=U4AYg_9i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPTImcF9jYXRzPTU4JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU4OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD10d2ludmlldw**&p_li=&p_topview=1](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=174&p_created=1101836147&p_sid=U4AYg_9i&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPTImcF9jYXRzPTU4JnBfcHY9MS4yOzIudTAmcF9jdj0xLjU4OzIudTAmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD10d2ludmlldw**&p_li=&p_topview=1)


Hope this helps someone. It's a bear to get setup when you are just starting out but it's sure nice when you get things working.

---

### Post by kamil212 on 2006-06-15
Looks great and simple,
I'll try it once I get home
I had too much problems with installation (refresh rate and RAID problems) and I didn't even try to set this up until now.
Thanks a lot.

---

