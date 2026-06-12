---
title: "NVIDIA Screen Stretching Past Monitor Edge"
date: 2010-12-30
forum: Multimedia Software
---

### Post by abbot on 2010-12-30
Hi,

I recently upgraded from onboard graphics in my Dell Vostro 200 to an MSI N210 nVidia card so that I could use my Samsung 40" LCD as a 2nd monitor.  I've got my main desktop monitor hooked up to VGA and the TV hooked into HDMI.  I was running the TV through VGA with the onboard graphics with no problem.

When I hooked up the TV to the HDMI on the new video card however, it's recognized as Samsung and pushes the correct 1920x1080 resolution to it, but there is about 22 pixels on all sides of the screen that are hidden past the viewable area.  It seems like things are being stretched because text and windows don't quite look as crisp and clean as they did through VGA.  Here is a photo.

[img]http://farm6.static.flickr.com/5125/5305953419_cf6667f206_z.jpg[/img]

As you can see, there is a 24 pixel panel at the top that only has 2 pixels showing, and all of the icons on the menu are being cut off.

I looked at the settings on my TV, but the options for screen stretching/skewing/etc.. are not available in HDMI.  Is there any way to fix this?

Here is my xorg.conf.  [http://pastebin.com/1yhuqedC](http://pastebin.com/1yhuqedC)  

As you can see I've been messing with nvidia driver settings.  I currently have it set as single x sessions per screen, but the problem has been the same with twinview as well.

Thanks.

---

