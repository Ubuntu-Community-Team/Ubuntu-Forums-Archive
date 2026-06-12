---
title: "9800XT Dual Headed output"
date: 2008-10-05
forum: Mythbuntu
---

### Post by slick666 on 2008-10-05
Dear Mythbuntu Users,

I recently upgraded the video card in my Myth box to a 9800XT that was lying around so I could get DVI (for DVI to HDMI). I ran into quite a snag though and spent hours and hours trying to figure out what exactly went wrong.

First I replace the video card and booted straight into myth. I updated the system.
[CENTER]**sudo apt-get update**
**sudo apt-get dist-upgrade**[/CENTER]
I then upgraded the the propriety driver and rebooted. I also changed my setup so that the projector was on the DVI head and a temporary CRT was put on the VGA output. I configured the X with the graphical utility and things seemed great. but whenever I tried to play anything (video, DVD) the front end would crash. :confused:

A couple hours of playing same result :mad:
so.....
reinstall Mythbuntu from scratch.
reinstall, update, install propriety drivers, etc.
Now things worked pretty good. I still had the temporary monitor plugged in and by default it was mirroring what was on the projector. The problem is that when playing a DVD or video the movie would play only the temporary CRT, not the projector. After about three hours of playing I found that turning the MergedFB variable on caused the problem I had in the beginning.

So turning MergedFB Off in the beginning would have saved me this whole fiasco! :mad:

So while I figured out the original problem I was still faced with the problem of the movie. More playing around and I found the solution

**Unplug the CRT Monitor!!!**

Thats it now things are working awesome. I have a little more reconfiguring to do but I'm where I wanted to be. It took about 8 hours longer than I had figured. I wasted to throw this up on the forums to share my experience so others wouldn't waste a saturday messing with there Mythboxes.

I hope this helps

---

