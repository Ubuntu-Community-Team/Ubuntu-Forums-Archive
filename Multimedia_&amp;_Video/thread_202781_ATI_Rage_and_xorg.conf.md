---
title: "ATI Rage and xorg.conf"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by Martian on 2006-06-24
According to ATI, I've got a RAGE 128 PRO 32MB AGP VGA - DELL.  Dell calls it a "ATI Rage 128 Ultra".

From my xorg.conf:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 Pro Ultra TF"
	Driver		"r128"
	BusID		"PCI:1:0:0"
	Option          "AGPMode" "4"
EndSection
```

Originally the driver was set to "ati"... and I added the AGPMode stuff (otherwise it was at AGP 1x), which actually seems to have improved performance in glxgears by about 7 or so fps.

My question is: should I have done anything else when I modified xorg.conf (aside from backing it up first and then restarting x afterward) with these changes?  Or are these changes sufficient to have Ubuntu use the r128 drivers for my video card and use AGP 4x?

---

### Post by BryanG3301 on 2008-06-10
This is the exact same video card that I have, has there been any update to the functionality of this card yet?

---

