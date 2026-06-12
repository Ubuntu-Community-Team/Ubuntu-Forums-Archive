---
title: "msi wind + intel 9xx dual monitors"
date: 2009-05-04
forum: Multimedia Software
---

### Post by robfindlay on 2009-05-04
The UXA fix worked--mostly stable.  Is it possible to get dual screen working? the following virtual settings force the system back down to VESA drivers. 

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1024
	EndSubSection

```

Any help would be much apprieated.

---

