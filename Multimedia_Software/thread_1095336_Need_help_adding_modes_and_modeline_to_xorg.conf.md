---
title: "Need help adding modes and modeline to xorg.conf"
date: 2009-03-13
forum: Multimedia Software
---

### Post by bedhead75 on 2009-03-13
I am running Intrepid Ibex in a Nvidia Twinview dual-monitor setup, with a Samsung monitor as the first screen and a LG LCD TV as my second screen.  Both are capable of supporting 1680 x 1050 resolution at 60Hz.  In my xorg.conf file, I need to specify the option "UseEdid" to "FALSE" in order to get analog sound coming out of the TV speakers from the 3.5mm jack on my PC.  The reason for this is because my graphics card doesn't allow for digital sound bypass, and I need to fool the TV into thinking that the video input from the PC is just DVI and not HDMI, otherwise the TV assumes there is sound coming in from HDMI, when there isn't, and automatically bypasses the analog audio.  
     I need help on how to manually add the proper mode and modelines to my xorg.conf file because the way it stands at the moment,the maximum resolution I can get out of both my monitors is 640 x 480 without EDID.  Can someone point me in the right direction as to exactly what else I need in order to get back the 1680 x 1050 resolution?  I'm confused on how to figure out what exact modeline I need, and where exactly I need to add this in the xorg.conf.  I've attached the current xorg.conf file.

---

