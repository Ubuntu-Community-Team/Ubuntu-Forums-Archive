---
title: "Totem/mplayer flashing video"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by sripplinger on 2008-04-07
I am running Gutsy on a laptop with a Radeon Mobility HD2600.  I used envy to install video drivers.  I have tried playing DVD's on totem-xine and Mplayer.  They run, but the video flashes a lot.  I've seen a few posts about disabling x11 or something.  If you're going to suggest something along those lines you might need to spell it out for me.  I'm not sure how to do it.

---

### Post by Metaljaz on 2008-04-07
This site explains how to install the driver. Cut and paste the commands that are in italics so you don't leave something out. I have no need to try the drivers but thought the site maybe helpful....
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

Based on this thread, looks like help will be coming with the new release of Ubuntu.
[http://ubuntuforums.org/showthread.php?t=692102](http://ubuntuforums.org/showthread.php?t=692102)

Another interesting read:
[http://georgia.ubuntuforums.org/showthread.php?t=570391](http://georgia.ubuntuforums.org/showthread.php?t=570391)

---

### Post by sripplinger on 2008-04-08
I tried installing the driver specified in the link you gave me.  Things were worse, then.  At least as far as any 3D graphics are concerned.  So, I reverted back to the ATI driver installed by Envy.

Here are the specific problems I have run into:

Totem-xine and mplayer flicker when playing a DVD
Screensavers flicker
When I run gmsh the view screen is grey, except when I zoom/translate/rotate the object
Flash player works fine

If anybody has solved this problem for an ATI card, lemme know!

---

### Post by Metaljaz on 2008-04-08
This link maybe the solution. I don't have this issue due to a different card, but just trying to help out another Ubuntu user:

[https://help.ubuntu.com/community/CompositeManager/Xgl/simple](https://help.ubuntu.com/community/CompositeManager/Xgl/simple)

---

