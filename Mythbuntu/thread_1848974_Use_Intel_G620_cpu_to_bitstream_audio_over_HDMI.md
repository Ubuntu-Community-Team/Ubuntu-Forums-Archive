---
title: "Use Intel G620 cpu to bitstream audio over HDMI?"
date: 2011-09-23
forum: Mythbuntu
---

### Post by BAdz on 2011-09-23
Hey Folks, here's a quick rundown of my hardware:
[PHP]CPU: Intel Pentium G620
MB: ASUS P8H67-M EVO 
RAM: CORSAIR XMS3 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333
HDD: Western Digital 500gb Caviar Blue 
PSU: CORSAIR CX430 

Receiver: Denon AVR-2808ci[/PHP]

I have been in talks with owners of the Intel G620 and [done my own research]("http://software.intel.com/en-us/articles/quick-reference-guide-to-intel-processor-graphics") confirming that the CPU not only can pump out HD video from the integrated GPU, but it can also bit-stream the HD audio tracks (Dolby TrueHD/DTS:HD Master Audio) over HDMI to an AVR.  The problem is that everyone I've spoken to are running Windows7 and they say the Intel chip is recognized and configured right out of the box, where my Mythbuntu box is having trouble finding this integrated audio controller.  

I first disabled the motherboards integrated audio controller in hopes that my mythbox would search and find this other controller, but so far I have been unsuccessful. I have checked and my ASLA and Xserver packages are up to date, and I've gone into the Myth settings (Utility/Settings>General) and tried toggling between ASLA: default, ASLA: Pulse, and a few other types of options that were available from that screen.

Does anyone have any ideas? solutions? similar problems? I'd love to stick with a linux solution for my HTPC but if I have to go to Windows I'll make the switch :(

Also I realize this isn't the most detailed thread post ever but I'm currently at work and unable to give more specifics.  If you need more details please let me know what you need and I'll gladly post back once I have access to the HTPC. 

Thanks so much,
-Chris

**TLDR **version: Mythbuntu is not finding any audio controllers and I am trying to setup my Intel CPU to bitstream over HDMI

---

### Post by BicyclerBoy on 2011-09-23
More questions marks than answers so it almost does not qualify as one..

G620 this is intel i3 sandybridge ?
It has HD2000 GPU I think.

If it was mine would:
- get the latest/very recent kernel
- use xorg-edgers ppa for video drivers.
- install VA-API libva stuff
- might need to update alsa user-space packages.

I think you can build MythTV with VAAPI support.
It has been practicable/possible for latest 3 months.
VA-API is to be supported in 0.25.

Could use VLC (custom build or 3rd party ppa for VAAPI) ?

Expect it to be hard to get working & expect daily xorg-edgers updates.

---

