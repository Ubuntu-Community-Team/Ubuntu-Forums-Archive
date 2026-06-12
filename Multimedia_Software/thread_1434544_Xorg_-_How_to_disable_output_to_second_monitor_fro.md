---
title: "Xorg - How to disable output to second monitor from xorg.conf?"
date: 2010-03-20
forum: Multimedia Software
---

### Post by rockyrobin on 2010-03-20
I'm currently using 2x ATI radeon 4850's with some OpenCL apps but don't need any video output from the second card as it is only doing GPGPU.

I would like to keep this card useable by the OpenCL apps, but not be available for video output.

I have tried trimming the xorg.conf here there and everywhere in an attempt to achieve this, but it would appear that as soon as the second card is not outputting something (even without connected monitor) then the ATI Catalyst fglrx does not allow the use of the card with the OpenCL apps.

Is there a command I can offer the xorg.conf file to disable the monitor output for the second card? I had a looksee at the man page for xorg.conf but couldn't find anything :confused:

---

### Post by rmt1947 on 2010-04-02
I had a similar problem myself yesterday and managed to solve it after reading three helpful threads.  My system is: ASRock X58 Deluxe motherboard, Intel Quad Core i7 (OpenCL capable), Radeon HD2600 (not OpenCL capable) for the monitor, three Radeon HD4650 (OpenCL capable) for GPGPU only;  OpenSUSE 11.2, kernel 2.6.31.12, ATI Catalyst (=fglrx) 10.3, ATI Stream SDK v2.01 with OpenCL 1.0.

I first modified xorg.conf so that it had four "Screen" sections and four "Device" sections, three of the latter including

Option "UseDisplayDevice" "none"

as explained at

[http://forums.nvidia.com/lofiversion/index.php?t49245.html](http://forums.nvidia.com/lofiversion/index.php?t49245.html)

[http://gpgpu.org/forums/viewtopic.php?t=4970](http://gpgpu.org/forums/viewtopic.php?t=4970)

However, that alone was not enough.  I also needed to issue the command

export DISPLAY=:0

as suggested at 

[http://forums.amd.com/forum/messageview.cfm?catid=328&threadid=121437](http://forums.amd.com/forum/messageview.cfm?catid=328&threadid=121437)

This finally gave me the result I wanted:  the OpenCL function

clGetDeviceIDs(.,CL_DEVICE_TYPE_ALL,.,.,.)

returned the number of devices present as 4, which is correct (see system specification above).

---

