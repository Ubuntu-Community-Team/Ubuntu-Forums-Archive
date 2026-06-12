---
title: "How to Set Non-Standard Video Resolution"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by MikeMcCollister on 2006-08-22
I have just installed Ubuntu on to a virtual machine. By editing the /etc/X11/xorg.conf I have ensured that my system will only work with 800x600 but making the screen section look like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c764/765 [Trio32/64/64V+]
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
EndSection


However, I want to add a mode for something like 1024x700. When I add this option to the Modes line it does not work.  Note that 1024x768 is not an option in this configuration.

Any idea how to do this?

Thanks,

Mike

---

