---
title: "Performance tweaks for radeon driver?"
date: 2008-12-13
forum: Multimedia Software
---

### Post by Twilight in Zero on 2008-12-13
Hi there. I've got a Gateway MT6452 laptop with an ATI Radeon Xpress 1150. I'm running Ubuntu Intrepid. Fglrx really stinks, for various reasons (video on compiz, zsnes, others), so I use the open source radeon driver. I'm trying to tweak it for extra performance.

Here's my xorg.conf, device section:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	BusID		"PCI:1:5:0"
	Option		"GARTSize"		"32"
	Option		"AccelMethod"		"EXA"
	Option		"EXANoOffscreenPixmaps"	"on"
	Option		"ColorTiling"		"on"
	Option		"BackingStore"		"on"
	Option		"EnablePageFlip"	"on"
	Option		"RenderAccel"		"on"
	Option		"SubPixelOrder"		"NONE"
EndSection
```

I've also installed DRIconf, but I can't make sense of most of the options. I've only disabled vsync there.

Is there anything else I can do to improve performance? Also, how do I add extra resolutions? Adding display subsections in the Screen section doesn't seem to work for Intrepid.

---

### Post by 2hot6ft2 on 2008-12-13
While not specifically for the graphics driver if you just want to do some tweaking for performance... I have done these on both my Hardy desktop and Intrepid laptop machines. Just use what you're sure you're comfortable with as I didn't do them all but most of them. Here you go.
[http://forumubuntusoftware.info/viewtopic.php?f=42&t=894&sid=b0234a8891bbfb37ee63c45d986485bb](http://forumubuntusoftware.info/viewtopic.php?f=42&t=894&sid=b0234a8891bbfb37ee63c45d986485bb)

Just be sure not to disable anything laptop specific and you should be alright however the usual disclaimer applies I will not be responsible if you mess up.

---

### Post by NoVista on 2008-12-14
You might want to try these drivers >>
[https://launchpad.net/~tormodvolden/+archive](https://launchpad.net/~tormodvolden/+archive)
Just use the .deb files by selecting one of the three links near the top of the page.

More info >>
[http://www.phoronix.com/scan.php?page=news_item&px=NjkwNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjkwNQ)

Greatly increased acceleration, no tearing, with full screen video still falling just a tad short, but way better than any original ATI driver.

---

### Post by Twilight in Zero on 2008-12-16
Ah, these are great drivers indeed! They've given me a little bit of a performance increase. I've bookmarked his ATI driver folder. Thank you!

What I really want to know, though, is about additional tweaks I can put into xorg.conf. Like, is it safe to use AGPFastWrites and AGPMode with Xpress IGPs? (I'm guessing not, since it's an IGP.) Should I increase my GARTSize? Any other options that might help? I haven't toucheed my xorg.conf since starting this thread.

DRIconf, too. What's the fastest TCL mode? The best method for limiting rendering latency? What size should I make the command buffer? Actually, I'd like to know about every option there. The only one I know is the one for Vsync (which is forced off right now).

---

