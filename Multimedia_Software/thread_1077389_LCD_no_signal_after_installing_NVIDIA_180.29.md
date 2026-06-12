---
title: "LCD no signal after installing NVIDIA 180.29"
date: 2009-02-22
forum: Multimedia Software
---

### Post by ghotik on 2009-02-22
Ok, I've followed the steps outlined [here]("http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+180.29").  But when I boot, after the loading screen, the LDC shows no signal (orange light).  I can hear Ubuntu loading in the background, but I can see nothing.  Can someone please help me on this?  Thanks.

---

### Post by cherva on 2009-02-22
I'm not very good at that, but can you paste your xorg.conf ?

---

### Post by ghotik on 2009-02-22
```
Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
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

Thanks for the reply, I entered the Busid information manually.

---

