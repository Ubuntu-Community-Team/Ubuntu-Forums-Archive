---
title: "Greenish tint on display from component output"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by personwholives on 2007-07-15
I have a magnavox hdtv (a bit older, not sure of the model number, as it belongs to my roommate.  Its a CRT, not an lcd or dlp)  which I hooked up to my mythtv box (built on ubuntu).  The only nagging issue is that the video displayed is somewhat greenish (well, to be more exact, it seems to be lacking red).  I checked the cable (I even tried one of my other cables).  I am using component video.  And I checked, this isn't something with the TV, or the stereo receiver, as I tried skipping the stereo, changing the input I was using, and checking my other devices.  Everything checks out.  Also, when I tried this with slackware running on the same box, it did not have this issue, and none of the hardware has changed since then (though the cables may have been rearranged) (long story as to why that was changed, but basically, that box finally finished driving me up a wall, and ubuntu worked really well on my laptop).

Video Card: geforce 6200
Latest ubuntu (downloaded and installed last week).

It looks fine on when run through other outputs (svideo, dvi to my monitor, etc).

I don't know what else to check.  Anyone got any thoughts?  Seen something similar?  Thanks in advance.

---

### Post by tgalati4 on 2007-07-15
Are you sending an RGB signal or a YPrPb signal?  One is simply red, green, blue, the other is Green Luminence, Green-Red, Green-Blue.

Changing the mode will often result in a weird-colored picture.

---

### Post by personwholives on 2007-07-16
I don't know how to change that.  My xorg.conf file is set to send tv in HD480p format.  I can post the whole thing tomorrow, if you think it will help.

---

