---
title: "MPEG/DVD playback -- Ugly lines!"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by tUrtleAE86 on 2006-07-20
I've been battling with this problem for a while now. I've done a lot of searching, and haven't been able to come up with anything.

Whenever I play an MPEG file, or a DVD, I get ugly lines whenever there is motion in the video. This happens with mplayer, Totem and VLC.

I do not have this problem in Windows. :confused:

Here is a screenshot from Ubuntu. (Horrible!)
[IMG]http://static.flickr.com/77/194372944_ddb2d8f973_o.png[/IMG]

Here is a screenshot from Windows. (This is what it should look like.)
[IMG]http://static.flickr.com/60/194372942_7989ccf437_o.jpg[/IMG]

I chose this clip, because there is a lot of motion, to best show the problem.

Does anyone have any ideas about what the problem is?

---

### Post by plexi50 on 2006-07-20
Depending an what program you use to watch the clips, it could be an interlacing problem. Try using ctl-i to bring up the interlacing menu. I am pretty sure that is the command for several programs. Try some of the settings to see if it goes away. I am at work (Windoze) so I cannot verify, but I know it is right for Totem.

---

### Post by tUrtleAE86 on 2006-07-21
Thanks, works perfectly now!

CTRL-I didn't get me to a menu, or anything. But, I enabled de-interlacing in VLC.

---

