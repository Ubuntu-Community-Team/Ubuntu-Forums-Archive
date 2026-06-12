---
title: "New ATI drivers released today"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by fishwithapipe on 2007-02-21
Linux Proprietary Driver 8.34.8 Release: x86 and x86_64 variants
Date:Wednesday 21 Feb 2007 20:00 
 
NEW FEATURES: (1) Support for ATI Xpress 1250 IGP product for AMD based motherboards.
 ISSUES RESOLVED: (1) A system hang no longer occurs when attempting to resume from hibernation mode. (2) Loading the XVideo Extension on 64-bit Xorg 6.9+ systems no longer results in the X Server segfaulting when launching with Radeon X1K products (3) Running aticonfig--dtop=(horizontal|vertical) no longer results in clone mode being activated when attempting to enable big desktop mode (4) Running through the un-install of the Linux graphics driver no longer results in the /usr/share/fglrx and /usr/share/ati folders failing to be removed

[Complete Stroy]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.34.8.html")

ChangeLog as of the RSS feed, does anyone know if this supports AIGLX?

---

### Post by christhemonkey on 2007-02-21
Not by the looks of things.  Dont have any ati hardware to test on though im afraid.
Found a nice link where you can let them know how bad you want AIGLX support:
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web)

---

### Post by fishwithapipe on 2007-02-22
Well i gave it a go, still no compositing, however this driver is a good step fixing many long standing bugs, fingers crossed for next month.

---

### Post by cb474 on 2007-02-23
In this wiki for installing the driver, why do they suggest blacklisting the old fglrx driver instead of uninstalling it?

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Wouldn't uninstalling be the cleaner solution?

---

