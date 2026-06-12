---
title: "Intel GMA 4500 Screen SIZING help, not resolution..."
date: 2009-06-23
forum: Multimedia Software
---

### Post by AoSteve on 2009-06-23
Alright, we built my little brothers "Netbox" as we've dubbed it today and the first thing to do was partition that hard disk and install XP Home (yeah yeah, flame all you want, it's REQUIRED by the school I'm going to, and he's going to be going to.)

First off, the XP install was hindered by loss of text and graphics outside of the resolution that it was being printed against..  alright....  Well, after we got into XP and installed the drivers, it was a simply fix by changing the sizing of the drivers output to put the entire desktop into the screen.  Vwala, fixed..   

Time for Jaunty!   

Wait, same thing, even with the Live! disk.. great.. what the heck now..   I'm the WORST luck when it comes to hardware and Linux.

[This MoBo](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121372), the Intel DG41TY is the heart of our system.  The audio just, kicks butt in windows, and the video doesn't do to shabby for what we need.

Now, with Ubuntu... using the DVI-D output to the HDMI on our Vizio 37" LCD, I can't get the screen to fit the resolution at all.  Even with the Live CD, the top panel isn't even visible and the sides of the screen are about 7-10% out of view.  The picture being shown is simply too big for the resolution/monitor space I guess you would say.  

We're only trying to reach 1280x720 as we don't need anything much more, and we don't want to stress that little processor by pushing 1080.

Ok, the second problem.  During installation, with the VGA enabled (which the TV automatically scales for), the install will crash and say there's an I/O error, unless I install in the safe graphics mode...     The disk installed 4 copies in Virtual box today in numerous tests, so it's not the disk.  Also, the disk integrity check passes as well.   Installing from the DVI though, it runs fine, no crashes, I just can't see the screen!   I can't see any mounted drives because the Icon is hidden behind the blackness that isn't being shown because it'd be two inches off my TV.  Heh

VGA and DVI(with adjusting hieght/width with the driver) in windows XP.  It's actually quite a good card for the price of the mobo.  But in linux, VGA results in being STUCK at 800x600, and DVI output won't let me see the outer parts of the desktop at all...

I've looked around for about two hours and haven't found a thing about adjusting this property.  I did come close, but no cigar.  I think it's setable in the xorg.conf file, I just don't know how to do it.  The width and height have to be reduced.   The card drivers, I could really care less about, but my little brother wouldn't mind some wobbling windows if you know what I mean.

Any help would be greatly appreciated, Thanks,
Steve.

---

### Post by AoSteve on 2009-06-23
Bump?   Noone knows how to resize the screen output?

---

