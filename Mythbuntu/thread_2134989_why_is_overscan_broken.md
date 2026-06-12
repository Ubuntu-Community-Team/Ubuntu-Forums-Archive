---
title: "why is overscan broken?"
date: 2013-04-12
forum: Mythbuntu
---

### Post by itlarson on 2013-04-12
A recent upgrade removed overscan correction from nvidia-settings on two of my systems. One has a gt-220 card, and the other is a Zotac Ion. I don't remember the exact chipset.  First, why is this a problem now after several trouble free years?  Secondly, what can I do about it.  Note that I need the proprietary driver for vdpau.

Here's another post on this issue:

[http://ubuntuforums.org/showthread.php?t=2134878&highlight=overscan]("http://ubuntuforums.org/showthread.php?t=2134878&highlight=overscan")

---

### Post by itlarson on 2013-04-13
I'm pretty sure this was all caused by a change in the newest proprietary Nvidia driver-  I found the solution at ask ubuntu.  The following command sets overscan corection from the command line:

nvidia-settings --assign CurrentMetaMode="DFP-1: 1280x720 { ViewPortIn=1280x720, ViewPortOut=1215x685+31+16 }"

The 1215x685+31+16 part is the corrected screen size, along with x and y offsets.  I had to determine this by trial and error.  To make the changes stick after a reboot, I needed to edit xorg.conf.  I made this change in the "Screen" section:

old:

Option "metamodes" "1920x1080 +0+0; 1280x720 +0+0"

new:

Option "metamodes" "1920x1080 +0+0; 1280x720 { ViewPortIn=1280x720, ViewPortOut=1215x685+31+16 }"

This gives me overscan corection in 1280x720, but not in 1920x1080. I have Mythtv set up to change resolutions when it starts playback.  That way I can read the screen from across the room when I'm using it as a computer monitor, but still have 1080p when playing back TV recordings. There's no overscan correction in 1080p, which reduces the load on the GPU, leaving more processing power for deinterlacing.

---

### Post by BicyclerBoy on 2013-04-16
The 319 beta driver release notes suggests that underscan adjustment has returned to the GUI settings tool..

You can override the screen dpi & use (native ?) 1080p..Changing the dpi scales the desktop widgets & text..

---

