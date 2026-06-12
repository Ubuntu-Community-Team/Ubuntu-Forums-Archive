---
title: "Voodoo2 Card - Blank"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by bottomtop on 2007-01-29
Ok.  I've trawled through the posts to try and get my Voodoo2 card working.  Here's the story:
The Voodoo2 card is an "in line" card - meaning that it takes the video signal from the video card of the PC (on board S3 Trio V64+) via an external cable.   The monitor then plugs into a second port on the Voodoo2 card.

All works fine when the S3 card is selected for the X server, the signal just passes through the Voodoo2 as if that card wasn't there.

When I change the Xorg.conf through the config program, so that the Voodoo2 is used, when the Xerver boots, the screen goes completely blank (and the light on the monitor goes off, as it does when one turns off the PC).  I still get the login prompt sound and if I type my login blindly I get the startup sound.

Interestingly, the bus address for the Voodoo2 is different depending on whehter I use lpci or look at the log from the Xserver crash that happens when I use the LCPI calues.  When I use 0:20:0 (which is where the logfile says the voodoo2 is), that is when I get No error images, just the blank screen.

If anybody has got one of these cards working - in the sense that it is actually being utilised by the system - I would be very grateful to know how.

---

### Post by deadgobby on 2007-01-29
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[https://help.ubuntu.com/community/Voodoo3doesnotdo3d](https://help.ubuntu.com/community/Voodoo3doesnotdo3d)
Hopes the links help

gobby

---

### Post by bottomtop on 2007-01-30
Unfortunately this did not resolve my problem, but many thanks for your reply.

It seems that XORG can either activate one video card or the other - but not both.  Perhaps I should just give up.

---

