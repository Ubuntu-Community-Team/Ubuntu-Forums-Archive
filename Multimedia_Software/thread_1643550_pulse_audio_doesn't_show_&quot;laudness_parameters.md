---
title: "pulse audio doesn't show &quot;laudness parameters&quot;, project M can't visualise correctly"
date: 2010-12-12
forum: Multimedia Software
---

### Post by f1ckratte on 2010-12-12
Hi guys,


I've recently got a problem. I've installed projectM, the pulse audio version. It worked fine until a couple of days. I noticed, that the visualization isn't synchron with the music. Then I opened pulse audio to check the volume controls. The blue bars showing the intensity of the loudness don't move at all, it's all gray. ProjectM can't analyze the music and therefor cannot visualize correctly. 

I need a solution to this, guys, as visualization is very important for me ;)

btw: got the newest version of Ubuntu x64 on an HP dv5-1040.


would be nice if you could help me

---

### Post by arpad9 on 2010-12-12
Same thing happened to me.  Ubuntu 10.10 64-bit.

Haven't been able to figure it out.  It seems like everything should be working.

---

### Post by f1ckratte on 2010-12-12
there has to be a solution to this problem guys, its extremely important ;)

---

### Post by f1ckratte on 2010-12-13
*push*

---

### Post by arpad9 on 2010-12-18
bumpity bump bump <-- ProjectM didn't visualize that

---

### Post by arpad9 on 2010-12-27
Normally, I would troubleshoot my own problems but with PA, I'm just lost.  No errors on the console, no log errors.  PA Manager shows ProjectM as a client and now even has a slider for input control level.

However, no beat sensitivity.

Such a bummer.  ProjectM is *exactly* what I've been waiting for since xmms and later G-Force (on Windows).

I keep waiting for an update to just magically fix it but alas...

---

### Post by arpad9 on 2011-01-23
FINALLY!!

So... as per this thread,
[http://gnome-look.org/content/show.php?content=99383&forumpage=13&PHPSESSID=6](http://gnome-look.org/content/show.php?content=99383&forumpage=13&PHPSESSID=6)

listing the sources via:
```
pacmd list-sources
```
and then unmuting the appropriate source via:

```
pacmd set-source-mute 1 0
```
did the trick.  Where 1 is the number of the source (beginning with 0) and 0 is the value (muted=0).

I don't know where this value shows up in any gui control interface and I'd argue that it doesn't but this command did the trick for me.

---

