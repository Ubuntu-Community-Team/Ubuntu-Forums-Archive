---
title: "ubuntu doesent recognize widescreen monitor"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by jamesford on 2006-12-05
hi, i just bought an eizo flexscan s2110w widescreen lcd. 

the problem is ubuntu dosent recognize it properly and gives it a resolution of 1280x1024, while it should be 1680x1050. 

ive run sudo dpkg-reconfigure xserver-xorg and also booted the live cd to see if there was any change, but its still running at 1280x1024.

xorg also sees it as 'default monitor' iirc. 

ive added 1680x1050 to xorg manually so all is well, but my question is is there anything else i need to do ? and is there something else i should do to ensure this monitor becomes fully detected in feisty?

---

### Post by kimara on 2006-12-05
Put this to your xorg.conf under Monitor Section

Modeline "1680x1050"  119.12  1680 1728 1760 1840  1050 1052 1058 1080

maybe it work

---

### Post by MacD on 2006-12-06
You may need to change the VertRefresh rate in xorg.conf
Check the specs to see what rate your monitor can handle

---

### Post by jamesford on 2006-12-06
thanks for the help

how do i set the vertical refresh rate in xorg?
from the specs: Vertical frequency [Hz]:  	 49 – 86 analog / 59 – 61 digital

how do i put that in xorg? im using digital (DVI)

i tried putting "1680x1050@60Hz" but i dont think it did anything. what is the syntax suppsed to look like?

---

### Post by MacD on 2006-12-06
Sorry to not be more clear.

My xorg.conf has a section like this:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-76
	VertRefresh	43-80
EndSection

I just changed the number (80) from the default lower number it was.

I'm no expert here, but I also recall somewhere seeing using the syntax you tried except using "_" instead of "@".

---

