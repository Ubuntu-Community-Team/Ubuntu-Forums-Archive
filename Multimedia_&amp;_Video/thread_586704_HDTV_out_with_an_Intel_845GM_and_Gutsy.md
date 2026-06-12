---
title: "HDTV out with an Intel 845GM and Gutsy"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by MatBi on 2007-10-22
I'm trying to get a valid video output  on a JVC HDTV; the TV is connected with an DVI -> HDMI cable.
I did some research but couldn't get a solution: everything i try puts the TV in bluescreen mode.
As far as i know, the Intel 854GM chipset is also included into the Mac Mini. 
Here's some infos:

**# xresprobe intel**
id: FPDEUFT3
res: 1920x540
freq: 15-46 49-61
disptype:

**# ddcprobe**
vbe: VESA 3.0 detected.
oem: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r) 82945GM Chipset Family Graphics Controller Hardware Version 0.0
memory: 12288kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid:
edid: 1 3
id: 21be
eisa: JVC21be
serial: 01010101
manufacture: 0 2006
input: analog signal.
screensize: 22 9
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
dtiming: 1920x540@62
dtiming: 1920x540@67
monitorname: FPDEUFT3
monitorrange: 15-46, 49-61

According to this infos, i tuned the xorg.conf to have in the Monitor section:
HorizSync       15-46
VertRefresh     49-61
Modeline "1920x540"      74.25  1920 2008 2052 2200  540 542 547 562 interlace +hsync +vsync
In the screen section, i point to the "1920x540" mode.

A 720p mode would also be ok, but the TV doesn't seem interested in it, and there's no video mode from the card; the only mode that works so far is 480p.
I post here some links that i found interesting:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)
[http://ubuntuforums.org/showthread.php?t=95864](http://ubuntuforums.org/showthread.php?t=95864)
[http://ubuntuforums.org/showthread.php?p=3520998](http://ubuntuforums.org/showthread.php?p=3520998)
[http://ubuntuforums.org/showthread.php?t=292108](http://ubuntuforums.org/showthread.php?t=292108)

I also tried to play around with 915resolution; now i'm stuck without any further idea.
It would be great, if anyone more successful than me could share his knowledge (and xorg.conf).

Thanks,
MatBi

---

### Post by High_Noonan on 2007-10-25
I'm in the same boat. My Mini is Intel Core 2, Intel 945 video with DVI to HDMI cable. 

All I have is a black screen on my 37" LCD. Even if I krdc to the Mini, the display is black.

I switched to i810 and was able to get a desktop displayed, but only in 1024x768. :-(
What is interesting is that when the desktop came up in i810, I had a new xserver-xorg-intel driver waiting to be installed: 2.1.1.1, I think. Switching to back to Intel put me back to a black screen after a full-reboot.


~# xresprobe intel
id: 37LC2D-UD
res: 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 30-61 56-75
disptype: 


# ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r) 82945GM Chipset Family Graphics Controller Hardware Version 0.0
memory: 16064kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 0001
eisa: GSM0001
serial: 0000821a
manufacture: 2 2006
input: analog signal.
screensize: 82 46
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 640x480@75
ctiming: 800x600@75
ctiming: 1024x768@75
dtiming: 1024x768@74
monitorrange: 30-61, 56-75
monitorname: 37LC2D-UD

Just went thru Xorg.0.log and it thinks it is working until I get to the last two lines:

(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV

---

### Post by MatBi on 2007-10-26
To clarify a bit my situation, the DVI output works fine ant 1600x1200, 1024x768 and other standard res, none of which is accepted by the HDTV. From specs, the HDTV accepts only 480p (which works but is not hires), 720p and 1080i. My goal is to set the video output to any of the HD modes.

---

### Post by pijiu on 2007-12-14
I'm in the same boat, I'm trying to get 1360x768 resolution but it doesn't want to happen.

```
vbe: VESA 3.0 detected.
oem: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)915GM/910ML/915MS Graphics Controller Hardware Version 0.0
memory: 7872kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 6
edid: 54 0
id: 4000
eisa: Y@Y4000
serial: 30260041
manufacture: 24 2126
input: composite sync, digital signal.
screensize: 242 49
gamma: 1.000000
dpms: non-RGB, no active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@67 Hz (Mac II, Apple)
ctiming: 504x504@92
ctiming: 504x504@92
ctiming: 504x504@92
ctiming: 248x155@120
ctiming: 248x186@79
ctiming: 768x576@73
ctiming: 912x684@81
dtiming: 522x544@572
dtiming: 4095x4095@34
dtiming: 4095x4095@34
dtiming: 4095x4095@34

```

---

