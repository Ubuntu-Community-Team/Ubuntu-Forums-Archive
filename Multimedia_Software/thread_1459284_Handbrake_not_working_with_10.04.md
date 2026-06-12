---
title: "Handbrake not working with 10.04?"
date: 2010-04-21
forum: Multimedia Software
---

### Post by servicetech on 2010-04-21
I'm trying to convert some files but the start button is grayed out. Any ideas?

---

### Post by JohnAStebbins on 2010-04-21
The latest libgtk breaks the last official handbrake release.  You'll have to use the snapshots.

[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901)

---

### Post by bryanl on 2010-04-21
> The latest libgtk breaks the last official handbrake release.
This seems to be happening every release. It has got to be really really frustrating for developers ... or is it an indication of poor design that uses the library in some 'special' way? whatever. not good.

---

### Post by JohnAStebbins on 2010-04-21
In this particular case, there was a fundamental change in where GtkBuilder stores the widget id's that come from the xml file.  Yes, it's disruptive, but the change was a good thoughtful design decision.  It took all of a few minutes to compensate for the change.  The only real issue is that the "official" handbrake release will be broken on 10.04 for a while since we don't release all that often.  But the snapshots are often better than the releases anyway.

---

### Post by servicetech on 2010-04-21
Thanks, new version works great :)

Also, how can I do a bunch of Files at once?

---

### Post by servicetech on 2010-04-21
I thought I had it. My encodes sound like the chipmunks. Video is normal speed, audio is fast and ands about 1/2 way through video.

---

### Post by Maybelline on 2010-04-29
JohnAStebbins, I've seen your PPA for the Handbrake nightly builds.  But, do you happen to know where I can still find the last snapshot that was available from the Handbrake website?

I don't want to rebuild so often, and would rather just stick with snapshots.

Thanks.

---

### Post by JohnAStebbins on 2010-04-30
The nightlies have replaced our previous snapshots.  If you don't want it to update constantly, just disable the PPA in your software sources after installing.  It's as easy as unchecking a checkbox.

---

