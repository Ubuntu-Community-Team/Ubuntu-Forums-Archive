---
title: "problem with gt440 resolution"
date: 2013-09-15
forum: Multimedia Software
---

### Post by jgw on 2013-09-15
Below is my original post.  Since i wrote that I went back into the nvidia and dinked with the x server display configuration.  the selection is no longer a denon 72" tv but a denon avamp (DFP-1 on GPU=0)  I then clicked on the resolution and chose a resolution of 1680x1050 (this resolution no longer exists and it now goes from 1920x1080 to 1280x720), set the configuration to a separate x screen (the configuration used to have two options, I think; all displays and denon, now its separate x screen, disabled, or twin view.  Anyway, I then changed the viewportout to 1850x1030+70 which kinda works.  the system magically changed that to 1728x1080+96.  The problem with this whole thing is that, if I move the cursor all the way to the right, the entire screen suddenly moves to the left with about 10/15% blank screen on the right.  the same occurs when I move the cursor all the way down in that the screen then displays an approximately 5 to 7% blank space on the bottom.  I seem to be getting there but, I suspect, somebody must have an answer to this one.  I have been computers for a long time and have learned to live with stuff but I would really appreciate any help that might be available, including any links to this stuff that has been solved. (I have looked but could have missed it). 

Thank you............

I have nvidia driver v319.32 for my gt440 display card.  I then, with an hdmi card, run that though my denon on its way to my tv set.  I do this so that I can control my speakers (5.1)  Anyway, when I look at the nvidia console it tells me that its getting its signal from my denon 70" tv.  The denon just passes the signal through and has no 72" tv signal although the nvidia drive, obviously, thinks that it doees.  As far as I know the denon has no controls that deal with the resolution at all.  I suspect that there is an nvidia configuration file out there, someplace, that controls the resolution but I cannot find it.  Does anybody have any idea where the resolution info is stored that might be edited?  My problem is that my screen is only 65" (diagonal) and it loos has if the resolution is about 2" off (top and side).  The board gets automatically set to 1920x1080 and I cannot get to any adjustments to make the output fit within the size of the tv set.  Resolutions are set automatically, it seems.  If I screw with the tv itself then, when it switched back to normal mode its going to be screwed up.

I finally found a thread that told me to edit the xorg.conf file and insert  Option  "ModeValidation" "AllowNonEdidModes" into the device section.  It will take some tweaking but I think I will set this one to solved

Thank you.............

---

