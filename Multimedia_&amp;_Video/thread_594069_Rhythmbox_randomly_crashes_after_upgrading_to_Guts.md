---
title: "Rhythmbox randomly crashes after upgrading to Gutsy"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by RobbieCrash on 2007-10-27
After upgrading to Gutsy, Rhythmbox randomly crashes for no apparent reason. Thought it might be specific songs, but when I try and play them after restarting Rhythmbox they play through perfectly. 

Started from the command line:

```

$ rhythmbox
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
Segmentation fault (core dumped)
$ rhythmbox
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found
Segmentation fault (core dumped)

```

I don't know where to find more information about it, as there's nothing in /var/log and I'm not sure if there's a way to make rhythmbox log itself?

---

### Post by RobbieCrash on 2007-11-05
Even after installing Jackd and getting it working and cutting out all jackd errors, I still get lots of segmentation faults. What can I do to fix this?

---

### Post by raintheory on 2007-11-09
I'm getting the segmentation faults as well..  they seem pretty random.  

No jackd errors though.

I also get random gstreamer errors:

**Error while saving song information**
*Internal GStreamer problem; file a bug*

Note that I get these gstreamer errors while loading library, *not* while editing anything.

Any help would be appreciated.

---

### Post by stinkinrich88 on 2007-11-11
I'm getting all your errors and:

> (rhythmbox:13128): RhythmDB-CRITICAL **: rhythmdb_entry_ref: assertion `entry != NULL' failed


---

### Post by sparks40 on 2007-12-06
I'm having the same problem.

---

### Post by Déjà Vu on 2008-01-21
Same here. (i.e. bump)

---

### Post by Cyfr on 2008-02-16
Same problem as original poster here. ANyone got a fix?

---

### Post by drowner on 2008-02-22
Yep - I've got the identical problem.

I've run rhythmbox -d in a terminal, to force it to reproduce.

It also happens with other music players for me.

Of course, now it hasn't happened (lol) so i cant get an error yet. I'll keep everyone updated.

I *think* installing that jackd package may be useful - but i want to see if i can reproduce it from a terminal firs.t

---

### Post by newagelink on 2008-05-22
[COLOR="Indigo"]I'm also getting the "error while saving ..." gstreamer error. ... It tells me to file a bug report? Huh?

Screenshot attached.[/COLOR]

---

