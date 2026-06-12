---
title: "Trouble with Dell E6500, Dock, DVI, Dual screen"
date: 2009-07-22
forum: Multimedia Software
---

### Post by trenchtractor on 2009-07-22
Hi peoples... I'll spare you the 'I'm awesome with windows' noob intro, but I am having some trouble with my current set up and build...

The hardware is as follows:

Dell E6500 with intel G45 family integrated video.
Dell PR02X Port replicator/dock, with Dual DVI-D single link out.
2 x LG L204WT 20" displays, with native res of 1680x1050.

The hardware has been running on Vista and W7, so I'd like to rule out hardware issues.

I'm running a fresh (24hr old) Ubuntu 9.04 build.  The OS is fine on the laptop, I have no real problems with it until I dock and try to use the dual display.  There are some monor issues with 'hot docking' but I don't really care about that.

In windows, the integrated video was not capable of driving the laptop monitor and the 2 x 20" displays, the laptop monitor would always disable.  However, Ubuntu seems to want to display to both, but can't generate the native resolution, instead 1153x864 is selected.  I did manage to get the display manager to set the 2 x 20" and 1 x 15" to their respective resolutions, only it crashed the display.  I'm not sure, but I suspect an X crash??  It appeared to me there was not enough memory assigned to the video device to manage 3 outputs??

I was proactive enough to record the foctory modeline for the 20" displays before blowing windows away...

```
Modeline "1680x1050@60" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -HSync +VSync
```

...so I have edited xconf to include monitor1 and monitor2 with those values... this hasn't really helped.

My goal is to have a laptop that works with the built in display 1440x900 when I'm away from the office, but can drive 2 x 1680x1050 displays when docked.  

I'm not really sure what direction to take... do I need 3 entried in xconf to cover the trhee monitors?  What's the deal with adding drivers for the intel device?  I'd like a little direction before I mess this thing up completely.

BTW, before you flame me, I've been searching this to death... and I am currently having a read of [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html).  Hopefully it will help with some of the jargon/prinicple deficit I am currently suffering.

---

### Post by trenchtractor on 2009-07-23
So the Ubuntu pocket guide was a little too noob oriented for me...

I can get the dual 20" display sto work... and that's a loose term, but whenever I restart, i get warning dialogues 'Ubuntu is running in low graphics mode' (EE) Problem parsing config file, (EE) error parsing config file.

I've tried setting virtual desktop resolution to 2x the monitor native res, ie 3360x1050, and that helped get the dual display working initially.

The windows boy in my says I need a driver for the G45... but I've been told I shouldn't need drivers...

---

### Post by trenchtractor on 2009-07-23
I've been reading up... trying to edit the xorg.conf manually... here's what I've come up with:

```
Section "Monitor"
        Identifier      "LVDS"

Option "Monitor-LVDS" "LVDS"

EndSection

Section "Monitor"
        Identifier      "TMDS-1"
        VendorName      "LG"
        HorizSync       "64.674"
        VertRefresh     "60.0"
        ModeLine        "1680x1050@60" 146.625 1680 1784 1960 2240 1050 1053 1059 1089 -HSync +VSync

Option "Monitor-TMDS-1" "TMDS-1"
EndSection

Section "Monitor"
        Identifier      "TMDS-2"
        VendorName      "LG"
        HorizSync       "64.674"
        VertRefresh     "60.0"
        ModeLine        "1680x1050@60" 146.625 1680 1784 1960 2240 1050 1053 1059 1089 -HSync +VSync

Option "LeftOf"  "TMDS-1"
Option "Monitor-TMDS-2" "TMDS-2"

EndSection

Section "Screen"
        Identifier      "Undocked"
        Monitor         "LVDS"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 1440 900
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Docked"
        Monitor         "TMDS-1, TMDS-2"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3360 1050
        EndSubSection
Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

I've no idea if it'll work yet... I'm upstairs with the kids.  I'll test it out tonight and see how it goes.

---

