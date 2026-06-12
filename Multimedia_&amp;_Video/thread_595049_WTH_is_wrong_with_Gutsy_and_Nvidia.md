---
title: "WTH is wrong with Gutsy and Nvidia??"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by pld on 2007-10-28
Look, I am about at my wits ends here, and it's really, really, really, really frustrating...

I upgraded from an old Dapper box where everything worked exactly how I liked it running Xubuntu.

So I decide to give Gutsy a shot w/ a default Ubuntu install, and I was hopeful to be wowed.

After installation everything looked good.  I allowed restricted Nvidia drivers, and could use compiz-fusion nicely.  I was just humming along rebuilding all my software and getting things the way I like them.

Nvidia GeForce6800GT, btw.

Then I had to reboot this morning to move some things around the office.

Next thing I know, I am presented with an xfailsafedialog box telling me that I am now running in low graphics mode!

I continue and find myself at my screen at a magical 800x600 resolution :(  WTH?

Ok, so Gutsy has these tools that will allow me to graphically change my screen resolution and drivers.  So I head there to change things up.  The VESA driver is chosen, and I cannot get my widescreen resolutions to show up at all.  Again...  WTH?

Things I have tried:

1. Remove the restricted drivers, set the driver to nv, set my resolution to 1680x1050.  Log out, back in, and I am at a 1280x1024 desktop.  Try to change the resolution again, and now my native resolution isn't in the damn list.
  In fact, I have tried every posisble combination of ubuntu specific methods to change the resolution and screen size, but with no luck.

2. Being a slightly older schooler, this is not my first linux box, so i can understand occasional problem getting X to play right.  So I figure I can just modify my xorg.conf file and try to set things right.  No matter what I do to my xorg.conf file, things still do not look right at all.

The MOST annoying thing I think is the failsafe X.  In the past, if you screwed up your xorg.conf file in any way, then you got NOTHING.  Just didn't start.  Which is fine, because the Xorg.0.log would tell you specifically why.

NOW, if I cannot boot my xorg.conf file, xfailsafe will take over.  Which I guess might be good, but the Xorg.0.log doesn't reflect WHY I FAILED IN THE FIRST PLACE!

SO, does anyone have any idea why this might be happening, and possible fixes?  I am tearing my hair out in frustration here...


Some details:
GeForce 6800GT 256MB card
Samsung Syncmaster 225BW monitor (1680x1050 native res)
Gutsy Gibbon vanilla Ubuntu install.

---

### Post by Caffeine_Junky on 2007-10-29
Hey there,  ...I did a google search for your monitor and found a dicusion[ [COLOR="Blue"]_here_[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=90041") that might be worth a look...

---

