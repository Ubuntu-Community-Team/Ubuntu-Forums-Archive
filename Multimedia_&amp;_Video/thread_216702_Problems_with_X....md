---
title: "Problems with X..."
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by KrazyArrow250 on 2006-07-15
First, I'll start by saying that I know this sounds like a Refresh rate problem, but I've gone through just about every solution on these forums regarding refresh rates and none of them have fixed this.
Okay, the problem:
I recently downloaded Ubuntu 6 to give Ubuntu another try.  I installed it using the alternate install disc because I had display problems during the graphical install.  When the install was complete and the computer restarted, my monitor (an [HP L1955]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/382087-64283-444767-72270-444767-427304.html")) displayed the error message "Input Signal Out of Range".
I followed instructions found here to fix refresh rate problems so my xorg.conf now looks like this (only the relavent section):
```

Section "Monitor"
Identifier "HP L1955"
Option "DPMS"
HorizSync 30-82
VertRefresh 56-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc.  RV350 AR [Radeon 9600 XT]"
Monitor "HP L1955"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024_60"
EndSubSection
#All of the rest of the SubSections look the same, excluding the
#Depth setting of course.
EndSection

```

Once again, my monitor is an HP L1955
And my graphics card is an ATI Radeon 9600XT AIW.

Thanks in advance.

---

### Post by KrazyArrow250 on 2006-07-17
Bump?

---

### Post by tseliot on 2006-07-17
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by KrazyArrow250 on 2006-07-17
Wow thanks mate, I thought I tried everything in there, apparently not in the right order though.  6.06 looks awesome on my LCD :P

Now only to get WoW running....

---

