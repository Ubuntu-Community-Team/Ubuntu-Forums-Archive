---
title: "NVIDIA : HDMI output is worse than VGA"
date: 2011-05-30
forum: Multimedia Software
---

### Post by nono240 on 2011-05-30
Hi folks, thanks for reading !

I recently switched from my integrated GPU (i5-650 Clarkdale) to a brand new nvidia GT520 but now my HDMI output is worse than my VGA : bright colors are completely saturated. I noticed that switching the HDMI colorspace from "full" to "limited" (using nvidia-settings) somewhat reduce the effects but doesn't solve it. I even tried to play with my monitor setting, with no luck.

This was NOT the case previously. I'm using the latest nvidia-drivers and my 2 monitors are the same reference ([FONT=Verdana][SIZE=2]LG 22" LCD - W2261VP-PF)[/SIZE][/FONT]. Ubuntu 11.04.

---

### Post by BicyclerBoy on 2011-05-30
I assume you are comparing video playback colour saturation etc..
As you seem to already know..
HDMI video (TVs) uses different colour space & normally use YUV encoding (actually YCbCr) not RGB.
HD & SD video have different colour space.

The PC can output either full or video & AFAIK most HDMI connectible PC monitors are okay with both. The EDID data indicates this capability.

The setting colour-space full to limited is meant to adjust the RGB levels from 0-255 to 16?-235.
I don't know what it does to the YUV output..

The nvidia driver will use full range by default for a PC type display (from EDID info) & the video mode used.
The nvidia driver's seem to have known & unfixed problems with colour-space.

My experience with nvidia VDPAU GT240 & HDMI YUV plasma TV was that it has excellent (correct) colour & blacks..

What version of nvidia driver are you using ?
266 or later seems to have addressed some of the problems.

Are you using VDPAU video decode/presentation ?

There are VDPAU settings for colour space. How you set/get them outside of MythTV/XBMC, I do not know.

---

### Post by nono240 on 2011-05-30
> **BicyclerBoy said:**
> 
Are you using VDPAU video decode/presentation ?


Absolutely not. Everything is satured, included my desktop wallpaper and window decorations !

---

### Post by BicyclerBoy on 2011-05-31
What version nvidia driver are you running ?
Where did you get the nvidia driver from ?
Standard Ubuntu distro or
nvidia.com driver downloads or
nvidia x-swat team ppa or
xorg-edgers ppa or
other..?

Can you ditch one HDMI connection for a real DVI-D connection ? or does the monitor use single_link_DVI-HDMI adapter cable.

Your monitor has (2) preset temperatures + sRGB + user settings ?

---

### Post by nono240 on 2011-05-31
> **BicyclerBoy said:**
> What version nvidia driver are you running ?
Where did you get the nvidia driver from ?
Standard Ubuntu distro or
nvidia.com driver downloads or
nvidia x-swat team ppa or
xorg-edgers ppa or
other..?

Can you ditch one HDMI connection for a real DVI-D connection ? or does the monitor use single_link_DVI-HDMI adapter cable.

Your monitor has (2) preset temperatures + sRGB + user settings ?

I used the "nvidia-current" package. 

The monitor have VGA, HDMI, and DVI. I didn't tried the DVI (yet), but since I have 2 monitors I planned to move to HDMI+DVI instead of HDMI+VGA. If DVI works well, maybe I should get rid of HDMI.. :(

Concerning the presets, I tried all of them, but there was no big improvements.

---

### Post by BicyclerBoy on 2011-05-31
nvidia-current does not mean much .. it is a empty meta-package for some version that ubuntu has released.
You could post the /var/log/Xorg.0.log file (as .txt attachment, because we so admire windows here, we use its file extensions).

This file will show the version & maybe some colour-space settings.

The HDMI DVI cable was a long shot any way..
My work PC uses LG w245 monitor that has HDMI only (+VGA) but it works fine as DVI connection.

From what have read in nvidia driver notes...if you select YUV colour, the driver forces limited colour range. This is a poor decision to make.
This would cause your colour saturation if the monitor does not detect reduced range.
(A HDMI TV is not likely to have this problem.)

The equivalent xorg.conf to the nvidia-settings app
Option "ColorSpace" "GPU-0.DFP-0: YCbCr444"
Option "ColorRange" "GPU-0.DFP-0: Limited"[FONT=monospace]   #(forced)

I would suggest that forcing RGB & full colour range should fix the problem..
[/FONT]Option "ColorSpace" "GPU-0.DFP-0: RGB"
Option "ColorRange" "GPU-0.DFP-0: Full"[FONT=monospace]
[/FONT]
I would also suggest using the nvidia driver from
nvidia x-swat team ppa
version 270.41.19 is recommend by nvidia for your GPU.

Other:
HDMI is an electrical subset of DVI.
A 19 pin HDMI cable is equivalent to a single link DVI-D cable.
Single link is fine for 1920x1200@60.
But HDMI standards are more evolved.

You can **not** connect HDMI to VGA without some external active adapter.
You can convert HDMI output (video card) to single link DVI-D with $5 cable adapter

---

### Post by nono240 on 2011-06-01
Apparently, i'm already running 270.41.19 :

[ATTACH]193830[/ATTACH]

See also : [ATTACH]193832[/ATTACH]

I'll give a try to your xorg.conf settings...

---

### Post by nono240 on 2011-06-05
I tried the DVI output: the result is "acceptable" but only in "limited" color range. That's better than hdmi though, but still worse than vga...
Ill try to force your settings into the .conf

---

### Post by eddier on 2011-06-05
Have you disabled the integrated graphics?

ed

---

### Post by BicyclerBoy on 2011-06-06
Doubt editing xorg.conf will do anything.
Your selections in the nvidia-setting program should achieve the same as the text strings, ColorSpace & ColorRange, in /etc/X11/xorg.conf file.

Your attached nvidia-settings.rc.txt shows boolean values for the "Color" variables & I don't know how to compare to "RGB" or "Limited"

I would have thought that selecting "limited range" colour would look more saturated if the monitor was not detecting limited range.

Is your monitor set to sRGB colour-space in RGB input mode ?
Can you disable the digital processing engine flatron DAFT ?

I have little faith in any LG processing engine after having studied their TVs.

---

