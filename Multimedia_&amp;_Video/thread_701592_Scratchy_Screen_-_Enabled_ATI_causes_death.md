---
title: "Scratchy Screen - Enabled ATI causes death"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Desert Fox on 2008-02-19
Hi,

I have enabled the restricted ATI drivers (running ATI Xpress 200) not knowing that the hardware didn't support 3D. Unlike the other threads, I don't get a white or black screen of death, everything is scratchy and faded out as if you was to scrape rocks on a painting.  Searching on the forums lead me to this thread [http://ubuntuforums.org/showthread.php?t=584143](http://ubuntuforums.org/showthread.php?t=584143) but it doesn't seem to work for me.

If there is anyway through recovery (since thats the only thing I can physically see) that I can disable this feature I would greatly appreciate it.

---

### Post by acoustibop on 2008-02-19
From the release notes for the current fglrx driver, Desert Fox:

> ATI Mobility&#8482; and Integrated Product Family Support

The ATI Catalyst&#8482; Linux software suite is designed to support the following ATI Mobility&#8482; products:
Mobility&#8482; Radeon&#8482; X1800
	Mobility&#8482; Radeon&#8482; X600
Mobility&#8482; Radeon&#8482; X1600
	Mobility&#8482; Radeon&#8482; X300
Mobility&#8482; Radeon&#8482; X1400
	Mobility&#8482; Radeon&#8482; X200
Mobility&#8482; Radeon&#8482; X1300
	Mobility&#8482; Radeon&#8482; 9800
Mobility&#8482; Radeon&#8482; X1200
	Mobility&#8482; Radeon&#8482; 9600
Mobility&#8482; Radeon&#8482; X1100
	Mobility&#8482; Radeon&#8482; 9550
Mobility&#8482; Radeon&#8482; X800
	Mobility&#8482; Radeon&#8482; 9500
Mobility&#8482; Radeon&#8482; X700
	Mobility&#8482; Radeon&#8482; Xpress 1100 series
Mobility&#8482; Radeon&#8482; Xpress 1200 series
	Mobility&#8482; Radeon&#8482; Xpress 200 series
According to this, the ATI Xpress 200 is supported.

**Edit:** FWIW I always use the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") howto for installing ATI drivers - it seems the most complete and problem-free one to me.

---

### Post by Desert Fox on 2008-02-20
ah ok thanks for bringing that to my attention. However, wouldn't I have to be on linux to install these drivers or can I install them in recovery mode? (Since I can't see through the scratchy screen)

I'll check the link out. Thanks.

---

### Post by Desert Fox on 2008-02-21
Well I got everything running perfectly now, followed this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) (used method 1)

However, 3D effects (cube, multi workstations etc) still aren't working, is there anything I've done wrong or over looked?

---

