---
title: "Need External Monitor Set as Default"
date: 2009-04-02
forum: Multimedia Software
---

### Post by Storms a Brewin on 2009-04-02
I have a Dell Inspiron 1720 and am running Ubuntu Intrepid. My laptop is 17" and my Samsung external monitor is 24". I am running an Intel Graphics Accelerator: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller. Can you tell me how to change my xorg.conf file to set my external monitor as the default so when I full screen it goes to the monitor? (My xorg.conf is bare bones)


# xorg.conf (X.Org X Window System server configuration file)

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier      "Default Screen"
	SubSection "Display"
		Virtual	3840 1200
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by Storms a Brewin on 2009-04-02
bump

---

