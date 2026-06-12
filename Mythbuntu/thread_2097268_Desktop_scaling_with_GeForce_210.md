---
title: "Desktop scaling with GeForce 210"
date: 2012-12-22
forum: Mythbuntu
---

### Post by wilma92010 on 2012-12-22
Hi There,

I am running mythbuntu 12.04 and just installed a GeForce 210 video card in my HTPC.  Mythbuntu recognized the card and installed the default driver.  Everything worked except audio over HDMI.

I decided to upgrade to the recommended proprietary driver.  This actually is not the current Nvidia released driver, but an older version.

I now have sound over the HDMI cable (had to do other things for this as well), however the desktop is not correctly scaled.  The Nvidia X Server Settings app properly reports my Samsung 42 inch Plasma display and its correct 1280x720 resolution.   

I also updated to the "updated" version of the recommended driver through the "Additional Drivers" app and the current version is 304.43.  

But no help on scaling.  By this I mean that the desktop does not fit my TV (or tightVNC) and all applications are launched as very large windows, often off the edges of the visible part of the desktop.  But without scrolling.  

MythTV does scale correctly and videos are displayed correctly.

I have other kinds of problems, like with MySQL, so proper scaling makes debugging MythTV much easier.

Any help with this problem would be appreciated.

Thanks you,

Wilma

---

### Post by BicyclerBoy on 2012-12-22
Best soln:
The better TVs have a input mode setup that allows "direct-pixel mapping".
Could be called:
- direct pixel mapping
- just scan
- PC mode
- no overscan

Fall-back soln:
The nVidia drivers allows overscan correction.
Older driver has option in nvidia-settings GUI.
Newer driver has forced us into option settings in hidden file or in xorg.conf.
(viewportin & viewportout)

The overscan compensation does has performance implications for weak shader GPUs like GT210.
Sorry but the GT210 is not a good choice.
AFAIK The GT210 & some GT220 don't have complete HDMI HDA capabilities.

---

### Post by barreyi on 2013-01-07
Similar problem here.

I am running Ubuntu 12.10 with a GeForce 210 card.  Audio seems to work fine through HDMI after I go into the sound settings and select it.  However, when I install the proprietary drivers I get the same issue as stated before.  I just figure I'll use the open source drivers unless there is some way to fix this problem.

---

### Post by BicyclerBoy on 2013-01-07
Just roll nvidia driver back to before the viewportin/out nonsense started..

I have my lucid HTPC box pinned at 295.xx..

---

### Post by kernowkoi on 2013-04-05
Hi All,

Have put together a Mythtv htpc with the Geforce 210 card. was miffed when found this overscan issue. 

Does anyone know the Viewport settings,  I have read that the Geforce 210 card has no support for that option in the xconf.org file

where/how did you get the 295.xx driver?



Some Additions:  OK So hears how my afternoon went______________________

Removed the proprietary drivers and and tried open source. Can't get anything better than 800x600 resolution, still with overscan issue!

Re-installed proprietary driver. the default is 295.40, but for some reason no longer has any options to change resolution or choose second screen

Tried a later version of 295.75 driver, no luck would not install.

Tried for the heck of it the latest 310.44 version driver.  system fails to load X term at all no desktop.

Manual removed All Navida drivers and let system restart on open source,

Finaly reinstaled proprietary driver 304.xx driver from additional drivers list. As this seems to give me the best results. but not great
Tried on a couple of TV's we have but same effect.

As this is a mythtv htpc what would be helpful would be some suggestions on myth settings to help with the issue.

Any thoughts would be appreciated.
Rgs
Steve

Rgs
Steve

---

### Post by BicyclerBoy on 2013-04-06
The GT210 is weak on shaders (just like 520/610) so scaling could be overloading with de-interlacing as well..

The 295 driver was the last with easy aspect ratio scaling (overscan compensation).

To get 295 installed you most likely need to install via "nVidia driver install" method..The driver readme has all the gory details.

The metamode viewport stuff can be used in xorg.conf or .nvidia-settings-rc

Supposedly the later xrandr can allow scaling (with nvidia driver) but with easy syntax.

16:9 aspect correct scale (W-80, H-45)
```

nvidia-settings --assign 0/CurrentMetaMode="DFP-1: 1920x1080 { ViewPortIn=1920x1080, ViewPortOut=1840x1035+40+22 }"
```

---

