---
title: "People are Blue after update"
date: 2010-05-09
forum: Multimedia Software
---

### Post by SSDF on 2010-05-09
I updated last night to the new 10.04 ubuntu version. This morning I popped in a flash drive opened the movie and all the people are blue.

The rest of the colour seems to be fine for the most part. However all the people have blue skin. I tried rebooting nothing is fixed I have a Nvidia Geforce 9500 GS video card.

I am relatively new to ubuntu, although I have had it a while I generally use my laptop which is vista OS.

Help would be awesome.

Note; I have tried in the default video player and the VLC player, no difference.

SSDF

---

### Post by nitstorm on 2010-05-09
Maybe [this]("http://joeb454.ubuntuforums.org/showthread.php?t=1222497") could help?

---

### Post by SSDF on 2010-05-09
I read that and another topic previously, The one you posted while a similar problem is not the same, he has a blue tint everywhere, Mine is limited just to watching movies and only so far in the appearance/colour of people. Also, online videos play perfectly normal.

Thanks for the prompt reply :)

---

### Post by no2498 on 2010-05-10
red rat put this up

This blue tint or hue problem might be caused by video. I found that when i played certain videos, can't remember which, I got the problem. It did NOT affect jpg or pictures or anything else, just video. The only solution was to run the Totem Video player and go to Edit> Preferences>Display and play with the sliders. Why this affects other video players is beyond me, but changing it in Totem helps.

---

### Post by Chronon on 2010-05-10
[http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

---

### Post by broken sword on 2010-05-13
I had the same issue, all my videos had a blue tint. Everything else showed the correct color, desktop, firefox, icons, empathy etc.

I upgraded to the current nvidia driver, worked for me.

Dell XPS M1530, nvidia graphics card ( obviously, lol )

---

### Post by petri.p on 2010-05-15
I had a similar problem after upgrading to 9.10 (I have an nvidia card), but nothing seemed to help.

I tried playing with hue controls of players, modifying the gstreamer-properties pipeline (with videobalance hue=-1 ! before the sink), leaving out xv, etc. All things which have previously helped.

This time, the solution was to use the nvidia X server settings dialog.
It worked in a really strange way (buggy driver, I guess).

First, I reset the xvideo hue to hw defaults, started a player -> bluish.
Moved the slider all the way to the right -> good.
Closed the nvidia utility -> still good.
Opened it again while video was still playing -> instant bluish hue, just from opening the dialog(!?)
This time moving the hue control around did nothing.
But resetting to hardware defaults fixed it -> all good again.

And now the value seems to stick.

This is really strange...

---

### Post by madchine on 2010-05-15
Is it too late to make an Avatar joke....?

---

