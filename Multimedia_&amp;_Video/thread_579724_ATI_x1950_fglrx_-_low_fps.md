---
title: "ATI x1950 fglrx - low fps?"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by inzeo on 2007-10-18
Hey Everyone:

I just installed a fresh copy of Ubuntu Gutsy Gibbon and made sure all the updates were applied.  I then enabled the Restricted driver (fglrx) for my ATI card that Ubuntu detected.  The computer was restarted and everything worked fine using the new driver.  Direct rendering was enabled and it appeared that I was set to go!  

But....running glxgears gave me very low FPS for this card - averaging around 900fps.   I know this can't be right because my Sony laptop that also is running Gutsy only has an onboard Intel video card and it gets around 900fps in glxgears.  Also, all videos that are played, no matter what format, play very choppy and with very low framerates.  

Does anyone have any idea why this would still be happening even though it appears my 3D acceleration should be working?  Thanks for all the help!

**I've also noticed after running "glxinfo" that I get:
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: ATI
client glx version string: 1.3

Does this help anyone?

--Scotty

---

