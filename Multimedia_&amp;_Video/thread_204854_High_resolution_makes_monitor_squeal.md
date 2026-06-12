---
title: "High resolution makes monitor squeal"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by jalefkowit on 2006-06-27
Hey everybody...

ran into a weird issue recently with my Kubuntu Dapper installation.  I noticed my monitor (a Viewsonic G71f+ CRT) making a weird, high pitched whine at random times.  

I think it has to do with the display resolution: I had it set to the highest available setting (1280x1024@60Hz).  I turned it down a bit, and now the whine is gone.

However, [the Viewsonic docs]("http://www.viewsonic.com/support/desktopdisplays/crtmonitors/graphicseries/g71fplusb/") indicate that the monitor can support this resolution -- in fact that it should be able to do so at up to 68Hz refresh (a refresh rate which Kubuntu doesn't provide for me).

I assume that this has something to do with my xorg.conf settings being out of whack for that resolution.  My first thought was to add the settings for 1280x1024@68Hz manually, since I know that is supposed to be supported, but trying to find instructions on how to manually update xorg.conf is an exercise in frustration.  I think I need to add a "ModeLine" under that monitor section, but I have no idea what values that "ModeLine" should contain.

Anyone else run into this type of issue with CRTs driven at high resolutions, and if so, how did you fix it?  (Other than just going to a lower resolution; it would kind of suck if that were truly the only option...)
[B]
EDIT:[/B] Just realized I should say more about my setup: video card is an ATI Radeon 9600, using the fglrx driver.

---

