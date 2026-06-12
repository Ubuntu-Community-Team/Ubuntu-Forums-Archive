---
title: "Cannot watch video files"
date: 2010-11-06
forum: Multimedia Software
---

### Post by ensisr on 2010-11-06
Hello,

I'm using Dell inspiron 1210 and installed netbook remix 10.10 recently.

But I have trouble with watching video files with any players,
including built-in player, SMPlayer, VLC media player.

Video is not appear with those players and can see only black screens.
Sound works well.

I think there are some troubles with codecs,
But though I installed some codecs and restricted-extra, there are no improvements.

What should I do to see video with this system?
Those video files can be watched with my desktop;Ubuntu 10.04 and VLC player
so I think files has no problem.


Dell inspiron 1210 specification;
Intel Atom Z530, GMA500, 1GB Ram.
GMA500 driver has installed.

---

### Post by cotcot on 2010-11-06
Try to install [[COLOR="Red"]these[/COLOR]]("https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html") codecs and check if this solves your problem. 
You could also try VLC. It is in the repos.
If this does not work, supply some details of your files. Which type ?

---

### Post by ensisr on 2010-11-06
Those codecs has already installed.
I don't know where the problem is, so I have installed many kind of codecs
like w32codecs, libavcodec, gstreamer and etc but doesn't help...

My file types are DVIX, XVID MPEG4 and H264 and so on.

---

### Post by andrew.46 on 2010-11-06
Hi ensisr,

Sounds like a video out problem. Perhaps try a different video out device from your media player preferences? For SMPlayer this can be found:

Options --> Preferences --> General --> Video --> Output Driver

Andrew

---

