---
title: "HVR-950 liveTV file fills up disk space breaks mythfrontend"
date: 2009-08-12
forum: Mythbuntu
---

### Post by haggiscanvas on 2009-08-12
Hello all,  

I have been fortunate enough to get my HVR-950 working almost perfectly in a full install of Ubuntu 9.10 with mythtv installed to it. I had problems with the mythbuntu install which is why I went with the full Ubuntu. After installing Ubuntu and Mythtv, I used the directions on the mythtv wiki for the tuner.

I can watch live tv for a while, recording scheduled shows is no problem at all.  I get great looking video with no sound issues.

[COLOR="Red"]However:[/COLOR]

It appears as if mythtv is recording one continuous multihour file. It does not break the file up by shows as it should. This file will continue to record until there is no longer any room on the harddrive at which point mythfrontend will lock up.  If I understand correctly, mythtv will delete livetv files as needed to free up disk space for new recordings and general computer uses.  I suspect the lockup is caused by the continuous file problem I am having.  I believe so because when this happens, I find only one file in the liveTV folder (this file is usually on the order of 150 - 200 Gb) and the mythfrontend.log is also really big.  


My problem is I cannot leave the computer on livetv overnight like I was able to with my old PVR-150.  I really miss that, I found a lot of really interesting shows I never would have otherwise just from letting it record live tv.  

Any suggestions would be greatly appreciated.

Thanks,

Jeff

FYI  My computer:

nvidia 7800 graphics
core2duo e4400
2 gig memory
2- 250 gig harddrives
Ubuntu Jaunty (fresh install as of June 2009)
Mythtv (fresh as of June 2009)

---

### Post by haggiscanvas on 2009-08-13
To add some things to the mix...

When this occurs, I have to delete the offending files just to regain system stability.  I also have to restart mysql before my previously recorded programs will show up in mythtv.  I have livetv files on one harddrive and scheduled recordings on the other...

---

