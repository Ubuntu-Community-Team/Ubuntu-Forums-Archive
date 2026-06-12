---
title: "Amarok - showing tracks twice"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by goughs on 2008-03-12
I've isntalled Amarok v.1.4.8 from the repos using the package manager, and I love it.  However, I have noticed a strange problem, in the collection it is showing every single track twice in the list, and also in the 'Context' view where it shows Albums by <Artist>, it is showing the track count as double what it should be, and the track names twice.

So for instance, I'm getting (in collection)

Blink-182 ->
      Dude Ranch ->
            Pathetic
            Pathetic
            Voyeur
            Voyeur
            Dammit
            Dammit

I have tried completely removing Amarok from Synaptic (right-click mark for complete removal) and re-installing but no dice.  I have also attempted to rebuild the Library, however the same problem keeps recurring.

P.S. I am running 7.10 AMD64.  The files are stored on an NTFS partition (if that's relevant).

---

### Post by goughs on 2008-03-12
Just in case its relevant, I have had (and been using Exaile) to manage and play music, which I also marked for complete removal in Synaptic.

---

### Post by goughs on 2008-03-12
I've solved this by completely removing Amarok, and then deleting the Amarok folder from home dir (/home/user/.kde/share/apps/amarok if anyone needs it for reference). Now I am only seeing one of each track.

---

