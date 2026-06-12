---
title: "Changing the primary monitor?"
date: 2010-05-06
forum: Multimedia Software
---

### Post by irvie on 2010-05-06
I'm trying to change my primary display in Ubuntu 10.04 64bit with an ATI 4500 series using the proprietary driver. Second monitor is coming out of VGA port on laptop.

Both the displays show up just fine and interact just fine, I just want to switch the items on the 'main' laptop display to the secondary display.

Any ideas?

---

### Post by petersfreeman on 2010-05-07
I have a similar problem.  

I have two monitors, both are connected to my video card, an ATI Radeon.  One is connected to the HDI port, the other to the VGA port.  

I want my panels to be displayed on the HDI monitor, that is I want the HDI Monitor to be my "Primary Monitor"where all of my controls are and the VGA Monitor to be my "Secondary Monitor" where I park some open windows.

I imagine that the solution is by adding some instructions in the /etc/X11/xorg.conf file but not sure how to go ahead with this and do not want to end up booting up blind because I screwed something up.

All I currently have in the xorg.conf file is:

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

Could you advise me where I should look for a solution to this problem.

Thanks,

Peter

---

### Post by petersfreeman on 2010-05-07
Try this, it worked for me:

[http://ubuntuforums.org/showthread.php?t=1329566&highlight=Primary+Display](http://ubuntuforums.org/showthread.php?t=1329566&highlight=Primary+Display)

Peter

---

