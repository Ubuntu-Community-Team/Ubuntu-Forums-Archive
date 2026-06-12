---
title: "Custom modelines being ignored?"
date: 2008-06-29
forum: Mythbuntu
---

### Post by haneymike on 2008-06-29
I have been trying for days to get a Mythbuntu frontend working on my older Mitsubishi 4:3 HDTV through component out.  I used the same machine (Nvidia 6150-based) to run WinMCE for over a year with this TV, but no matter what I do, I can't get Mythbuntu to work with this TV.

Here's what I tried - 

- installed a copy of WinXP and configured the NVidia driver to work with the TV at 1280x960 resolution with essentially 1080i timings.  This is what worked for me forever when running WinMCE.

- I took a screenshot of the timings screen once I had the right mode working under windows.  I've attached that screenshot.

- Using this data, I went to an online modeline calculator and came up with the following modeline:

Modeline "1280x960_60i" 28.08 1280 1376 1488 1800 960 964 976 1120 +hsync +vsync interlace

- I added the modeline to xorg.conf, and set it as the only available mode in the Screens section

No matter what I change, the result is always the same - Mythbuntu boots into 1024x768 mode and the colors are all screwed up (has a purplish hue to everything).

I tried a bunch of different options for the nvidia driver, to no avail.  I played around a little bit with meta modes, forced it to TVout, etc. and the result is always the same.  Heck, at this point I would even settle for 640x480 with the colors right, just so I can watch TV on this box, but I can only run low-res modes when using the Vesa driver - as soon as I enable the Nvidia driver, it always does 1024x768 with the bad colors.

Anyone have any ideas?  I'm not even sure what to try next at this point.

---

### Post by yonkiman on 2008-09-24
Unfortunately the proprietary nvidia driver does indeed ignore modelines.  I've tried to do what you're doing since February and have given up. 

Instead, I pick the appropriate TV mode when installing (the installer will ask if you want to use the proprietary drivers, select yes, select component, and select the resolution that you want (I think you'd want 1080i - I used 720p), and then it loads OK, but I have overscan, so I can't see the task bar (or the left, right or bottom 10% of the screen).

You can adjust mythTV show it appears and plays back inside whatever size window you want, but I haven't found a way to do it with Ubuntu itself.  :-(

I still love MythTV, and this problem will go away when I get a new TV with HDMI.  But it's still mean not to support modelines...

---

### Post by SiHa on 2008-09-24
> this problem will go away when I get a new TV with HDMI

HDMI will still have overscan. Although, to be fair, most TV's let you turn it off. 

Well, my Panasonic does anyway.

---

