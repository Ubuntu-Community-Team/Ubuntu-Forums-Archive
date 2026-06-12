---
title: "Minor desktop graphics corruption with ATI 7500"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by jaynyls on 2006-07-09
Hey all,

I just took the Linux plunge on my T42 thinkpad.  Ubuntu has detected pretty much everything the notebook has.  Occassionally, I notice that some selection icons like "OK," "Apply," or "Cancel," etc., are marked with red dots or some form of graphic corruption, but disappear when i move my cursor over it.  I'm guessing this is an ATI driver issue.  Could anyone point me in the right direction with how to fix it?  The more explicit you can be, the better as I am very new with all of this.

Secondly, I'd like to get full functionality with my thinkpad UltraNav.  The middle mouse button only functions as another button as opposed to a scrollbar when pressed.  I'd appreciate some guidance there too.

Thanks.

---

### Post by gcc on 2006-12-06
Same here, with Thinkpad X31. 

xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

---

### Post by eXisor on 2006-12-06
It sounds like your card is running without acceleration. Try changing the driver to 'radeon'. Below follows my Device section of my xorg file (I have a radeon 7000).

```

	Driver		"radeon"
	Option		"GARTSize"		"64"
	Option 		"ColorTiling" 		"true"
	Option 		"EnablePageFlip"	"true"
	Option 		"AccelMethod" 		"XAA"
	Option 		"XAANoOffScreenPixmaps" "true"
	Option 		"AGPFastWrite" 		"true"
	Option 		"BackingStore" 		"true"
	Option 		"SubPixelOrder" 	"NONE"
	Option 		"DynamicClocks"		"true"
	Option		"RenderAccel"		"true"

```


The XAA stuff is to get beryl using aiglx going effectively. With these radeon 7 series cards I find I have to run in 16 bit color mode to get decent scrolling in firefox, but YMMV.

Once you've edited your xorg.conf file, reboot and type glxinfo to see if DRi is on.

---

