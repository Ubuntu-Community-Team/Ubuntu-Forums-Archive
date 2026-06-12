---
title: "TV-out:  Does anything just work?"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by tyleulen on 2007-09-14
I started collecting parts to build a MythTV box last year.  I read reviews, planned out hardware, and generally did all the research I could before I ever started.  I am new to linux, but having worked with several other flavors of *nix over the years, and actively using Solaris at work, I was comfortable with the underlying OS.  I finally put it all together in June, and after a couple weeks of figuring, reconfiguring and tweeking, I finally had a system that did what I wanted it to do.  Almost.  There were always little niggling things:  MythWeather didn't work, Xine wasn't quite set up properly.

  But the one thing that has been a CONSTANT thorn in my side has been TV-out.  I have an ATI card, I have an NVIDIA card and I a PVR-350 card all with S-video outs, and I can't seem to get any of them to work stably.  It will work for a month, and then some update will start the week long process of reconfiguring all over again.  I have tried using the restricted drivers, I have tried using Envy, and I have tried installing them manually.  I have tried installing Fiesty, Gutsy, and Mythbuntu.

What just works?  What can i do to stabilize this system so it will do what I have spent the last 9 months planning and working for?

---

### Post by peabody on 2007-09-14
Unfortunately, of all things, tv-out has been historically the most difficult thing about mythtv setups so don't feel too bad, you aren't alone there.  The problem stems from the fact that very few open source drivers actually can get the tv-out to function on the respective cards.  Proprietary drivers are often relied upon and proprietary drivers are often trouble.

The other problem can be related to hardware overlays.  Sometimes the drivers for cards will only do hardware acceleration of video on the primary display which is almost never what you want with mythtv boxes.  Getting hardware acceleration (Xv) to work on the TV often takes special directives in the xorg.conf file.

I've heard much better things about nvidia drivers than I have about ATI regarding TV-out.  Myself, I have a radeon 9000 and the tv-out on it has never worked well, even when the proprietary drivers supported that card (support has now been discontinued and now the open source drivers provided by feisty work better than the proprietary drivers ever have.  No tv-out though, however, I did find this: [http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1) which probably means future version of Ubuntu will support the tv-out on my card out of the box... yay!)

---

### Post by Tautoa on 2007-09-14
Ahh... is that maybe why my TV doesn't work properly as a second screen? 
I had assumed it was because the TV was old...

---

### Post by rsambuca on 2007-09-14
I fiddled with mythtv a while ago, but nothing too serious.  From my research, it seems like a lot of hardcore myth users turn off all updates once they have it up and running, as this does seem to be a common occurrence.

---

