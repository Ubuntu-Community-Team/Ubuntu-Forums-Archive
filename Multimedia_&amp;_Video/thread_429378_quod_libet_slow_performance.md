---
title: "quod libet slow performance?"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by gantengx on 2007-05-01
i have 5000+ songs in my library and the performance is quite bad.. when i want to display all the songs or do some search it always took some time to finish...

does anyone share the same problem? i'm using ubuntu feisty, quodlibet 0.24, p4/2.8ghz, 1gb ram...

---

### Post by hugmenot on 2007-05-01
That&#8217;s because the song database of QL is a simple Python pickled dict and no real database. It is reliable but a tad slow.

---

### Post by gantengx on 2007-05-02
so there's no way to improve it? :(

---

