---
title: "resolution issue"
date: 2009-04-26
forum: Multimedia Software
---

### Post by terrordrone on 2009-04-26
on my office desktop (kubuntu 8.10)..  the resolution has been reset to 800x600

and xrandr gives :

```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0
   640x480        60.0
   400x300        60.0     56.0
   320x240        60.0

```

how do i get it back to 1024x768 or higher ?

thanks

---

### Post by scootre on 2009-04-26
wrong thread sorry

---

### Post by terrordrone on 2009-04-26
this is my xorg.conf

```

....
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

```

this is the card on the system :
```

01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev c1)

```

please help..

---

### Post by terrordrone on 2009-04-28
bump :confused:

someone please help

---

