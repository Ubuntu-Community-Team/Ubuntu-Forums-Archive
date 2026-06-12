---
title: "artifact accross middle of video"
date: 2009-02-08
forum: Multimedia Software
---

### Post by eppo on 2009-02-08
this is kind of hard to explain in technical terms, but basically what is happening, when i play video, and say there is a lot of camera movement (camera moves from left and pans right) or a lot of action on the screen, there is a visible line that appears, like the top of the picture is not in sync with the bottom. this is happening with both mythtv recordings, and divx/xvid dvd rips that i backup from dvd. these files play fine on my other system. the system having the problem is a [http://system76.com/product_info.php?cPath=27&products_id=83](http://system76.com/product_info.php?cPath=27&products_id=83) which has 2 gigs of ram and upgraded cpu to the Core 2 Duo T5750 2.0 GHz. but it seems to be all video that is doing this, not just the high def. stuff.
anyone else ever have this problem? or know how i could fix it?
thanks

---

### Post by redroad55 on 2009-02-08
there are several threads this last week on "tearing" ..put that in "search".. you should find a solution there .. best to you

---

### Post by eppo on 2009-02-08
after doing some searching i found the answer to my problem, i'm running 8.10 completely updated. all you have to do is add these lines to the xorg.conf file to eliminate the tearing.
Option "TexturedVideo" "false"
Option "VideoOverlay" "on"

hope that this helps anyone else that is having this problem

---

