---
title: "MusicBrainz Picard problem"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by fergrorke on 2008-01-11
I installed MusicBrainz Picard from the Gutsy repositories without a hitch but can't actully use it to edit my tags. The problem is that the list of files from which one is supposed to drag and drop for tagging is grayed out and dragging them is impossible

Any idea what's wrong?

---

### Post by asktoby on 2008-02-14
I have the same problem. Searching indicates this should happen when the file is a format Picard cannot manage. For me it happens with mp3s so my guess is that Picard is missing some library or other to give it the ability to deal with mp3s.

---

### Post by asktoby on 2008-02-14
Installing Libtunepimp5-mp3 from the repos fixed the problem.

---

### Post by Kendall on 2008-03-05
> Installing Libtunepimp5-mp3 from the repos fixed the problem.

Thanks! That worked for me too.

---

