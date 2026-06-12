---
title: "Video card is unclaimed"
date: 2008-11-16
forum: Multimedia Software
---

### Post by degtukas on 2008-11-16
After upgrading my Dell Latitude D830 laptop to Intrepid, the video card became unclaimed. 

Video seems to work allright except that I cannot run Compiz.

/etc/X11/xorg.conf entry for "Driver" is "intel"

Why is it unclaimed? How can I see which driver is being used?

Here's what "lshw -C display" shows:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by zerubbabel on 2008-11-25
I have exactly the same situation with my D830, after a clean install of Intrepid, and am wondering whether I have the right video driver. I am experiencing random logouts with no apparent pattern of cause & effect. I suspect that the X server is crashing and restarting.

---

### Post by encryption trouble on 2008-12-18
I have the same problem here. I just recently reinstalled Ubuntu.
lsdhw -C video gives:
>  sudo lshw -C video
[sudo] password for elie: 
  *-display:0 [COLOR="Red"]UNCLAIMED[/COLOR]   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
  *-display:1 [COLOR="Red"]UNCLAIMED[/COLOR]
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

Could someone please help us out?

---

### Post by degtukas on 2009-02-04
It looks like nobody can help us...

I have also another problem, System->Administration->Screen Resolution does not work. Running gnome-display-properties in terminal gives

display-properties-ERROR **: Could not get screen info
aborting...
Aborted

Any clue?

---

### Post by degtukas on 2009-11-06
Well, I guess the problem is solved in Karmic.

---

