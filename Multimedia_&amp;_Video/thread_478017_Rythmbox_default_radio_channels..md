---
title: "Rythmbox default radio channels."
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by tigerhawk686 on 2007-06-18
When I first started up rhythmbox it had 3 radio channels listed in it. When trying to play one it crashed (the end of a song played and the next one started then crashed) and now none are listed. I was wondering if anyone knew the addresses for the channels as I am trying to get radio working and am having some problems. Would be nice to try the others to see if they work.

---

### Post by Ramas on 2007-06-23
Check out the file rhythmdb.xml in the ~/.gnome2/rhythmbox, it contains local music and also radio informations.

Find the section starting with <entry type="iradio">, there are the adresses for the channels as well as other informations.

---

