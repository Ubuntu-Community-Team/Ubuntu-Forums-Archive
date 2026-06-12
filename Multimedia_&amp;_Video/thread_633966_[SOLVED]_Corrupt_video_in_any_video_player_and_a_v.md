---
title: "[SOLVED] Corrupt video in any video player and a vertical green line"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by MidBSD on 2007-12-07
**
Ok, latest update - I've got it working although it's not very satisfactory. It has something to do with the video being rendered on x11.

If you're using Totem-Xine (as I am) you can edit your

/home/username/.gnome2/Totem/xine_config

Change
# video driver to use
# string, default: auto
#video.driver:auto

To
# video driver to use
# string, default: auto
video.driver:xshm

Unfortunately it makes the video quality lower. What I do is I change it back after watching the video files that have the horizontal green stripe along the top.

**

*
I marked this thread solved because it solved the specific problem I asked but in terms of a complete solution, this is only a partial fix.

How did you solve it?
I followed the instructions on this page for Gutsy.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

What isn't solved?
Other videos that previously played with the corruption now play with discolouration and a horizontal green stripe across the top.


Here's the video that started it all off - worth the watch if you're into technology
[http://media.newscientist.com/data/images/ns/av/dn13004V1.mov](http://media.newscientist.com/data/images/ns/av/dn13004V1.mov)
*

I'm trying to watch a video from the New Scientist website (it's of someone trying to push over a robot that automatically balances itself) but the video is corrupt and has a vertical green line.

Screenshot for clarity:
[img]http://img2.freeimagehosting.net/uploads/d58c863607.png[/img]

This file happens to be a mov but I know it also happens with other files like AVIs but not all AVI files.

Does anyone know how to fix this?

---

### Post by MidBSD on 2007-12-07
Just tried uninstalling all codecs and re-installing them but that hasn't fixed the problem.

Can anyone else with a Mobile X1300 confirm that they don't have this problem so I can eliminate the graphics card and drivers as the problem?

---

### Post by coskierken on 2007-12-07
What player are you trying this on?  Do you have problems with DVD or MPEG4 playback?  Let us know!:confused:

---

### Post by MidBSD on 2007-12-07
I haven't actually ever played a DVD on this laptop. I just tried it now and it told me to go install some plugins. I'll get to doing that in a minute.

I have some old rips of DVDs from my Windows days that play fine if that's useful info. I have a couple of mp4 files that play fine though.

I've been testing in Totem and VLC but I've uninstalled VLC in the last hour or so during testing.

I'm guessing it's just my configuration as nobody else seems to have this problem.

---

### Post by fozzieb on 2007-12-07
i'm using mint linux based on ubuntu and i get the exact same problem. It is not all videos some are ok but most are corrupted.

this is with both avi and mp4 files

I just moved over to linux and these all played ok in windows, i have moved from an ntfs patition to an ext3 one
any ideas?

Cheers.

---

### Post by MidBSD on 2007-12-08
I've just installed DVD playing libraries a la:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Now the green stripe has gone - yay! The other corrupt videos are no longer as corrupt now but instead they have a green band running across the top of them.

fozzieb - I'm guessing you don't have the ability to play DVDs installed?

Try this page (I used the Gutsy info):

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I don't think it'll fix the problem entirely but like for me, it'll probably make it a lot better. Perhaps this is something that only affects people in Scotland? (I'm in Dundee but yes I'm joking :))

All my videos and DVDs play fine in Windows too.

---

### Post by fozzieb on 2007-12-08
How do mate, always good to see a fellow scot online.

My system is playing dvd's ok, Linux mint has all multimedia installed.

I have a feeling that the videos got corrupted when moving partitions and the resizing them.

Glad to see you got yours working though.

Have a good one mate.

---

### Post by MidBSD on 2007-12-09
It's a small world fozzieb :)

I think I've managed to solve the problem now. Check the first post for update.

---

