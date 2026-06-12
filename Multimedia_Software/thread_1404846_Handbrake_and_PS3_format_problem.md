---
title: "Handbrake and PS3 format problem"
date: 2010-02-11
forum: Multimedia Software
---

### Post by Neezer on 2010-02-11
Hi,

I have ripped quite a few movies onto my server and I play them on my PS3 with mediatomb. I haven't changed any of the settings in handbrake except I was playing around with the quality meter on the video tab. Some of my movies will play and others won't. The ones that do not play say something about an unsupported file type. They also will not play in Movie Player.

Why is this happening? is it just a bad rip and I need to re-rip the ones that aren't working?

---

### Post by JohnAStebbins on 2010-02-12
I suggest you take this question to [HandBrake's forums]("http://forum.handbrake.fr/viewforum.php?f=13&sid=1d2f6a3e00ded0d0bc86d3b97a8fe961").  And include an [Activity Log]("http://trac.handbrake.fr/wiki/ActivityLogLinux") of one of the encodes that can't be played.

---

### Post by Neezer on 2010-02-15
Thanks for the reply...Sorry I've been so long getting back to you.

I figured out my problem. There is some problem with file sizes over 4GB. It has something to do with 32 bit vs. 64bit.... anyways, I just used a little bit higher compression and everything is great now.

There is a check box that you can select if the file is going to be more than 4GB. I was told that the PS3 does not support this so I settled with a bit more compression. The quality is still very good as far as I can tell.

---

### Post by JohnAStebbins on 2010-02-15
hehe, yup, I recall your visit to #handbrake on irc.

---

