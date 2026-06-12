---
title: "Banshee: Two Questions About Podcasts"
date: 2009-01-26
forum: Multimedia Software
---

### Post by wpwend42 on 2009-01-26
Been using Banshee for a long time, love it, but have a problem and a question.  I feel like I a missing an obvious solution to this...

1.  When I download podcasts via Banshee they become "read only" (with the graphical lock)...now, fixing that for individual files is simple (right click-permissions), but what do I do to make sure no file is downloaded as read only?

2.  That said, in Banshee is there a listing of what podcasts I am subscribed to or a method for exporting a list?

---

### Post by Linuxdork on 2009-01-26
I use Banshee and it does the same thing here.  There is no GUI setting that I can see to make it stop downloading as read-only.  This is more than likly configured in the podcast plugin.  There may be a config file some where that you can change this behavior but I'm not aware of one.  As far as exporting a list goes, I would like this feature but I do not currently see a way to do it.  I will keep up the search on both of these items, as they both intrest me as well.

---

### Post by wpwend42 on 2009-01-27
Well, let's hope there is a solution sometime soon to this!  Fixing read-only isn't a huge deal (is there a way to do it for an entire folder of files at once?  As in, switch off read-only for PODCASTS which has individual podcast folders inside of it)

As for not being able to export a list, that is very disappointing, but I can always keep a list of them for now.

---

### Post by Linuxdork on 2009-01-27
Yeah you can do something like:

```
chmod -R 777 $HOME/Music/Podcasts/
```

That would give full read, write, execute permissions on everything in the Podcast directory.  So you want to make sure you set it right.  Let me know if you have any other questions.

---

### Post by wpwend42 on 2009-01-28
Excellent I will give that a try.  Thanks.

---

### Post by wpwend42 on 2009-02-16
I was thinking today that, because Banshee organizes podcasts by folder, you don't really need a separate list, right?  I mean it is good to have one offsite, but if you are doing proper backup those folders are your list.

Still, an exportable list is preferable.

---

