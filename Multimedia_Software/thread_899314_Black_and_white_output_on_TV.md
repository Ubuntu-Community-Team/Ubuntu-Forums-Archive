---
title: "Black and white output on TV"
date: 2008-08-24
forum: Multimedia Software
---

### Post by freak_lick on 2008-08-24
Hi,
I have Laptop Toshiba Tecra A8 with inegrated graphics intel gma 950, it has S-Video out that I have connected to TV with SCART. On Win XP i get picture a ok, but in Ubuntu 8.04.1 i get it black and white.
I know it can be fixed, just don't know how exactly.
I have read in forums that i need to add

Option		"TVStandard" "PAL-B"
Option		"TVOutFormat" "SVIDEO"

in Section "Screen" in xorg.conf file, as i did...


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"TVStandard" "PAL-B"
	Option		"TVOutFormat" "SVIDEO"
EndSection

but it is still black and white..
Any help?

---

### Post by tronica on 2008-09-27
I have the exact same problem, I've searched... and searched, but can't find a solution. The strange part is in windows its just fine. Does anyone have a solution?

---

