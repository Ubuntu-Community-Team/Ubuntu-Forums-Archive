---
title: "HDMI TV output does not fit the screen"
date: 2011-07-02
forum: Multimedia Software
---

### Post by ausairman on 2011-07-02
Hi everyone,
I have an Okano 42" LCD TV, which I connect to my laptop via HDMI cable. Unfortunately, it doesn't fit the screen at the TV's resolution of 1920x1080, and there are about 40 pixels that run over the edge of each side on the TV, making the Ubuntu toolbars invisible.

The standard NVIDIA control panel doesn't have any options for correcting this (in windows it had settings for adjusting the stretch/position of the screen), so I was wondering whether there are any common tools that ubuntu users can use to adjust the relative position and stretch of a screen?

BTW I think the cause of this is that my dodgy TV isn't correctly reporting its resolution to the laptop, and unlike most branded TVs, I don't have any system settings that can be adjusted to correct this (I know the panasonic counterpart can fix this in the system menu)..

---

### Post by ausairman on 2011-07-22
I still haven't resolved this, would be great to get some feedback. I'll keep looking and post back if I find anything in the meantime..

---

### Post by papibe on 2011-07-22
I had a couple of similar problems in the past. I solved both on the TV side. In my Sony Bravia I went to the menu Screen -> Display Area and selected 'Full Pixel'. In my brother's Samsung, there's an option P.size (in a menu that I don't remember). I set that to 'Just Scan'

Hope it helps.

---

### Post by ausairman on 2011-10-01
Well I tried fixing this and asking around, but it seems there's no fix that actually works, at least for my TV, so it's back to win 7 for me, where I can just stretch the screen to make it fit...

---

### Post by papibe on 2011-10-01
Sorry to hear that. I finally found a way to fix it using the 'Nvidia X Server Settings'. [Here]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/")'s a simple tutorial.

At least if you decide to go back, there's an option.

Regards.

---

### Post by BicyclerBoy on 2011-10-23
The nVidia 270 driver has HDMI overscan compensation that works.
I had cause to try it when demo'ing mythtv on an old Panasonic LCD..

Or try this xrandr cmd..
xrandr --fb 1840x1000 --output LVDS1 --pos 40x40

replace LVDS1 with the screen name from
xrandr --prop or just xrandr..

Note: This cmd worked fine couple of months ago on intel graphics ...but today the --pos offset does not work..

---

### Post by BicyclerBoy on 2011-10-23
The nVidia overscan compensation tool works perfectly but..

You could try this modeline:

Modeline "1920x1080RH"  138.50  1860 1928 1960 2080  1000 1043 1048 1111 +hsync -vsync
(the H suffix for hack)

The pixel clock & sync freq the same as std mode but moved the visible screen size.
It's been a while since I played with modelines & I would normally just change things incrementally. So this may not work.

xrandr should work with nVidia driver..
else stick it in the xorg.conf file in a custom mode section or in the device section (display sub section)

This in the xorg.conf is useful for logging info:
Option         "ModeDebug" "TRUE"

You may have to use 
Option "UseEDID"  "false"
to make the driver accept the mode but only if it rejects it..
See the /var/log/Xorg.0.log..

---

### Post by wannabegeek on 2011-11-11
Hi All,
I'm having the same problem with my HDMI and a Sony Bravia TV...

The TV is detected at 1320x720  but that's too big....When I used to use VGA, I wold run
@ 1024x768 and set the TV to WIDE mode.

I have an Asus P8H67-m PRO with integrated Intel graphics, and every xrandr  newmode I try
gives me a black screen. I have to go into tty1 and restart gdm.

I've never used HDMI before so I don't know what to do....:(

thanks in advance
wbg

UPDATE:  Googling "Sony Bravia modeline"   have helpful information for MythTV  [http://www.mythtv.org/wiki/Modeline_Database#Sony](http://www.mythtv.org/wiki/Modeline_Database#Sony)

UPDATE: I found several posts around the web started by people with Sony Bravias and scr res issues like mine. I finally solve my problem. The  answer lies in understanding the modeline numbers. See this page, [http://www.mythtv.org/wiki/Working_with_Modelines](http://www.mythtv.org/wiki/Working_with_Modelines), but don't mess with the sync numbers.

Pull your working modeline from /var/log/Xorg.0.log and modify it

---

### Post by Cerin on 2013-01-20
> **ausairman said:**
> Well I tried fixing this and asking around, but it seems there's no fix that actually works, at least for my TV, so it's back to win 7 for me, where I can just stretch the screen to make it fit...

I had a similar problem with my 40" Samsung LED. I fixed it by pressing the "P.Size" button on the remote, which cycled between various display formats until it got to "Screen Fit" mode, which shows everything received over the HDMI cable. I'd be surprised if your tv doesn't have a similar feature.

---

### Post by edwin6 on 2013-12-10
Had same issue with my Sony Bravia TV and it was an obscure setting what caused the picture to be too big. Under HOME button on the remote, navigate to Settings, Features, Video/Photo setting. In my case it was on Video and changing it to Photo, it scaled back to fit the entire [COLOR=#000000]1920x1080.[/COLOR]

---

### Post by oldos2er on 2013-12-10
Old thread closed.

---

