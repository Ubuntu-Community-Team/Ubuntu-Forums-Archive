---
title: "Video Shakes Vertically, all formats, all players"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Darksword on 2008-06-06
Cross posting from another forum:


    Mplayer won't work.

    For some reason almost all my video players have this bizarre problem where the video image shakes up and down as it plays. It happens with all videos of all formats, but does it worst with .mp4s and .wmvs. It's not a stutter or chop, the play rate and smoothness are normal. It's just like the image itself goes crazy in the player window, flickering up and down like it's on crack. I've never been able to fix it. Cranking up the postprocessing on Mplayer helps, but it's still unwatchable.

    Totem is the only player I've used that doesn't do it for .mp4s. Actually it still kind of does it, but it's more like one tiny stutter every 45 seconds or so. I can live with that, but Totem won't play all my file formats properly.  

    My video card is an ATI Radeon Xpress 200, running on the flgrx driver with the ATI Restricted Driver enabled (it did it before I enabled this.  There was no change), if anyone has heard of a fix for this you'll personally win the internet.

---

### Post by Darksword on 2008-06-09
So no one has even the slightest idea?  This renders my entire video collection pretty much unusable, and it's happened with every version of Ubuntu since 6.06.

I've also noticed one other thing:  If I'm taking up a lot of video RAM, the shaking gets even worse.

---

### Post by anindya_m on 2008-06-09
Try using mplayer with the -vo x11 option. Does that help?

---

### Post by rahulkavi on 2008-09-23
wow.......thanks.........

this works....:KS
ive tried different variants of the above command.....

found 
-xo x11
-xo gl
-xo gl2

very useful..... rest of them didnt work......

but the resolution is quite low.....

the following will work(with a zoom) with good resolution

mplayer [filepath] -xo x11 -zoom

---

