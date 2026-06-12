---
title: "Help me get Dell 2005FPW+Intel i810 working!"
date: 2006-03-15
forum: Multimedia &amp; Video
---

### Post by fumidus on 2006-03-15
One of my computers at work is giving me a hard time.
 Im trying to get widescreen resolutions working on a Fujitsu Siemens with i810 graphics chipset and a Dell 2005FPW 20" LCD.

I have tried 955resolution with no luck!
 Here is parts of my xorg.conf

```

Section "Module"
# Load "dri"
...
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	60
EndSection
...

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x1050" 
	EndSubSection
EndSection

```

My /etc/defaults/915resolution file
```

MODE=5c
XRESO=1440
YRESO=1050
BIT=32

```


Any suggestions?


/* johannes */

---

### Post by alamba on 2006-03-15
Change below:

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"

Change to:

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"vesa"
	BusID		"PCI:0:2:0"

Reboot. This will atleast get you up and running. Then we can look at your xorg logs to see what's wrong.

A

---

### Post by fumidus on 2006-03-15
I changed the driver to vesa and rebooted.
 When trying the resolution 1400x1050 it only shows me a blank black screen with no error report from Xorg.


/* fumidus */

---

### Post by alamba on 2006-03-15
Do you have a modeline entry in that? I'm assuming u're using 5.10. Based on the monitor you have you'll need to put in the horizontal and vertical frequencies and modeline.

A

---

### Post by alamba on 2006-03-15
oops...fumidus...sorry but I think i've given you incorrect advice. I thought you couldn't get a graphical screen at all with the first driver. If you did and just not the right resolution it is highly suggested that you revert to the i810 driver.

What could probably fix the resolution would be modeline. Just google "modeline" and you'll find a number of sites that will give you the neccessary modeling entry needed based on the specifications of your display.

A

---

### Post by fumidus on 2006-03-16
I have tried with a specific ModeLine for 1400x1050@60hz with no luck.
 Starting Xorg in that resolution and freq gives me a blank/black screen, it doesnt complain about the freq being out of range.

Im giving up soon i think!


/* johannes */

---

### Post by alamba on 2006-03-18
Nothing in the logs when you use modeline?

A

---

