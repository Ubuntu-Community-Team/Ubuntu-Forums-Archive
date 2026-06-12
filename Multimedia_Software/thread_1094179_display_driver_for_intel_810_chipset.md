---
title: "display driver for intel 810 chipset"
date: 2009-03-12
forum: Multimedia Software
---

### Post by errorxp on 2009-03-12
Hello,

i just installed Kubuntu 8.10 on my older pc which has intel 810 chipset with integrated video. It seems like no display driver is installed - upon booting i get some weird artifacts. xorg.conf shows nothing

```
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

any ideas?

---

