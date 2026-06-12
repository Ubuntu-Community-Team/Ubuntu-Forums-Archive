---
title: "Setting audio volume very quiet"
date: 2009-03-05
forum: Multimedia Software
---

### Post by jlebar on 2009-03-05
Hi, all.

I just installed Ubuntu a few days ago after being a longtime Cygwin user, and configuring the install to my liking is coming along pretty well.

I'm currently stuck on one point, though: My laptop has a highly-amplified headphone port, and I can't seem to set the volume quiet enough without turning it off completely.  (On Windows, I had to set both the master and the wave volumes very close to 0.)

I've tried running
```
amixer set Master ###
```
but it seems that the inputs to this program are discretized -- In my case, the smallest value I can set the volume to without having it turn off is 1058.

Is there a way to get my volume quieter than this?  I'd appreciate any pointers...

Thanks,
-Justin

---

### Post by Lars Stokholm on 2009-03-05
Try setting PCM along with Master. You can also use percent when setting the levels (see man amixer). It might be easier for you to use gnome-volume-control.

---

### Post by jlebar on 2009-03-05
It looks like amixer doesn't recognize "PCM":

```

jlebar@jlebar-laptop:~/bin$ amixer set PCM 10%
amixer: Unable to find simple control 'PCM',0

```

I'll look into gnome-volume-control...

---

### Post by jlebar on 2009-03-05
Hm.  So gnome-volume-control shows PCM sliders, and those work great.  But I'd like to do this via the command-line if I can, so I can write a script to set my volume to the appropriate levels.

---

### Post by Lars Stokholm on 2009-03-05
Try adding the switch -c0 to amixer.

---

### Post by jlebar on 2009-03-05
Oh, beautiful.  That works perfectly, Lars.

Thanks so much!

---

