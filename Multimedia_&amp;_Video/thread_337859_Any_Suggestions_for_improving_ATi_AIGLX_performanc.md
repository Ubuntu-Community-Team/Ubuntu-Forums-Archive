---
title: "Any Suggestions for improving ATi AIGLX performance?"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by happy-and-lost on 2007-01-13
I'm using AIGLX/Beryl on my ATi x300 card, and it seems a bit laggy. Does anyone have any useful xorg.conf tweaks (Like the: Option "XAANoOffscreenPixmaps" tweak) which may improve performance a little?

My Device section already looks like this...

```
Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option 		"DRI" 		 "true"
        Option 		"ColorTiling" 	 "on"
        Option 		"EnablePageFlip" "true"
        Option 		"AccelMethod"	 "EXA"
        Option 		"RenderAccel" 	 "true"
EndSection
```

---

### Post by strawman on 2007-01-14
if you are using 

```
Option          "XAANoOffscreenPixmaps"
```

then your acceleration method should be:

```
Option 		"AccelMethod"	 "XAA"
```

or vice versa

---

### Post by teddmeister2 on 2007-06-17
With EXA rendering the option should be "EXANoOffScreenPixmaps", but I've used the option "AccelDFS" "true", and think I may have gotten a slight improvement in performance.
Does anyone else have any good tweaks for an ATI card in xorg.conf?

N/M, just tried going back to EXA and couldn't get my desktop to run stably.

---

