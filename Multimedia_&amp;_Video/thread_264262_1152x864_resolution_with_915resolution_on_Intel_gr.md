---
title: "1152x864 resolution with 915resolution on Intel graphics"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by popcorn09 on 2006-09-24
Hi,

I want to increase my screen resolution to 1152x864. I installed the 915 resolution package but it doesn't have this resolution. It has 1024x768 or 1280x1024. 

Can anyone please help with this?

Thanks.

---

### Post by tosun pasa on 2006-09-24
I had a same problem 1440x900 resolution in widescreen.I solve problem by changing xorg.conf file.[Here]("https://wiki.caosity.org/tiki-index.php?page=X+Server+Configuration&bl") you can find this solution under 'Getting the Right Mode for an LCD monitor'.
i hope it works.

---

### Post by danburney999 on 2006-10-28
Hey. I'm a relative newbie and have tried loads to get my packard bell easynote R4650 LAPTOP to output on my 19" widescreen monitor at 1440x900 to no avail. I know that it is possible as it works under windows.

The best that i have got is improving the options of screen resolution. i have installed 915resolution and messed about with my xorg.conf but just seem to be missing something.

Also, i dont know if this is related, but everytime i restart the monitor and laptop screen both output the same, but with the monitor chopping about an inch off the bottom. This is fixed by using the laptop keyboard to tab through form 'laptop' to 'dual' to just the monitor.

here is my messed up xorg.conf

```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
Option "ForceBIOS" "1920x1440=1440x900"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Subsection "Display"
        	Depth     24
        	Modes     "1440x900"
    	EndSubsection
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

and here is the backed up, pre-messed with:
```

ection "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

---

### Post by teknorah on 2007-04-08
Are you wanting to use both the laptop and external monitor at the same time?

---

