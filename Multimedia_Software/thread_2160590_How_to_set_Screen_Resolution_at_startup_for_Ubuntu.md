---
title: "How to set Screen Resolution at startup for Ubuntu 12.10"
date: 2013-07-07
forum: Multimedia Software
---

### Post by dccmgb on 2013-07-07
I am currently using an LCD TV (16:9)  as my monitor for Ubuntu 12.10.  The resolution I desire is when starting up is 1280x720.  The resolution that is selected upon startup is 1024x768 - then I manually have to to to Settings, then /Display, and then click on Detect Displays so to get the 1280x720 option.  It would be nice to have the 1280x720 resolution be automatically set upon startup instead of having to change it each time.

Any suggestions on how to accomplish that would be appreciated.  Thanks.  dccmgb

---

### Post by gordintoronto on 2013-07-07
Is this a "720P" TV? What video card is in your computer? Have you installed an "additional driver"? How is your computer connected to the TV?

From what I have seen, this type of problem is often caused by using an adapter to go from computer to display, where they don't have a common connector type. If both support HDMI, for example, it just doesn't happen.

---

### Post by dccmgb on 2013-07-08
The video is built in to the M61PME-SP2 motherboard by Gigabyte.  It uses the NVIDIA[SUP][SIZE=2]®[/SIZE][/SUP] GeForce 6100 / nForce 430 chipset.  The TV is capable of 1920x1080 resolution but is too small to view when sitting 10' away - that is why I prefer the 1280x720 resolution.  It is connected to the TV via a VGA port on both ends.  When I run Microsoft XP on the same computer it has no problem with the 1280x720 resolution.  Let me know what other information you may need.  Thanks.

---

### Post by gordintoronto on 2013-07-09
I assume you have installed nvidia-current from the Software Centre.

This is worth a shot: run Nvidia X Server Settings, click on X Server Display Configuration (the second line on my computer). There's a drop-down box labelled Resolution, which should let you choose the one you want. I'm not certain that it will remain that way across reboots, though. Please let us know if it works.

---

### Post by dccmgb on 2013-07-12
I was able to run Nvidia X Server Setting and set the resolution to 1280x720 and it worked fine until I restarted the system, in which the resolution reverted back to 1024x768 - so I had to go back and manually reset to 1280x720 (as I usually do).  For some reason on system startup, the initial password screen has already reverted back to 1024x768.  For some reason, once you set the 1280x720 resolution, it will not hold that resolution the next startup.  

One observation:  the 1280x720 resolution used to work fine but after numerous 12.10 system updates, somewhere something changed to where I know have this problem.  Frustrating, especially since XP does not have this issue.

---

### Post by deri on 2013-07-12
you can set your screen resolution on xrandr command. 

"xrandr -s 1920x1080"

---

### Post by dccmgb on 2013-07-13
Tried the "xrandr -s 1280x720 command.  Still did not work as the system reverted back to 1024x768 upon startup.

One message I get most of the time on startup is "Could not apply the stored configuration for monitors".  Does this give anymore clues to the root problem?  When that happens the selected resolution is usually 1024x768 and then I manually have to set to 1280x720 in  Displays.

---

