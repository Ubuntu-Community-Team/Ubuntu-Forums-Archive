---
title: "How is X configured in Ubuntu?"
date: 2009-01-20
forum: Multimedia Software
---

### Post by nPoc on 2009-01-20
My current xorg looks like this.
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3080 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

So where is my "Configured Video Device" actually configured?  Is this a new auto-setup xorg feature?  What exactly happened here?  Just curious, basically if I go messing with things I want to make sure that X isn't making use of some additional files other than /etc/X11/xorg.conf, so I can go back to functioning without much hassle.

---

